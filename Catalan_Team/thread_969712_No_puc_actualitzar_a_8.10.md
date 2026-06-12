---
title: "No puc actualitzar a 8.10"
date: 2008-11-03
forum: Catalan Team
---

### Post by lFossil on 2008-11-03
Molt bones! Altre cop, al anar a actualitzar a una nova versió tinc problemes, engego el gestor d'actualitzacions i em surt 
[això]("http://img142.imageshack.us/my.php?image=capturacb1.png")


i al clicar a actualització parcial em surt [això]("http://img125.imageshack.us/my.php?image=capturaupdatemanagerig1.png")

Què hi puc fer? Gràcies per davant!

---

### Post by PatrickVogeli on 2008-11-03
sudo aptitude dist-upgrade, a veure que pasa

---

### Post by lFossil on 2008-11-05
jasiel@jasiel-laptop:~$ sudo aptitude dist-upgrade
[sudo] password for jasiel: 
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
S'està llegint la informació d'estat estesa       
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
Els paquets següents contenen errors.
  openoffice.org-base openoffice.org-base-core openoffice.org-calc 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-binfilter openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-report-builder-bin openoffice.org-writer python-uno 
  uno-libs3 ure 
Els paquets següents no s'utilitzen i se suprimiran:
  openoffice.org-style-andromeda 
Els paquets nous següents s'instal·laran automàticament:<
  libgmp3c2 libraptor1 librasqal0 librdf0 openoffice.org-emailmerge 
  raptor-utils redland-utils ttf-liberation 
Els paquets nous següents s'instal·laran:
  libgmp3c2 libraptor1 librasqal0 librdf0 openoffice.org-emailmerge 
  raptor-utils redland-utils ttf-liberation 
Els paquets següents s'actualitzaran:
  openoffice.org openoffice.org-common openoffice.org-help-en-gb 
  openoffice.org-help-en-us openoffice.org-help-es openoffice.org-l10n-ca 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za 
  openoffice.org-l10n-es openoffice.org-officebean 
  openoffice.org-style-human openoffice.org-style-industrial 
26 paquets actualitzats, 11 instal·lats, 1 a suprimir i 0 a no actualitzar.
Es necessita obtenir 106MB d'arxius. Després del desempaquetat s'utilitzaran 17,1MB.
No s'han trobat les dependències del paquets següents:
  openoffice.org-gnome: Depén: libstlport4.6ldbl que és un paquet virtual.
  openoffice.org-core: Depén: libdb4.7 que és un paquet virtual.
                       Depén: libgtk2.0-0 (>= 2.14.1) però el 2.12.9-3ubuntu5 està instal·lat.
                       Depén: libhunspell-1.2-0 (>= 1.2.4) que és un paquet virtual.
                       Depén: libhyphen0 (>= 2.4) però no es pot instal·lar.
                       Depén: libneon27 (>= 0.28.2) però el 0.27.2-1 està instal·lat.
                       Depén: libstlport4.6ldbl que és un paquet virtual.
  openoffice.org-writer: Depén: libstlport4.6ldbl que és un paquet virtual.
  openoffice.org-impress: Depén: libstlport4.6ldbl que és un paquet virtual.
  openoffice.org-draw: Depén: libstlport4.6ldbl que és un paquet virtual.
  openoffice.org-filter-binfilter: Depén: libstlport4.6ldbl que és un paquet virtual.
  openoffice.org-java-common: Depén: libsaxonb-java que és un paquet virtual.
  openoffice.org-gtk: Depén: libgtk2.0-0 (>= 2.14.1) però el 2.12.9-3ubuntu5 està instal·lat.
                      Depén: libpango1.0-0 (>= 1.21.6) però el 1.20.5-0ubuntu1 està instal·lat.
                      Depén: libstlport4.6ldbl que és un paquet virtual.
  openoffice.org-report-builder-bin: Depén: libstlport4.6ldbl que és un paquet virtual.
  uno-libs3: Depén: libstlport4.6ldbl que és un paquet virtual.
  openoffice.org-evolution: Depén: libstlport4.6ldbl que és un paquet virtual.
  openoffice.org-math: Depén: libstlport4.6ldbl que és un paquet virtual.
  python-uno: Depén: libstlport4.6ldbl que és un paquet virtual.
  openoffice.org-base-core: Depén: libstlport4.6ldbl que és un paquet virtual.
  ure: Depén: libstlport4.6ldbl que és un paquet virtual.
  openoffice.org-base: Depén: libstlport4.6ldbl que és un paquet virtual.
  openoffice.org-calc: Depén: libstlport4.6ldbl que és un paquet virtual.
                       Depén: lp-solve (>= 5.5.0.10-10) però no es pot instal·lar.
Resolving dependencies...
Les accions següents resoldran les dependències:

Suprimeix els següents paquets:
openoffice.org
openoffice.org-base
openoffice.org-calc
openoffice.org-draw
openoffice.org-evolution
openoffice.org-filter-binfilter
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-impress
openoffice.org-math
openoffice.org-writer

