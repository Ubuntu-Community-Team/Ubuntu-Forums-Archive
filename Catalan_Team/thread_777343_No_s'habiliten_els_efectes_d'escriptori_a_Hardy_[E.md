---
title: "No s'habiliten els efectes d'escriptori a Hardy [Era:Problema amb Ubuntu 8.04]"
date: 2008-05-01
forum: Catalan Team
---

### Post by ktix007 on 2008-05-01
Acabo d'instal·lar l'ubuntu 8.04 i quan vull activar els efectes em diu: "No s'han pogut habilitar els efectes d'escriptori" hi ha alguna solució?

---

### Post by papapep on 2008-05-01
Benvingut al fòrum Ktix007.

Seria bo que fessis un cop d'ull al fil que pretèn explicar als nous com treure més profit del fòrum. Si no ens dones informació, és molt difícil que et poguem ajudar [http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)

També et convido a passar pel fil de benvinguda a fi de saber alguna cosa més de tu :-) [http://ubuntuforums.org/showthread.php?t=562776](http://ubuntuforums.org/showthread.php?t=562776)

Per cert, posar un títol que indiqui de què va el tema també pot fer que algú que en sàpiga la solució s'hi fixi i t'ajudi. "Problema amb Ubuntu" el podrien tenir gairebé tots els fils en aquest fòrum ;-)

---

### Post by CarlesOriol on 2008-05-01
Sí

---

### Post by papapep on 2008-05-01
Pels que no sapigueu CarlesOriolenc, en Carles ha sintetitzat en dues lletres, una sil·laba, una paraula tot el meu post anterior :-D

---

### Post by ktix007 on 2008-05-01
Molt bé, però no em podrieu solucionar el problema? Si us plau?

---

### Post by RainCT on 2008-05-01
A pregunta incompleta, resposta incompleta... Si no ens dones més informació ho tenim difícil.

Per exemple, podries començar per dir-nos quina targeta gràfica tens.

---

### Post by papapep on 2008-05-01
> Molt bé, però no em podrieu solucionar el problema? Si us plau?

Ja t'he intentat explicar que no dones la informació que cal per a poder-te ajudar. Podem saber, o no, de coses d'ordinadors, però no som adivins. Sinó expliques quin ordinador, placa gràfica, sabor d'ubuntu, etc, tens, es com si vas al metge i li dius que et fa mal però no li dius on.

---

### Post by ktix007 on 2008-05-01
Tinc una NVIDIA Quadro de 64 MB

---

### Post by pespin on 2008-05-01
fes un "sudo aptitude search nvidia-glx" a la terminal i mira si de la llista que et surt, apareix una "i" a l'esquerra d'alguna línia. Així sabrem si tens instal·lats els drivers necessaris per a utilitzar efectes d'escriptori / 3d.

Per exemple, jo tinc instal·lats els nvidia-glx-new:

```
p   nvidia-glx                                             - NVIDIA binary XFree86 4.x/X.Org driver
p   nvidia-glx-dev                                         - NVIDIA binary XFree86 4.x/X.Org driver development files
p   nvidia-glx-legacy                                      - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver
p   nvidia-glx-legacy-dev                                  - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development file
i   nvidia-glx-new                                         - NVIDIA binary XFree86 4.x/X.Org 'new' driver
p   nvidia-glx-new-dev                                     - NVIDIA binary XFree86 4.x/X.Org 'new' driver development files
```


Si tens algun d'aquests paquets instal·lat, escriu la ordre "glxinfo | grep rendering" i mira si posa Yes o No. La pregunta a aquesta resposta és si tens l'acceleració 3d de la targeta funcionant.

Si et diu que no troba el programa glxinfo, instal·lal amb: sudo aptitude install mesa-utils

---

### Post by ktix007 on 2008-05-02
He fet el que m'has dit i em surt això:

p   nvidia-glx                      - NVIDIA binary XFree86 4.x/X.Org driver    
p   nvidia-glx-dev                  - NVIDIA binary XFree86 4.x/X.Org driver dev
i   nvidia-glx-legacy               - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
p   n****vidia-glx-legacy-dev           - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
p   nvidia-glx-new                  - NVIDIA binary XFree86 4.x/X.Org 'new' driv
p   nvidia-glx-new-dev              - NVIDIA binary XFree86 4.x/X.Org 'new' driv

i després quan posu "glxinfo | grep rendering" em diu "Yes"

Què faig ara?

---

### Post by ktix007 on 2008-05-02
Algú em pot contestar si us plau? pespin?

> He fet el que m'has dit i em surt això:

p nvidia-glx - NVIDIA binary XFree86 4.x/X.Org driver
p nvidia-glx-dev - NVIDIA binary XFree86 4.x/X.Org driver dev
i nvidia-glx-legacy - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
p nvidia-glx-legacy-dev - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
p nvidia-glx-new - NVIDIA binary XFree86 4.x/X.Org 'new' driv
p nvidia-glx-new-dev - NVIDIA binary XFree86 4.x/X.Org 'new' driv

i després quan posu "glxinfo | grep rendering" em diu "Yes"

Què faig ara?

---

### Post by papapep on 2008-05-02
Ktix007, això no és un servei d'assistència tècnica pagat. Si ningú et respon pot ser perquè no poden o no en saben o no els ve de gust en aquest moment. Crec que no t'has llegit l'enllaç que et vaig passar a la meva primera resposta amb suficient "carinyo".

---

### Post by ktix007 on 2008-05-02
perdó però es k haig de marxar i no torno fins d'aquí a uns dies i m'agradaria molt saber com ho puc posar

---

### Post by climent on 2008-05-02
L'experiència m'ha ensenyat que les presses mai no són bones. En el terminal, fes sudo compiz compizconfig-settings-manager emerald. Fet això, vas a Sistema-Preferències i hauries de tenir una opció "Copnfiguració avançada dels efectes d'escriptori", on tens tot el ventall d'efectes. I a jugar!!!

I subscric totalment el consell donat: fes una cerca en els fils i googleja.

---

### Post by ktix007 on 2008-05-02
Ja ho fet però no em surt "Configuració avançada dels efectes d'escriptori" a sistema/preferències.

El terminal em diu això:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0103 (rev 10) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by ktix007 on 2008-05-03
Ara ja em surt a Sistema/Preferències "Configuració avançada dels efectes d'escriptori" però igualment no em serveix per res perquè encara no me'ls deixa activar.

---

### Post by climent on 2008-05-04
A Sistema-Preferències-aparença-efectes visuals, has activat a la part inferior l'opció "extra"?

---

### Post by ktix007 on 2008-05-04
He intentat activar el que diu normal i el que diu extra per`tots dos em diuen "No s'han pogut habilitar els efectes d'escriptori"

---

### Post by pespin on 2008-05-04
Executa el programa via terminal i enganxa aquí el que et mostri la terminal en activar els efectes:

```
gnome-appearance-properties
```

---

### Post by ktix007 on 2008-05-04
Em diu això:
```
No hi ha cap controlador gràfic per al vostre sistema que funcioni amb l'extensió de composició.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0103 (rev 10) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

---

