---
title: "Desisnstalar completament, si purge no funciona ?"
date: 2008-06-16
forum: Catalan Team
---

### Post by sianeu on 2008-06-16
Segueixo l'aventura amb el Kdenlive, però en un nou post per que en papapep no em renyi :).

Mentre aprenc a fer-lo anar he decidit desinstalar-lo i tornar-lo a instalar per recuperar la configuració inicial. Amb el Sinaptic no ho aconseguia per que guarda les configuracions a part. Després he fet un *apt-get purge* i continuava tenint el mateix problema. He provat amb *sudo aptitude remove --purge kdenlive* i amb *sudo aptitude --purge-unused purge kdenlive *, però tot segueix igual.

Després de un aptitude he buscat fitxers kdenlive i només en he trobat dos a /var/cache/var/apt/archives que son fitxers comprimits que no crec que tinguin res a veure.

El problema amb el Kdenlive, si no heu vist l'altre post, es que no em presenta la finestra d'entrada del programa tal i com ho fa el primer cop que s'instal·la, sino amb tres o cuatre finestres independents.

Per si serveix d'alguna cosa copio aquí el que diu la consola al iniciar el programa:

> sianeu@unicorn:~$ kdenlive
kbuildsycoca running...
kdenlive:  + + YOUR MLT INSTALL WAS FOUND IN: /usr
kdenlive: //  INIT EFFECT SEARCH
kdenlive: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kdenlive: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kdenlive: ---------  close 1b
kdenlive: ---------  close 2b
kdenlive: Mlt inited
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: Creating new document DONE 
kdenlive: ---------  close 3b
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive:  + + CREATING CONSUMER WITH PROFILE: atsc_1080i_60
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive: 
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
kdenlive:  + + CREATING CONSUMER WITH PROFILE: atsc_1080i_60
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive: 
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
kdenlive: / / / / / SAVING RECOVERY FILE



---

### Post by papapep on 2008-06-16
> per que en papapep no em renyi 

Jo???? :-\"

Jo provaria amb un simple:

```
sudo aptitude purge nom_del_paquet
```

Després, verifica que sota /home/elteuusuari no quedi cap directori ocult, o no ocult, que faci referència al programa i, si n'hi ha, esborra'l.

---

### Post by sianeu on 2008-06-16
Al final he trobat la solució gracies al amic orestesmas. Les deinstal·lacions deixaven un fitxer de configuració a  ./kde/share/config/kdenliveui.rc 
Borrat aquest fitxer, tot solucionat.

> Jo provaria amb un simple:

Code:

sudo aptitude purge nom_del_paquet



*sudo aptitude purge nom_del_paquet* es més eficient que *sudo aptitude remove --purge nom_del_paquet* ?

Per que el cercador de fitxers no trobava el fitxer en questiò si en el nom porta kdenlive i tenia indicat buscar els fitxers ocults?

Per un altre cop, hi ha alguna manera lògica d'actuar en aquests casos? 

Salut

---

