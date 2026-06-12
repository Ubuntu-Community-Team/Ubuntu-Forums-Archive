---
title: "[SOLVED] audio"
date: 2008-06-16
forum: Catalan Team
---

### Post by grundt on 2008-06-16
Hola,
m'he instalat la nova versió de l'ubuntu,
normalment veig les pelicules amb l'VLC media player,
però ara l'audio va fent uns talls,que abans no feia,
sabeu si és questió d'algun codec?

---

### Post by orestesmas on 2008-06-16
Pot ser cosa del PulseAudio, el nou servidor de so que han posat.

Prova de dir-li al VLC que "passi" del PulseAudio i que ataqui l'ALSA directament.

EDITO: Bé, l'anterior frase és inexacta (ho sento, no conec encara massa bé el PulseAudio). Sembla (segons la viquipèdia) que el que caldria fer és dir-li a l'ALSA que ataqui el maquinari directament, en lloc d'atacar un maquinari virtual proveït pel PulseAudio.

Per tant, obre el VLC, vés a Paràmetres -> Preferències -> Àudio -> Mòduls de sortida -> ALSA, i com a dispositiu per omissió li poses la targeta de so, que deu ser el hw:0,0 (és el més usual)

---

### Post by grundt on 2008-06-18
He fet el que m'has dit i ha funcionat, gràcies.

---

### Post by orestesmas on 2008-06-18
Doncs me n'alegro :-)

Si et plau, pren-te uns segons per afegir el [SOLVED] al títol del fil.

---

### Post by grundt on 2008-06-18
Gràcies.

---

