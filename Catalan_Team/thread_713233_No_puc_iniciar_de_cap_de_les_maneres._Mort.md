---
title: "No puc iniciar de cap de les maneres. Mort???"
date: 2008-03-02
forum: Catalan Team
---

### Post by almogabber on 2008-03-02
Us explico des del principi, perquè us situeu:
    - Volia provar l'escriptori KDE, però el que no sabia és que ja el tenia, i l'únic que havia de fer era triar-lo a l'iniciar la sessió, però com que no ho sabia vaig instalar un paquet 'general' de KDE. Amb jocs, navegadors, editos de fotos.. molts, molts programes (no puc posar quin paquet era exactament, perquè ara estic amb win).
    - Un cop fet això, i després de descobrir que no era d'aquesta manera, que el que havia fet no era instalar un nou escriptori, vist que molts no em servien de res, he volgut fer l'operació inversa. Esborrar l'instal·lat.
    - Igual que he fet abans, busco <kde> al sinaptic, y vaig revisant el que està instal·lat per desintalar-ho.

Doncs m'he passat de llarg. Alguna cosa he desinstalat i ara no puc entrar ni a la pantalla de benvinguda.
Val a dir que la desinstalació ha acabat amb errors, i ha deixat de respondre. He hagut de reiniciar per la força. Abans d'entrar en coma m'ha saltat un error dient que el Network Manager no podia respondre, perquè faltaven "connectors".

Bé, doncs ara només puc entrar en mode consola. Tant si trio el mode a prova d'errors com al normal des del grub. Com dic, no arriba a la pantalla de benvinguda.

Com és lògic, no en tinc ni idea del "mode consola".

Hi ha alguna manera de fer una comprovació dels errors, o tornar a instalar el que possiblement falti o així??

Espero no haver de tornar a començar de 0... :S

Gràcies, i socors!!!!

---

### Post by menut on 2008-03-02
Si tens connexió a internet, per què no proves a tornar a instal·lar el KDE per la consola, i un cop instal·lat, mirar-ho amb calma?

Prova un:
```
sudo apt-get install kde
```

Instal·larà el KDE i molts paquets, la majoria programes.

---

### Post by patrickfromspain on 2008-03-02
jo diria que el mes facil es, si tens conexio a internet: sudo aptitude install ubuntu-desktop

salut!

---

### Post by papapep on 2008-03-02
Potser l'únic que t'has carregat de més és el gdm, el gestor gràfic d'autenticació. Podries provar amb un:

```
startx
```

Si així se t'engega l'entorn gràfic amb un:

```
sudo aptitude install gdm
```

t'hauria de tornar tot a la normalitat (excepte que hagis fet més destrosses:))

---

### Post by almogabber on 2008-03-02
Papapep, el teu remei no m¡ha funcionat del tot. HE fet el que has dit, i he instlat el GDM (tot i que fent startx no he pas entrat de nou).
Però un cop instalat el gdm em surt el següent missatge:
```
/etc/gdm/failsafeXServer: line 47: [: too many arguments
WArning: Could not retrieve EDID because get-edit is not installed (1)
FATAL: Error inserting battery (/lib/modules/2.6.20-16-386/kernel/driver
: error: this program does not know how to configure the "10
shared/default-x-server doesen't exist" X server
WArning: Could not generate /etc/X11/xorg.conf.failsafe for vesa driver
```
Clico seguir i:
```
El servidor X està inhabilitat. Reinicieu el GDM quan estigui configurat correctament.
```

Sembla que el que falla és el servidor X. I què és això?? i el més important, com s'habilita i es configura??

gràcies nois!!!

(ara mateix estic fent el que has comentat, menut, de tornar a instalar tot el kde. Sino, provaré el que diu en patrickfromspain)

no sé pas que faria sense vosaltres!!! :KS

---

### Post by patrickfromspain on 2008-03-02
sudo /etc/init.d/gdm restart per resetejar

sudo /etc/init.d/gdm start per iniciar-lo

salut!

---

### Post by almogabber on 2008-03-02
Gràcies nois!! Sembla que ja està.

Finalment, ha funcionat el que ha dit en patrick, de reinstalar el ubuntu-desktop. Tot i que abans ja havia provat les altres maneres que heu propsat..

Ara m'agradaria fer-li una repasada, aviam si tot és on ha d'estar i està configurat de forma satisfactoria. Per si de cas queden fallos 'residuals'.

Com ho hauria de fer? és possible no??

---

### Post by patrickfromspain on 2008-03-02
jo diria que no hi ha res a revisar.. mira si tens insta&#320;lat tot el que necessites i si vols, caba de desinsta&#320;lar el kde (ves amb compte! ;))

Si alguna cosa falla.. ja ho veuras al seu moment. Pero realment hi ha massa fitxers de configuració com per anar mirant un a un.

salut!

---

