---
title: "Signar documents amb openoffice"
date: 2007-11-25
forum: Catalan Team
---

### Post by CarlesOriol on 2007-11-25
L'openoffice té una opció per signar documents (fitxer > signatures digitals). Però no usa les signatures que usem pel correu i de les festes.

Algú sap cop es pot fer per usar aquestes signature, les del seahorse, gpg... en l'openoffice? Segons he llegit usa les que hi hagi insta&#320;lades al firefox però aquest a Edita > preferències > Avançat > Xifratge > Visualitza certificats sols em dona a opció a importar una cosa anomenada pkcs12.

---

### Post by papapep on 2007-11-25
Els pcks12 són els certificats SSL, com bé tu dius, que es fan servir per identificar-te (p. ex. davant l'Agència Recaptaire). 
Jo no he vist mai, el qual no vol dir que no es pugui, que es facin servir les claus GPG amb l'OO.

Ja saps, sempre ens quedarà l'intèrpret d'ordres :-D :

Signar un fitxer de text (per exemple pel correu). Genera una sortida al fitxer file.asc:

```
  gpg --clearsign file
```

Signar un fitxer binari. Genera una sortida al fitxer file.gpg:

```
gpg --sign file
```

---

### Post by CarlesOriol on 2007-11-25
ole, ole... En patatet reinventa la sopa d'all.

Així també ho faig jo... perdó a cop de clic amb el butó de la dreta del ratolí (el que està més a la dreta dels dos eh.... ;-)) menú > signa

Però no serveix, el signat dins del mateix openoffice fins i tot del hasefrog office permet d'establir editors de confiança per l'us de macros per exemple.

La pregunta doncs hauria de ser... és possible crear un certificat autosignat basat en la informació de l'anell de claus del gpg que puguem usar al firefox i a l'openoffice?

---

### Post by papapep on 2007-11-25
Ara t'ho busques tu per espavilat...:-P

No, no són compatibles.

---

