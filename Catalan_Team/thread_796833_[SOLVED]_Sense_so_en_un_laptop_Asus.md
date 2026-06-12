---
title: "[SOLVED] Sense so en un laptop Asus"
date: 2008-05-16
forum: Catalan Team
---

### Post by jamomila on 2008-05-16
He instal·lat l'Ubuntu 8.04 en un laptop Asus Z53 i no aconsegueixo de cap manera tenir so. Tots els controls estan al màxim i no sento res. En el Totem apareixen imatges en moviment seguint la música, per tant sembla que detecta so però no se sent.
Si algú sap la solució li agrairia enormement...

---

### Post by SiscoGarcia on 2008-05-16
Benvingut/da jamomila,

Hauries de fer almenys dues coses abans de res, passar-te pel [fil de benvinguda]("http://ubuntuforums.org/showthread.php?t=562776") per presentar-te i llegir-te el [fil que conté algunes pautes per millorar l'entesa al fòrum]("http://ubuntuforums.org/showthread.php?t=599965").

Dit això, i lligant amb l'últim apunt, si haguessis buscat una mica pel fòrum hauries vist que [ahir un company feia una pregunta sense haver cercat com tu i en el mateix sentit]("http://ubuntuforums.org/showthread.php?t=795216"), no fa gaire [s'havia parlat al respecte del so i Hardy  i s'havia trobat una solució]("http://ubuntuforums.org/showthread.php?t=795216").

Salut!

---

### Post by jamomila on 2008-05-17
Hola SiscoGarcia,

Ja he passat pel fil de benvinguda i m'he presentat, us demano perdó.
Ja havia buscat pel fòrum però no és el mateix problema d'en MiquelBLL. Jo no havia instal·lat abans la 7.10 i a mi el so no és que soni més fluix, és que no sona gens ni mica. Les solucions proposades a l'altre fil tampoc m'han solucionat el problema i és per això que n'he obert un.

Gràcies

---

### Post by papapep on 2008-05-17
Benvingut Jamomila,

Primer caldria que busquessis a veure quina placa d'audio tens en concret fent a un terminal:

```
lspci | grep Audio
```

i enganxa aquí el que et surti.

---

### Post by SiscoGarcia on 2008-05-18
> **jamomila said:**
> Hola SiscoGarcia,

Ja he passat pel fil de benvinguda i m'he presentat, us demano perdó.
Ja havia buscat pel fòrum però no és el mateix problema d'en MiquelBLL. Jo no havia instal·lat abans la 7.10 i a mi el so no és que soni més fluix, és que no sona gens ni mica. Les solucions proposades a l'altre fil tampoc m'han solucionat el problema i és per això que n'he obert un.

Gràcies

jamomila, tampoc cal que et disculpis, crec que és normal que busquis com solucionar el teu problema i no pensis a presentar-te. Pel que fa al problema concret potser també t'hauria de demanar perdó jo, però la clau està a descriure el millor possible el problema i el que s'ha fet fins el moment, d'aquesta manera jo no ho hauria confos.

Benvingut/da en qualsevol cas.

---

### Post by jamomila on 2008-05-18
Bona tarda,

Això és el que em surt:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Gràcies papapep, a veure què hi trobem...

SiscoGarcia,tens tota la raó: potser no m'havia explicat prou bé però pensa que sóc bastant profà en el tema. Gràcies també.

Jamomila

---

### Post by papapep on 2008-05-18
Bé, tinc una notícia bona i una de dolenta, :-D

La bona és que el problema està identificat:[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133)

La dolenta és que no té solució, actualment, en tots els casos i en cap cas és "precisament" simple. En el teu cas crec que la possible solució és la H (però tampoc és segur):[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by jamomila on 2008-05-18
Molt bé papapep, ja t'ho explicaré quan ho hagi provat.

Moltes gràcies, us mantindré informats.

Jamomila

---

### Post by jamomila on 2008-05-19
Bé, ja ho he provat.
La solució que em donava papapep era instal.lar l'última versió de l'Alsa 1.0.15 i crear un fitxer a /etc/modutils amb el següent:

 alias char-major-116 snd
 alias snd-card-0 snd-hda-intel
 # module options should go here
 options snd-hda-intel model=lenovo

 # OSS/Free
 alias char-major-14 soundcore
 alias sound-slot-0 snd-card-0

 # card #1
 alias sound-service-0-0 snd-mixer-oss
 alias sound-service-0-1 snd-seq-oss
 alias sound-service-0-3 snd-pcm-oss
 alias sound-service-0-8 snd-seq-oss
 alias sound-service-0-12 snd-pcm-oss

 options snd-hda-intel model=lenovo

i afegir l'última línia al final del fitxer /etc/modprobe.d/alsa-base , després reiniciar.

He verificat la versió d'Alsa i tinc l'última (1.0.15), he creat el fitxer amb la seqüència que he escrit més amunt i he reiniciat: tot ha seguit igual, o sigui mut però quan he afegit l'última línia:

options snd-hda-intel model=lenovo

al fitxer /etc/modprobe.d/alsa-base , aleshores, després de reiniciar ha començat a produir un so d'acoplament molt agut molt molest i abans d'iniciar l'entorn gràfic s'ha penjat però continuant fent el so tan molest i fort. Ha donat una sèrie d'errors i no ha avançat més. He hagut de resetejar la bateria del portàtil.
Cada cop que l'engego passa el mateix però encara no canviat res ja que no puc. Només em queda reinstal·lar l'Ubuntu sencer.

No sé si us ho he explicat bé.

---

### Post by jamomila on 2008-05-20
Per fi he trobat la solució en el següent enllaç:
[http://ubuntuforums.org/showthread.php?t=616845&highlight=lenovo+3000+n200+%2B+sound](http://ubuntuforums.org/showthread.php?t=616845&highlight=lenovo+3000+n200+%2B+sound)

fent:
[B]cat /proc/asound/card0/codec#* | grep Codec
[/B]
m'ha donat informació de la meva placa; en el meu cas:

Realtek ALC660VD
Motorola Si3054

En el llistat de l'enllaç que us he dit apareix:

ALC861VD/660VD
3stack 3-jack
3stack-dig 3-jack with SPDIF OUT
6stack-dig 6-jack with SPDIF OUT
3stack-660 3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo Lenovo 3000 C200
dallas Dallas laptops
hp HP TX1000
auto auto-config reading BIOS (default)

Aleshores he editat el fitxer **/etc/modprobe.d/alsa-base**

i a la primera línia he afegit el següent:

**options snd-hda-intel model=hp**

He reiniciat i el so ha aparegut per art de màgia (tambors, musiqueta, etc.)

Cal dir que enlloc de hp (el meu ordinador és Asus) podeu provar lenovo, dallas i base. Jo he provat hp i m'ha funcionat.

Espero que a algú li pugui servir. Jo ja portava temps al darrera  d'aquesta solució i finalment l'he trobat.

Bona nit

---

