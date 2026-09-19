# Landing acheteur — ashkan-landing.vercel.app

Même contenu servi par 3 projets Vercel : `ashkan-landing`, `ashkan-landing-f8dw`,
`ashkan-landing-ojbl` (compte omarrerosarduy-1283s-projects). Pages : `/` (et `/acheteur`,
`/acheteur.html`), `/confidentialite`. `presentation.html` est la présentation GRP.

## Ce que fait une soumission (`api/lead.js`)
1. Contact retrouvé par téléphone et courriel, sinon créé : source `landing-acheteur`,
   étiquettes `acheteur`, `landing-acheteur`, plus `délai-*`, `préqualifié-*`, `région-*`
   selon les réponses. Champs Type de propriété, Budget min/max, Délai d'achat,
   Préapprobation, Secteurs. Contact existant : nom et coordonnées intacts, critères et
   étiquettes de famille mis à jour seulement pour les questions répondues.
2. Opportunité OZ - Acheteur à « Nouveau lead », valeur = budget maximum. Un dossier déjà en
   cours n'est pas touché ; un ancien dossier Gagné/Nurture/Perdu n'empêche pas d'en ouvrir un.
3. Note (réponses, campagne UTM encadrée, commentaire encadré comme texte non vérifié),
   tâche « Rappeler » pour Ashkan, échéance 2 h.
4. Texto d'accusé de réception au lead (numéros nord-américains seulement) et texto
   d'alerte à Ashkan (fiche GHL `cUafne3cRWoCokXJPuy0`, son cellulaire).

La vidéo (page 2) ne s'affiche et ne se télécharge que si le CRM a accepté la demande.

## Configuration Vercel (les 3 projets)
- `GHL_TOKEN` : jeton d'intégration privée GHL, sensible, production seulement
- `ALERTE_CONTACT_ID` : absent en temps normal. `desactive` coupe l'alerte à Ashkan le
  temps d'un essai en production (retirer ensuite et redéployer)
- Pare-feu : « Limite formulaire landing », 10 POST par 10 min par IP sur `/api/lead`

## Déployer
Un push sur `main` redéploie les 3 projets. Sans Git :
`VERCEL_ORG_ID=team_okqvQmjwuG6hsQaZvSFIPmdy VERCEL_PROJECT_ID=<id> npx vercel@latest deploy --prod`

## Tester
Numéro fictif 514-555-01xx et courriel `@example.com`, puis supprimer contact et opportunité.
Un numéro fictif reçoit un blocage texto automatique de GHL après le premier envoi : c'est normal.
