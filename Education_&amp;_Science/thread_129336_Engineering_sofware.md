---
title: "Engineering sofware?"
date: 2006-02-13
forum: Education &amp; Science
---

### Post by racermike1967 on 2006-02-13
Hi,
Does anyone know if there are any CAD software out there that I could install on ubuntu?

---

### Post by Kyral on 2006-02-13
[quote=racermike1967]Hi,
Does anyone know if there are any CAD software out there that I could install on ubuntu?[/quote]

I just searched quickly with apt-cache and the only thing I found was qcad. Sounds like what you are looking for ;D

---

### Post by rubinstein on 2006-02-13
There is a free 2D CAD package named qCAD.
You need to enable the universe repository, then type "sudo apt-get install qcad" to install it.
Website: [http://www.ribbonsoft.com/qcad.html](http://www.ribbonsoft.com/qcad.html)

---

### Post by rubinstein on 2006-02-13
Also, look at [http://pfrostie.freeservers.com/cad-tastrafy/](http://pfrostie.freeservers.com/cad-tastrafy/) for a list of cad programs.
If you need a more professional package, you can download a trial version of varicad at [http://www.varicad.com/](http://www.varicad.com/)

---

### Post by dalani on 2006-02-23
GraphiteOne 3D looks promising. I installed on my Hoary but there are issues with dependencies. Nevertheless, the app uses a features method to defining parts (fillets, chamfers etc..)

Another is BRL-Cad a physics oriented engineering  package for simulation and design. If you try it lemme know how it performs.

I work mostly with autocad professionaly at an architectural firm. I would not mind a GPL CAd app for home. QtCad does not allow remapping  keyboard shortcuts to autocad (THe best way to effiicently use a CAD program-mousing is tooo slooow).

---

### Post by azanutta on 2006-04-10
i've tryed TO download VARICAD for my ubuntu DAPPER, but i'm new on linux.... what version works???? there are many of them
debian
red hat
suse
mandrake....
????
tnk

---

### Post by zad on 2006-04-13
[QUOTE=azanutta]i've tryed TO download VARICAD for my ubuntu DAPPER, but i'm new on linux.... what version works???? there are many of them
debian
red hat
suse
mandrake....
????
tnk[/QUOTE]

The debian one will work for you.

Im looking around for software to do basic top view of roof's trying a few to see which is easiest best to use :D

Zad

---

### Post by jchan on 2006-09-27
Dalani,
Can you show us how to install graphiteone on ubuntu, I try the lastest one, It seems to be installed after I changed the files from rpm to deb and installed. but I cannot run it.
I do know where it was installed and I type graphiteone the terminal responsed no such command.
Can you help?
jchan

---

### Post by Bill Cosby on 2006-11-07
When I try to start graphiteone I get the following error

```
/usr/bin/graphiteone: 19: function: not found
usage : graphiteone [options]
Options:
   --ogl=[yes|no]               Enable/Disable OpenGL display driver (default is no).
   --fsaa-mode=[0..5]           Enable FSAA mode for nVidia graphic cards (experimental!).
   --python=[python executable] The python executable to use (default is python).
   --paths=[path:...]           More entries for PYTHONPATH.
```
Anyone knows what's happening here?

---

