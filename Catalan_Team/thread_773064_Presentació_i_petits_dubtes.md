---
title: "Presentació i petits dubtes"
date: 2008-04-28
forum: Catalan Team
---

### Post by Alcadissar on 2008-04-28
Hola amics d'Ubuntu en català.

Vaig conèixer aquest fòrum gràcies a la vostra presentació a Caldes. Aquell mateix dia vaig instal·lar-me la nova Ubuntu i vaig començar a trastejar...

Val a dir que ja havia provat forces distribucions de linux, però la configuració del PC (un tan especial) em feia sempre desistir.

Després de 2 dies aquests són el mèrits que he aconseguit.He fet funcionar la targeta de so EMU-1212m configurant ALSA. Funciona amb el driver de la SB Audigy tal i com posa a la pàgina d'ALSA. Em funcionen més o menys correctament tots els perifèrics i totes les unitats i tinc una resolució bona.

- Problema número 1: La targeta està configurada per sonar a 48khz, quan hauria d'estar a 44,1khz perquè sonés bé. He provat de fer alsamixer per canviar el freqüència, i ho he acoseguit, però tot i que després faig alsactl store, no es queden els canvis i sempre que encenc Ubuntu en torna a 48khz.

- Problema número 2: La meva paleta gràfica Wacom no funciona com a llapis, sinó com a ratoli, no sé com es poden canviar les opcions de la paleta.

- Problema número 3: Em funcionen tots els programes d'audio i em sonen a la perfecció, però els sons del sistema no sonen. Crec que té a veure amb Pulseaudio, que me'ls envia per la targeta de so de la placa. Com puc fer perquè els sons de sistema sonin també per la targeta.

- Problema número 4: Tinc una ATI Radeon 9250.

- Problema número 5: No puc configurar la segona pantalla per fer un escritori extès. Amb la versió 7.10 ho havia aconseguit, i amb SUSE també, però ara el xorg.cong apareix diferent al que estava acostumat a veure.


Si algú té respostes a aquestes preguntes molt gràcies per endavant.

El meu PC és un AMD Athlon 64 bits amb la targeta de so i gràfica que ja he dit.

---

### Post by SiscoGarcia on 2008-04-28
Hola Alcadissar, benvingut al fòrum (per cert, com diuen els mestres, passa't pel fil de benvinguda i explica'ns sobre tu). Me n'alegro que t'hagis "convertit" a ubuntu. Anem a pams:

1.- Has de tenir en compte una màxima del fòrum, "cada problema un fil i cada fil un problema", d'aquesta manera és més fàcil donar-te solucions i a més és més efectiu per d'altra gent que pugui tenir els teus problemes. En aquest sentit estaria bé que et miressis el [fil de començament]("http://ubuntuforums.org/showthread.php?t=599965") que ha fet el papapep.

2.- Pel que fa a ajudar-te en els problemes que comentes, jo sento no poder fer gran cosa. Els meus coneixements són limitats però pel que fa al problema número 4, crec que et seria de grana ajuda fer servir l'[envy]("http://albertomilone.com/nvidia_scripts1.html") que serveix per instal·lar els drivers d'ATI i d'NVIDIA.

Espero que et vagi bé, i que altres puguin ajudar-te en els altres problemes.

Fins aviat!

---

### Post by RainCT on 2008-04-29
> **Alcadissar said:**
> - Problema número 3: Em funcionen tots els programes d'audio i em sonen a la perfecció, però els sons del sistema no sonen. Crec que té a veure amb Pulseaudio, que me'ls envia per la targeta de so de la placa. Com puc fer perquè els sons de sistema sonin també per la targeta.

Has mirat que a Sistema -> Preferències -> So estigui configurat per a utilitzar la targeta i el servidor de so adequats?


> **Alcadissar said:**
> - Problema número 4: Tinc una ATI Radeon 9250.

Com ja ha dit en Sisco, prova amb l'Envy NG.


> **Alcadissar said:**
> - Problema número 5: No puc configurar la segona pantalla per fer un escritori extès. Amb la versió 7.10 ho havia aconseguit, i amb SUSE també, però ara el xorg.cong apareix diferent al que estava acostumat a veure.

Espero que no soni a resposta tonta, però com que només parles del xorg.conf, has provat a Sistema -> Preferències -> Resolució de la pantalla?

---

