---
title: "Flash natiu per a 64bits!"
date: 2008-11-18
forum: Catalan Team
---

### Post by PatrickVogeli on 2008-11-18
Hola gent!

Per un cop, sembla que linux s'avança a windows en el tema flash, i es que ja ha sortit una primera versió pre-alfa del connector flash d'Adobe especific per a arquitectures de 64bits.

Jo de moment l'estic fent servir i sembla que va prou bé, diria que va millor que la versió de 32 bits amb l'nspluginwrapper.

**Per instal·lar-lo:**

```

cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo apt-get remove --purge flashplugin-nonfree nspluginwrapper
killall firefox ## COMPTE, AIXÒ TANCARÀ EL FIREFOX!!!
tar -xvf libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/

```

Si ara obriu el firefox, haurieu d'estar funcionant amb la nova versió. Ho podeu comprovar a about:plugins i assegurant-vos que, en la informació referent al firefox, la versió és la Shockwave Flash 10.0 d20

**Per desinstal·lar-lo:**

```

sudo rm -rf /usr/lib/firefox-addons/plugins/libflashplayer.so
killall firefox
sudo apt-get install flashplugin-nonfree

```

salut!

---

### Post by SnowTDM on 2008-11-19
Moltes gràcies, de moment funciona perfectament.

Salutacions

---

### Post by CarlesOriol on 2008-11-20
> **PatrickVogeli said:**
> Per un cop, sembla que linux s'avança a windows... 

i al Mac!!

---

### Post by SiscoGarcia on 2008-11-20
> **PatrickVogeli said:**
> Per un cop, ...

Tant de bo això vulgui dir "per primer cop, ..."

---

