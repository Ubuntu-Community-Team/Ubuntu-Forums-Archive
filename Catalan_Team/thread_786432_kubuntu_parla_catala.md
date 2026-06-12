---
title: "kubuntu parla catala?"
date: 2008-05-08
forum: Catalan Team
---

### Post by fonde on 2008-05-08
hola familia

ara que ja torno a tenir connexio d'internet amb el meu kubuntu 8.04 tinc una pregunta

la versio catalanitzada que surt en aquest tros de forum qu`e es ben be?
perqu`e jo tinc el kubuntu en angl`es basicament,tot i haver fet l'instal·lacio en catala.
per pes i format m'imagino que deu ser un cd d'instal·lacio de kubuntu no?

saluuut!


franki llibertat!

---

### Post by lesergi on 2008-05-08
Hola!!

Si vols tenir la Kubuntu catalanitzada, l'únic que has de fer és anar a:

Menú K->System Settings->Country & Language->Install New Language, i després, un cop instal·lat, Select System Language->Catalan.

Hauràs de reiniciar.

Ja em contes.

---

### Post by orestesmas on 2008-05-09
Bé, jo no ho faria així (de fet, no sé perquè instal·lar una nova llengua tal i com dius tu, a mi no em funciona).

Jo instal·laria amb l'Adept els paquets "language-support-ca" i "language-pack-ca", i llavors ja m'apareixeria el català al Menú K->System Settings->Country & Language, i podria posar-lo allí com a llengua per omissió.

Però de fet el que preguntava Fonde no era això, sinó que ell volia saber què era aquest CD "catalanitzat". Bàsicament el CD aquest és un CD d'instal·lació de kubuntu en el que hi he substituït les llengües que hi venen per omissió per el català, amb la qual cosa no només la instal·lació es pot fer en català, sinó que una vegada instal·lat totes les aplicacions ja et queden en català.

---

### Post by lesergi on 2008-05-09
Hola orestesmas!

Cal fer-ho d'eixa forma perquè el sistema estiga en català, sino únicament ho estarà el KDE.

De totes formes, respecte al CD d'instal·lació, sempre ho he instal·lat des de l'original en català triant a l'inici amb F2 la llengua i no he hagut de canviar res.

Salut!

---

### Post by LitusMayol on 2008-05-09
> Bàsicament el CD aquest és un CD d'instal·lació de kubuntu en el que hi he substituït les llengües que hi venen per omissió per el català, amb la qual cosa no només la instal·lació es pot fer en català, sinó que una vegada instal·lat totes les aplicacions ja et queden en català.

Renoi Orestes, quina feina! Molt bé! Això pels que no n'entenen massa deu ser genial. Jo vaig començar amb una Live en anglès però amb un amic que en sabia prou(el de l'Atzusac d'en Tux a Sant Cugat, en Juli).

Merci per facilitar aquest tipus de coses.

---

### Post by orestesmas on 2008-05-09
Bé, jo penso que fent-ho de les dues maneres sempre et queda *tot* el sistema en català, perquè jo no he parlat d'instal·lar únicament el paquet language-pack-kde-ca, sinó el language-pack-ca el qual, si et mires les dependències, depèn de les traduccions del sistema base, de les del gnome i de les del kde.

D'altra banda reitero que si vaig via "System Settings", a mi en clicar el botó de "Install New language" no em fa res. Deu ser un bug, no sé.

finalment, si tries l'idioma català en la instal·lació, et deixa el sistema final en català *únicament si durant la instal·lació tens connexió a internet i l'instal·lador és capaç de detectar-la i configurar-la correctament*. En cas contrari et quedarà un sistema en anglès, perquè les traduccions en català no estan incloses al CD original (però sí al DVD, que té més espai).

Aquest cas és típic si ho estàs instal·lant en un PC sense connexió a xarxa o en un portàtil en què la connexió a internet és per Wifi però per activar-la necessita descarregar-se prèviament uns controladors privatius que no venen al CD per qüestions legals. En aquest cas no tens més remei que connectar-te per cable tan per baixar-te els paquets d'idioma com per activar la wifi... Llavors és quan fer una versió catalanitzada té sentit.

---

### Post by lesergi on 2008-05-09
Aaaaaaammmmmmmm... Es de veres que es necessita Internet per configurar l'idioma a la instal·lació... No he caigut hehe.

Respecte a l'idioma, encara que instal·les el language-pack-ca la variable d'entorn del sistema se't canvia a "ca_ES"?

Salut i força al canut!

---

### Post by orestesmas on 2008-05-09
Jo diria que la variable d'entorn és independent dels paquets d'idioma que instal·lis. Per exemple, pots tenir instal·lades tantes llengües com vulguis i anar canviant entre elles (cosa que et farà variar la variable LANG a ca_ES, en_US, fr_FR, etc...)

D'altra banda la cosa és més complexa, perquè pots tenir configurada una llengua a nivell global del sistema, només per l'entorn d'escriptori, o fins i tot pots executar una aplicació concreta amb una llengua diferent a la d'omissió: només cal invocar-la amb un valor de la variable LANG canviat.

Per veure això últim, obre un terminal i tecleja:
```

date
LANG=en_US.utf8 date

```

i veuràs els efectes d'allò que dic.

---

### Post by lesergi on 2008-05-09
Ja per això deia jo de canviar la llengua del sistema des del Kcontrol, sinó ho fa quan execute una aplicació no-KDE es mostrarà en anglès si la instal·lació es va fer en anglès.

Vinga, a cuidar-se!

---

### Post by fonde on 2008-05-09
gràcies!

ja gaudeixo d'un OS amb la meva llengua!!

---

### Post by lesergi on 2008-05-09
Linux rocks!

---

### Post by CarlesOriol on 2008-05-10
> **lesergi said:**
> Kcontrol

i en kde4 el kcontrol es diu systemsettings

---

### Post by lesergi on 2008-05-10
> **CarlesOriol said:**
> i en kde4 el kcontrol es diu systemsettings

I al KDE3 del Kubuntu també es systemsettings, però utilitzen els mateixos mòduls :razz:

A cuidar-se!

---

