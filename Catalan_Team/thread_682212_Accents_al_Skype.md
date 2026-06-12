---
title: "Accents al Skype"
date: 2008-01-29
forum: Catalan Team
---

### Post by Jordi B on 2008-01-29
Faig servir un ordinador que el puc arrencar amb la Ubuntu Feisty Fawn o la Ubuntu Gutsy Gibbon (tot i compartir la carpeta /home). Amb la Feisty puc escriure els accents amb normalitat al xat del Skype, però a la Gutsy he involucionat i he d'escriure sense accents. Algú sap a que és degut?. Agrairé molt qualsevol suggeriment. Gràcies per endavant. (pregunta també plantejada als fòrums de Softcatalà sense resposta )

---

### Post by borgg on 2008-01-31
Et connec, ets un tal jordi balcells? si l'ets sapigues que et segueixo d'aprop :P

A mi em va passar igual, això té a veure amb el suport parcial que te el gusty i la resta de distribucions d'ubuntu per defecte. Per solucionar-ho l'única cosa que has de fer és actualitzar per complet el suport de l'idioma català a l'ubuntu. Jo ho vaig solucionar així:

Sistema->Administració->Suport d'idioma

En aquest punt et dirà que el suport d'idioma no està actualitzat. Llavors deselecciones l'anglès i deixès només el català, i actualitzes. El problema hauria d'estar solucionat.

Salut!

---

### Post by Jordi B on 2008-01-31
He seguit el teu suggeriment però segueixo tenint el mateix problema. Quan vull escriure "ò" em surt "`o", a l'hora d'escriure "ó" em surt "o". Alternativament, he anat a Aplicacions -> Afegeix/Elimina i he carregat tots els programes relacionats amb Qt3 i Qt4. El més curiós és que amb la Feisty em va bé, però acostumo a treballar amb la Gutsy i no hi ha manera d'escriure directament al xat del Skype en català.

En quant al meu nom, em dic Jordi Binefa. Salut !!!!

---

### Post by borgg on 2008-01-31
Vaja doncs jo pensava que l'error es devia a això. Recordo que una altra cosa que vaig fer quan vaig tenir el mateix problema que tu per solucionar-ho és instal·lar el paquet kcontrol:

sudo apt-get install kcontrol

Pel que sé l'skype almenys en la seva versió dinàmica està basat en els paquets del kde, així en el kcontrol vaig ficar la codificació de caràcters a utf-8. Crec que així se'm va solucionar. A veure si t'ajuda.

Una altra opció que pots tenir si amb aixo no te'n surts és instal·lar el paquet skype-static que no usa les llibreries del kde. Potser així te'n surts.

Digue'm alguna cosa si ho aconsegueixes arreglar o sinó a veure si et puc ajudar més :P

Salut!! 

PD: t'avia confòs amb un amic meu :P

---

### Post by orestesmas on 2008-01-31
Per ventura tens seleccionat el català d'andorra (ca_AD.UTF-8)? Hi ha un error conegut en aquest *locale* que fa que no funcionin els accents. La "solució", si és que es pot dir així, és usar el locale ca_ES.UTF-8.

---

### Post by Jordi B on 2008-04-21
Moltes gràcies Orestes. He anat a Sistema/Administració/Suport d'idioma i he canviat Catalan (Andorra) per Catalan (Spain). (Com diuen els nostres colonitzadors : "No barregéssim pas la política !!!!"). Després s'ha de reiniciar el sistema i ja es pot fer servir aquest programari privatiu sense fer faltes ortogràfiques. (El S.O. és un GNU/Linux Ubuntu 7.10 o Gutsy Gibbon)

---

