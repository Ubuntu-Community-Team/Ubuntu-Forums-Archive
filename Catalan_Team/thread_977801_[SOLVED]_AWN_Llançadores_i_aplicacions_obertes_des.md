---
title: "[SOLVED] AWN Llançadores i aplicacions obertes desaparegudes"
date: 2008-11-10
forum: Catalan Team
---

### Post by Omit7 on 2008-11-10
Hola a tothom,

Acabo d'actualitzar a Intrepid Ibex. El funcionament en general tot be però l'AWN no acaba de funcionar com caldria.

M'han desaparegut les llançadores i quant obro una aplicació o una finestra nova no apareixen a la barra. He verificat la configuració i a la pestanya de les llançadores si m'apareixen però a la barra no.

He probat a desinstal·lar i tornar a instal·lar però res de res. He buscat per el forum a veure si trobava alguna solució però no trobo res semblant.

Gràcies anticipades per l'ajuda.

---

### Post by open-pitu on 2008-11-10
Bones!

Personalment vaig utilitzar durant un any o més Avant Window Navigator, fins que vaig descobrir Cairo-dock. Molt més personalitzable, més temes de sèrie, més estable... en definitiva millor (si més no per la meva experiència).

És molt fàcil d'utilitzar i instal·lar aquí et deixo els passos:

```
sudo gedit /etc/apt/sources.list
```

Afegim el repositori per Cairo-Dock

[INDENT]```
# Afegim aquestes per Cairo-Dock
# deb http://repository.cairo-dock.org/ubuntu gutsy cairo-dock
```[/INDENT]

Executem des de terminal

```
$ wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install cairo-dock cairo-dock-plug-ins
```
$ cairo-dock[/CODE]

I ja el tens en marxa. Ja pots triar el tema, l'estructura, applets... A mi m'ha agradat molt més que AWN.

(Sento no contestar-te lo de l'AWN, però el què faig és donar-te una solució amb un programa del mateix estil)

---

### Post by oriolsbd on 2008-11-10
Hola, si vas a la configuració de l'AWN, a l'apartat d'Applets has de tenir activat el que es diu "Launcher/Taskmanager". El tens activat?

Salut!

---

### Post by Omit7 on 2008-11-11
Ondia!!!! Doncs mes fàcil no podia ser. Nomes havia d'activar el launcher/taskmanager i ja està. Això es allò que diuen de la novatada no? ;-)

Gràcies oriolsbd per l'ajuda.

open-pitu dons el cairo-dock no el conec però el probaré a veure que tal i em quedaré amb el que mes em convenci. Gràcies també a tu.

---

