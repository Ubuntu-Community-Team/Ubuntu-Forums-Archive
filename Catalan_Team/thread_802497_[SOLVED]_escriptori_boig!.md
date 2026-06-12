---
title: "[SOLVED] escriptori boig!"
date: 2008-05-21
forum: Catalan Team
---

### Post by rogespierre on 2008-05-21
m'han desaparegut totes les icones de l'escriptori despres duna penjada de l'ordinador!

i quan hi faig click amb el boto dret no es desplega res! que passa?

(si vaig a llocs - escritori, tot està al seu lloc, pero que passa amb l'escriptori en si?)

que faig?
gràcies

---

### Post by papapep on 2008-05-21
Per començar et caldria posar un títol que descrigui mínimament bé el teu problema. Com bé comprendràs, "escriptori boig!" no és el més adequat.

Seguidament, podries provar a crear un usuari nou i veure si l'escriptori li funciona correctament. Així sabries si és cosa de que ha quedat algun paquet important tocat o que només és la configuració del teu usuari.

---

### Post by rogespierre on 2008-05-21
he tornat  a iniciar i tot ha tornat al seu lloc... mmm, millor aixi

gràcies de totes maneres!:)

---

### Post by RainCT on 2008-05-21
Com a futura referència, pel que sembla el problema que tenies és que no t'anava el gestor de finestres. La manera més fàcil d'explicar de com solucionar el problema és tancar la sessió i tornar a entrar, però naturalment tenim una alternativa millor:

Obrir la terminal (Aplicacions -> Accessoris -> Terminal) i executar-hi "metacity --replace &" (o, si s'utilitzen els efectes d'escriptori, "compiz --replace &") i un cop acabi premer enter i executar "disown %%" (cosa que ens permetrà de tancar la finestra i que el gestor de finestres continui funcionant). En cas que les icones no apareguin a l'escriptori, prémer Alt+F2 i allà executar-hi "nautilus".

---

### Post by pespin on 2008-05-21
> Com a futura referència, pel que sembla el problema que tenies és que no t'anava el gestor de finestres.

Diria que aquest no és el problema, perquè a mi em sembla que m'ha passat el mateix algun cop. Es com si petés l'escriptori visual, és a dir, el que és veu de fons que està al directori -/Escriptori. Quan m'ha passat això alguna vegada, també m'ha desaparegut el fons de pantalla i s'ha quedat el fons negre. I com es diu més a dalt, no pots interaccionar amb ell. No crec que tingui gaire a veure amb el gestor de finestres, però potser estic equivocat :)

i com bé dius, reiniciant el sistema gràfic ja funciona.

---

### Post by papapep on 2008-05-21
> he tornat a iniciar i tot ha tornat al seu lloc... mmm, millor aixi


Vols dir que ni tan sols havies provat a reiniciar l'ordinador abans d'iniciar el fil??

---

### Post by RainCT on 2008-05-22
> **pespin said:**
> No crec que tingui gaire a veure amb el gestor de finestres, però potser estic equivocat :)

Pot ser. Per això també he dit de fer Alt+F2 -> "nautilus".

És el Nautilus el que s'encarrega de les icones del fons de pantalla i del menú del botó dret, i a mi també m'ha passat alguna vegada que ha fet el *tonto* alguna vegada, però iniciant-lo de nou tal com dic a dalt el problema sempre se m'ha arreglat.

---

### Post by rogespierre on 2008-06-17
ara em passa ja sempre per molt que renicii... les icones no apareixen a l'escriptori i no s'hi pot interactuar

he escrit això de compiz i disown al terminal... xo tot segueix igual

no sé on he de fer alt+f12 però no em surt res, i no se q es el nautilus

i això de reniciar el sistema visual tampoc se que es...

bé, a veure si em podeu ajudar gràcies

---

### Post by pespin on 2008-06-18
> **rogespierre said:**
> ara em passa ja sempre per molt que renicii... les icones no apareixen a l'escriptori i no s'hi pot interactuar

he escrit això de compiz i disown al terminal... xo tot segueix igual

no sé on he de fer alt+f12 però no em surt res, i no se q es el nautilus

i això de reniciar el sistema visual tampoc se que es...

bé, a veure si em podeu ajudar gràcies


A mi també em passava sovint fa uns dies, i la solució d'en RainCT no funcionava, però ara ja deu fer més d'una setmana que no em passa. Prova a actualitzar la paqueteria a veure si ja se t'arregla. 

Per reiniciar el sistema gràfic (apaga la sessió que tens oberta i torna a la pantalla de Login): **CTRL+ALT+BACKSPACE** (lletra de borrar)

---

