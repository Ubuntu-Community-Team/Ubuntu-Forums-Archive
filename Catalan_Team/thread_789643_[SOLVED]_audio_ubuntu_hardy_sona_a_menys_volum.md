---
title: "[SOLVED] audio: ubuntu hardy sona a menys volum"
date: 2008-05-10
forum: Catalan Team
---

### Post by diablessamariken on 2008-05-10
Hola!

Bé, havia intervingut aprofitant un altre fil antic, però crec que ara la cosa se separa una mica d'aquella temàtica i per això en creo un de nou.

Des que vaig actualitzar a Hardy que el volum màxim de l'ordinador ha disminuït respecte a la versió anterior. He comprovat tots les opcions de pujar i baixar volums, i fins i tot he seguit la recomanació del fil anterior en què em suggerien que triés el servidor ALSA per a totes les opcions de so. Però res ho ha millorat. 
Algú s'ha trobat amb el mateix cas? Alguna idea?

Gràcies!
Astrid

---

### Post by SiscoGarcia on 2008-05-10
Astrid, crec que hauries de posar l'enllaç al [fil]("http://ubuntuforums.org/showthread.php?t=778900") a què fas referència per tal d'entendre-ho millor, no?

Per cert, jo també faig anar Hardy i no hi he trobat cap diferència de volum.

---

### Post by RainCT on 2008-05-11
Per estar segurs de que no és aquest el problema, has provat pujant **tots** els controls de volum (Mestre, Master Mono, Headphone, PCM, etc.)?

---

### Post by diablessamariken on 2008-05-11
HOla

jo diria que he pujat tots els volums, almenys, els que es fan anar des del teclat, el del quadre superior (just al costat de la data) i els dels programes reproductors de música. Però tot i així no millora gaire... Podria mirar de pujar més volums en algun lloc? 

coses estranyes... 

Per cert, aquest és l['enllaç al fil]("http://ubuntuforums.org/showthread.php?t=778900") del que parlava inicialment (a la llarga aprendré a fer els comentaris complets... :)  )

---

### Post by diablessamariken on 2008-05-11
Hola

ja he solucionat el problema. He trobat el comentari de resposta d'un tal Roberto Briones en el següent [post]("http://www.paraisogeek.com/que-pasa-con-ubuntu-hardy-heron/")

I introduint ```
alsamixer
```
he pogut regular tots els volums del sistema. N'hi havia un que estava força més baix del màxim. Només ha calgut pujar-lo i llestos. Ara sona com abans.

Per tant, i a falta d'etiquetes, SOLVED.

Astrid

---

### Post by RainCT on 2008-05-12
> **diablessamariken said:**
> I introduint *alsamixer* he pogut regular tots els volums del sistema. N'hi havia un que estava força més baix del màxim. Només ha calgut pujar-lo i llestos.

Sí, és això el que et comentava. Pots fer-ho de forma gràfica fent doble clic a la icona del quadre superior perquè obri la finestra "controlador del volum" i allà anant a Edita -> Preferències i marcant-hi totes les opcions (llavors t'apareixen controls per a tots els volums i allà podries haver pujat el que estava baix).

[[img]http://img379.imageshack.us/img379/8968/controldelvolumrf6.th.png[/img]](http://img379.imageshack.us/img379/8968/controldelvolumrf6.png)

---