Manté la versió actual dels següents paquets:
openoffice.org-base-core [1:2.4.1-1ubuntu2 (hardy-updates, now)]
openoffice.org-core [1:2.4.1-1ubuntu2 (hardy-updates, now)]
openoffice.org-help-en-gb [1:2.4.1-1ubuntu2 (hardy-updates, now)]
openoffice.org-help-en-us [1:2.4.1-1ubuntu2 (hardy-updates, now)]
openoffice.org-help-es [1:2.4.1-1ubuntu2 (hardy-updates, now)]
openoffice.org-java-common [1:2.4.1-1ubuntu2 (hardy-updates, now)]
openoffice.org-l10n-ca [1:2.4.1-1ubuntu2 (hardy-updates, now)]
openoffice.org-l10n-en-gb [1:2.4.1-1ubuntu2 (hardy-updates, now)]
openoffice.org-l10n-en-za [1:2.4.1-1ubuntu2 (hardy-updates, now)]
openoffice.org-l10n-es [1:2.4.1-1ubuntu2 (hardy-updates, now)]
openoffice.org-officebean [1:2.4.1-1ubuntu2 (hardy-updates, now)]
openoffice.org-report-builder-bin [No instal·lat]
python-uno [1:2.4.1-1ubuntu2 (hardy-updates, now)]
uno-libs3 [No instal·lat]
ure [No instal·lat]

La puntuació és 1076

Accepteu la solució? [Y/n/q/?] y
Avís: s'instal·laran versions no fiables dels paquets següents!

Els paquets no fiables podrien comprometre la seguretat del vostre sistema.
Únicament hauríeu de continuar la instal·lació si n'esteu completament segur.

  openoffice.org-style-industrial openoffice.org-style-human 
  openoffice.org-common 

Voleu ignorar l'avís i continuar?
Per continuar introduïu "Sí"; per abortar introduïu "No": si
No es reconeix l'entrada. Introduïu "Sí" o "No".
Voleu ignorar l'avís i continuar?
Per continuar introduïu "Sí"; per abortar introduïu "No": sí
Els paquets següents no s'utilitzen i se suprimiran:
  libwpg-0.1-1 openoffice.org-filter-mobiledev openoffice.org-officebean 
  openoffice.org-style-andromeda 
Els paquets següents s'han apartat automàticament:
  openoffice.org-base-core openoffice.org-help-es openoffice.org-l10n-es 
Els paquets nous següents s'instal·laran automàticament:<
  ttf-liberation 
Els paquets següents se suprimiran automàticament:
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-binfilter openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-math openoffice.org-writer 
Els paquets següents s'han apartat:
  openoffice.org-core openoffice.org-help-en-gb openoffice.org-help-en-us 
  openoffice.org-java-common openoffice.org-l10n-ca 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za python-uno 
Els paquets nous següents s'instal·laran:
  ttf-liberation 
Els paquets següents se suprimiran:
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-binfilter openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-math openoffice.org-writer 
Els paquets següents s'actualitzaran:
  openoffice.org-common openoffice.org-style-human 
  openoffice.org-style-industrial 
3 paquets actualitzats, 1 instal·lats, 15 a suprimir i 11 a no actualitzar.
Es necessita obtenir 26,8MB d'arxius. Després del desempaquetat s'alliberaran 75,1MB.
Esteu segur de voler continuar? [Y/n/?] y
Avís: s'instal·laran versions no fiables dels paquets següents!

Els paquets no fiables podrien comprometre la seguretat del vostre sistema.
Únicament hauríeu de continuar la instal·lació si n'esteu completament segur.

  openoffice.org-style-industrial openoffice.org-style-human 
  openoffice.org-common 

Voleu ignorar l'avís i continuar?
Per continuar introduïu "Sí"; per abortar introduïu "No": Sí
S'està escrivint la informació d'estat estesa... Fet
Obté:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main openoffice.org-style-industrial 1:3.0.0-2ubuntu1 [3694kB]
Obté:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse ttf-liberation 1.0-0ubuntu1 [1156kB]
Obté:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main openoffice.org-style-human 1:3.0.0-2ubuntu1 [4539kB]
Obté:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main openoffice.org-common 1:3.0.0-2ubuntu1 [17,4MB]
S'han recollit 26,8MB en 2min38s (169kB/s)                                      
(S'està llegint la base de dades ... hi ha 209303 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant openoffice.org ...
S'està desinstal·lant openoffice.org-impress ...
S'està desinstal·lant openoffice.org-draw ...
S'està desinstal·lant libwpg-0.1-1 ...
S'està desinstal·lant openoffice.org-evolution ...
S'està desinstal·lant openoffice.org-base ...
S'està desinstal·lant openoffice.org-calc ...
S'està desinstal·lant openoffice.org-filter-binfilter ...
S'està desinstal·lant openoffice.org-filter-mobiledev ...
S'està desinstal·lant openoffice.org-gnome ...
S'està desinstal·lant openoffice.org-gtk ...
S'està desinstal·lant openoffice.org-math ...
S'està desinstal·lant openoffice.org-officebean ...
S'està desinstal·lant openoffice.org-writer ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(S'està llegint la base de dades ... hi ha 208998 fitxers i directoris instal·lats actualment.)
S'està preparant per a reemplaçar openoffice.org-style-industrial 1:2.4.1-1ubuntu2 (fent servir .../openoffice.org-style-industrial_1%3a3.0.0-2ubuntu1_all.deb) ...
S'està desempaquetant el reemplaçament de openoffice.org-style-industrial ...
S'està preparant per a reemplaçar openoffice.org-style-human 1:2.4.1-1ubuntu2 (fent servir .../openoffice.org-style-human_1%3a3.0.0-2ubuntu1_all.deb) ...
S'està desempaquetant el reemplaçament de openoffice.org-style-human ...
dpkg: openoffice.org-style-andromeda: problemes de dependències, però es desinstal·larà igualment tal i com heu demanat:
 openoffice.org-common depèn de openoffice.org-style-human | openoffice.org-style-tango | openoffice.org-style-crystal | openoffice.org-style-andromeda; tot i així:
  El paquet openoffice.org-style-human encara no està configurat.
  El paquet openoffice.org-style-tango no està instal·lat.
  El paquet openoffice.org-style-crystal no està instal·lat.
  El paquet openoffice.org-style-andromeda serà desinstal·lat.
