---
title: "[SOLVED] Connectors per a vídeos en format rm dins de webs"
date: 2008-11-18
forum: Catalan Team
---

### Post by abuch on 2008-11-18
Hola,

estic intentant veure vídeos del web edu3.cat (format Real Media) sense haver-los de baixar i reproduir amb el realplayer. El Firefox m'ofereix d'instal·lar 3 connectors (xine, gecko-plugin i mplayer). D'aquests, només el mplayer funciona parcialment, reproduint el so però no la imatge. Tampoc no funciona si faig servir el realplayer com a plugin per al Firefox.

Algú té alguna solució per aquest problema?

Gràcies per avançat.

Aleix

---

### Post by SiscoGarcia on 2008-11-18
Ja tens instal·lats els "ubuntu-restricted-extras"?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by abuch on 2008-11-19
> **SiscoGarcia said:**
> Ja tens instal·lats els "ubuntu-restricted-extras"?

```
sudo apt-get install ubuntu-restricted-extras
```

Sí, ja estan instal·lats.

---

### Post by lesergi on 2008-11-19
Ei hola!

Has provat amb el gecko-mediaplayer??

He estat provant i a mi sí que em funciona. Prova també instal·lar-te el paquet w32codecs des del repositori [Medibuntu](http://www.medibuntu.org/).

Vaja bé!

---

### Post by abuch on 2008-11-20
> **lesergi said:**
> Ei hola!

Has provat amb el gecko-mediaplayer??

He estat provant i a mi sí que em funciona. Prova també instal·lar-te el paquet w32codecs des del repositori [Medibuntu](http://www.medibuntu.org/).

Vaja bé!

Hola,

ha estat instal·lar w32codecs i començar a funcionar, amb el plugin mplayer. No l'he provat amb el gecko-mediaplayer.

Moltes gràcies!

Aleix

---

