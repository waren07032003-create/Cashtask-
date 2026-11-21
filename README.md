# CASHTASK

Site statique (index.html) + Supabase (inscription par email avec code OTP).

## Déployer sur Vercel
1. Mets ce dossier sur GitHub, puis Vercel > Add New > Project > importe le dépôt.
   (ou, dans ce dossier : `npx vercel --prod`)
2. Framework : Other. Aucune commande de build. Racine : ./

## Supabase
- Exécute `supabase/01_auth_profiles.sql` dans SQL Editor.
- Authentication > Email : « Confirm email » activé.
- Email Templates (Confirm signup + Reset Password) : mets `{{ .Token }}` dans le corps.
- Authentication > URL Configuration : ajoute l'URL Vercel dans « Site URL ».
- Admin : `update public.profiles set is_admin = true where email = 'ton-email';`

## État
Comptes = Supabase (réel). Missions, soldes, parrainage, retraits = encore stockés dans le navigateur.
`supabase/02_reference_schema_missions.sql` est un schéma de référence (ids en nombre) à adapter en uuid avant usage.
La clé publishable de Supabase est dans index.html (c'est normal, elle est publique). Ne mets jamais la clé service_role dans le site.