(S'està llegint la base de dades ... hi ha 209000 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant openoffice.org-style-andromeda ...
(S'està llegint la base de dades ... hi ha 208997 fitxers i directoris instal·lats actualment.)
S'està preparant per a reemplaçar openoffice.org-common 1:2.4.1-1ubuntu2 (fent servir .../openoffice.org-common_1%3a3.0.0-2ubuntu1_all.deb) ...
S'està desempaquetant el reemplaçament de openoffice.org-common ...
S'està seleccionant el paquet ttf-liberation prèviament no seleccionat.
S'està desempaquetant ttf-liberation (de .../ttf-liberation_1.0-0ubuntu1_all.deb) ...
S'està configurant ttf-liberation (1.0-0ubuntu1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-liberation
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for UKaiCN, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.

S'està configurant openoffice.org-style-human (1:3.0.0-2ubuntu1) ...
S'està configurant openoffice.org-common (1:3.0.0-2ubuntu1) ...
S'està instal·lant una versió nova del fitxer de configuració /etc/bash_completion.d/ooffice.sh ...
S'està instal·lant una versió nova del fitxer de configuració /etc/openoffice/sofficerc ...
Updating OpenOffice.org's dictionary list... done.

S'està configurant openoffice.org-style-industrial (1:3.0.0-2ubuntu1) ...
S'està llegint la llista de paquets... Fet           
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
S'està llegint la informació d'estat estesa       
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet 
jasiel@jasiel-laptop:~$

---

### Post by lFossil on 2008-11-05
NOTA IMPORTANT: m'ha desaparegut l'openoffice i he intentat tornar-lo a instal·lar al afegeix/elimina no obstant em diu que no es pot instal·lar perquè es troba en conflicte amb una altra aplicació instal·lada, em diu que l'he de resoldre al gestor de paquets synaptic.
He anat allí i  he desmarcat tot el referent a l'openoffice, però continua igual.
Algú em pot ajudar si us plau es que necessito el processador de textos urgent, moltes gràcies!

---

### Post by SiscoGarcia on 2008-11-05
No sé si pot funcionar, però ja posats, jo provaria a instal·lar l'OpenOffice 3 fent:

```
sudo gedit /etc/apt/sources.list
```

i afegint les següents comandes:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

i tot seguit actualitza els paquets:

```
sudo aptitude update
```

i finalment:

```
sudo aptitude upgrade
```

a veure què.

---

### Post by lFossil on 2008-11-05
Doncs no, el de la sources.list ja ho tenia, de manera que he realitzat els passos següents però no ha passat res, s'han desinstal·lat alguns paquets i poca cosa més. He provat d'instal·lar l'openoffice altre cop al afegeix /elimina però no n'hi ha manera :-k

---

### Post by torracastanyes on 2008-11-05
Em sembla que tens repositoris barrejats.

Jo miraría de deixar només els oficials i ho tornaría a provar.

---

### Post by lFossil on 2008-11-05
Què vols dir?
Que borri això de la sources.list?

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

---

### Post by PatrickVogeli on 2008-11-06
has fet una de les coses que s'aconsella no fer: posar repositoris no oficial i, a més, que no corresponen amb la versió que tens instalada.

Pots tenir problemes per aixo.

salut

---

### Post by lFossil on 2008-11-08
I què hi podria fer per solucionar això?
Al gestor d'actualitzacions encara no em surt el 8.10

---

### Post by torracastanyes on 2008-11-08
Si ja has fet neteja dels repositoris, vés a   Sistema->administració->synaptic->paràmetres->dipòsits   i a la pestanya "actualitzacions" busca "actualització de la versió"(és a baix de tot), selecciona "versions normals" i ja et demanarà si vols actualitzar.

---

