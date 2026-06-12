---
title: "Enllaç html no funciona [Era:El gedit apareix quan no toca]"
date: 2008-06-30
forum: Catalan Team
---

### Post by Quepotser on 2008-06-30
Hola a tothom. Tinc un problema, si més no, enutjos. M'explico: quan intento fer servir els enllaços directes des de l'escriptori o activar determinats comtes (no tots) del aMSN em surt en pantalla el corresponent fitxer del **gedit** i d'allà no puc passar ja que si tanco el fitxer torno a ser al principi. Faig servir l'Ubuntu 8.04 i fins ara havia funcionat bastant bé. Això va començar a fer-ho ahir a la tarda. Si algú em podés dir a què es degut aquest comportament anòmal i com sol.lucionar-ho li estaria molt agrait.

---

### Post by LitusMayol on 2008-06-30
> **Quepotser said:**
> Hola a tothom. Tinc un problema, si més no, enutjos. M'explico: quan intento fer servir els enllaços directes des de l'escriptori o activar determinats comtes (no tots) del aMSN em surt en pantalla el corresponent fitxer del **gedit** i d'allà no puc passar ja que si tanco el fitxer torno a ser al principi. Faig servir l'Ubuntu 8.04 i fins ara havia funcionat bastant bé. Això va començar a fer-ho ahir a la tarda. Si algú em podés dir a què es degut aquest comportament anòmal i com sol.lucionar-ho li estaria molt agrait.

Fes una cosa: obre el terminal  (Alt+F2 i "*gnome-terminal*"si Gnome o "*Konsole*" si KDE) i allí tecleja-hi "*aMSN*". 

D'aquesta manera se t'obrirà tot igual, però et quedarà registrat al terminal l'error. Quan t'hagi aparegut tot (vaja, quan se t'hagin obert aquests fitxers amb el **Gedit**)l, aleshores copia aquí el que et surti a la consola.

Així serà més fàcil determinar què passa;)

---

### Post by oriolsbd on 2008-06-30
Hola.

Els accessos directes de l'escriptori tenen permisos d'execució?

Salut!

---

### Post by Quepotser on 2008-06-30
Quina rapidesa! Gracies. Faig tot el proces i l'únic que surt a la terminal és això:
lespedretes@lespedretes:~$ amsn
Per si servis d'alguna cosa t'enganxo el fitxer **gedit**que m'apareix quan intento accedir a la bustia del correo:

<html>
<head>
<noscript>
<meta http-equiv=Refresh content="0; url=http://www.hotmail.com">
</noscript>
</head>

<body onload="document.pform.submit(); ">
<form name="pform" action="https://login.live.com/ppsecure/md5auth.srf?lc=3082" method="POST">

<input type="hidden" name="mode" value="ttl">
<input type="hidden" name="login" value="altair_9">
<input type="hidden" name="username" value="altair_9@hotmail.com">
<input type="hidden" name="sid" value="507">
<input type="hidden" name="kv" value="">
<input type="hidden" name="id" value="2">
<input type="hidden" name="sl" value="19">
<input type="hidden" name="rru" value="/cgi-bin/HoTMaiL">
<input type="hidden" name="ru" value="/cgi-bin/HoTMaiL">
<input type="hidden" name="sru" value="/cgi-bin/HoTMaiL">
<input type="hidden" name="auth" value="9S8oorBAXFT1IRN*h12GOtwqsBitwpU0!*!OMfSQX4Me9On3AOx!2q8P!vj8MHfekCocwN49AKufPHM8HjZMkDmFas*v!NZzPlYdvKe0g!WwxvUv4shyO376RWewtBi6eG">
<input type="hidden" name="creds" value="476f009969be3657a80d1d2ba7e9d95b">
<input type="hidden" name="svc" value="mail">
<input type="hidden" name="js" value="yes">
</form></body>
</html>

La qüestiò és que la cosa aquesta em passa quan intento accedir a la bustia d'_algún_ compte (no de tots) i (sempre) que intento utilitzar qualsevol enllaç directe des de l'escriptori que impliqui una connexió a internet. Perdona per la paparrafada. I gracies altra vegada.

---

### Post by Quepotser on 2008-06-30
oriolsbd  	
Re: El gedit apareix quan no toca
Hola.

Els accessos directes de l'escriptori tenen permisos d'execució?

Salut! 

Fins ahir havien funcionat a les mil meravelles. Ho tornaré a mirar però, no fos que s'haguessin modificat involuntariament.
Doncs, l'únic que diu en quant els permisos es alguna cosa similar a això:
**no s'han pogut determinar els permisos per a "/"**.

---

### Post by lluisanunez on 2008-06-30
Uix. Alguna cosa deus haver tocat perquè no es puguin determinar esl permissos per /
Quan cliques a sobre un script i se t'obre amb el Gedit, és que l'script no està declarat com a executable, i només s'obre per editar-lo.  Clica amb el botó contrari > propietats > permisos i marca'l com a executable.

---

### Post by papapep on 2008-06-30
Bones Quepotser,

Aquests "enllaços" que esmentes no són tals, sinó que són fitxers html que en obrir-se al navegador executen el codi html que tenen dins.

D'amsn no en tinc ni idea, però tal i com t'han comentant, alguna cosa deus haver canviat, ni que sigui inconscientment, per a que abans anéssin i ara no. A Linux de màgia poqueta :-D

Si cliques damunt amb el botó de la dreta del ratolí,  vas a Propietats, i li dius que l'obri amb el Firefox, si fas doble clic al seu damunt, funciona?

PD. Benvingut/da (desconec el teu gènere :-)) al fòrum, quan tinguis una estoneta, passat pels dos fils de capçalera i així sabrem un pic de tu i, de pas, nosaltres t'expliquem també una mica com intentem funcionar.

---

### Post by Quepotser on 2008-07-01
A lluisanunez gràcies: quan clico botò dret> propietats> permisos, m'apareix el missatget: "no s'han pogut determinar els permisos de <</>>" en el cas d'un enllaç que tinc a l'escriptori que em serveix per veure el maquinari, drivers i andomines diverses, suportades per linux. Si vull veure els permisos d'un enllaç que tinc per veure l' Herbario Virtual del Mediterraneo em surt: "no s'han pogut determinar els permisos de <<5322.html>>", i així amb tots els enllaços que tinc per l'escriptori: "no s'han pogut determinar els permisos de <<....>>".

---

### Post by Quepotser on 2008-07-01
A papapep: moltes gràcies. No es manca de cortesia el que no m'hagi presentat degudament, però es que de vegades el temps ens apreta d'allò més.

En quant a obrir amb el Firefox no em dona la oportunitat ja que directament s'en va al **gedit**. Pel que fa al **aMSN** la cosa tan sols passa amb un dels comptes que hi tinc oberts, i tant sols, quan vull accedir a la bustia del correo. Si vull xatejar, cap problema. La veritat es que estic una mica desconcertat, per què si m'ho fes en tots els comptes ho entendria més, en el sentit de que semblaria més normal: falla, doncs falla.

---

### Post by papapep on 2008-07-01
Però has provat a fer el que t'he comentat de dir-li que l'obri amb el Firefox o no? no ho deixes clar.

---

### Post by Quepotser on 2008-07-02
Hola papapep:

Doncs ara sí que m'has enganxat, perquè no se a què et refereixes, o no ho entenc. De totes maneres, et faig una descripció de tot el que faig.

Jo tinc al **Firefox** una sèrie d'adreces (URL s'en diuen?el meu coneixement de la terminologia es més aviat pobre), a **Adreces d'interès)** algunes de les quals les he passat a l'escriptori en forma  d'enllaç directe. Des de fa un parell de dies, quan les intento activar des de l'escriptori em surt el **gedit**. Si jo clico amb el botò dret a sobre la icona d'aquest enllaç i vaig a *Propietats* em surt una finestreta en la qual hi ha unes pestanyes, cinc en total, anomenades:
*Basic,Distintius,Permisos,Notes i Enllaç*, i aquí és on ja sóc perdut perquè no veig per enlloc com fer el que em dius, no veig cap indicació de con fer que obri amb el **Firefox**. Si clico a sobre de la icona que apareix a la finestreta de *Propietats* m'envia a una altra finestra per tal de que seleccioni una icona personalitzada.
Ara bé, si des de **Adreces d'interès**, clico a sobre de la mateixa adreça, cap problema, funciona tot de meravella.
Buf!, no sé si amb això he contestat a la teva pregunta.

---

### Post by papapep on 2008-07-02
Sí :-D

Quan fas clic damunt l'accés directe que dius de l'escriptori amb el botó dret, ves a "Obre amb" i _li has de dir que ho faci amb el Firefox_.
No et funciona correctament, per que l'ordinador no sap què fer amb aquest enllaç, i fa l'opció "per defecte", obrir-lo per editar-lo.
Si tu li dius que l'ha d'obrir amb el navegador, hauria de funcionar bé.

---

### Post by Quepotser on 2008-07-02
Això sí que ès rapidesa! Hola una altra vegada papapep. Em dius:

Sí

Quan fas clic damunt l'accés directe que dius de l'escriptori amb el botó dret, ves a "Obre amb" i li has de dir que ho faci amb el Firefox.
No et funciona correctament, per que l'ordinador no sap què fer amb aquest enllaç, i fa l'opció "per defecte", obrir-lo per editar-lo.
Si tu li dius que l'ha d'obrir amb el navegador, hauria de funcionar bé. 



Bé, en cap moment m'ofereix la possibilitat, ni surt per enlloc el "Obre amb". Quan clico el botó dret a sobre la icona tan sols m'apareix una finestreta en la que es veu un "Obre" a la part de dalt. Si clico allà em porta a un fitxer gedit en blanc anomenat**Document sense desar 1 - gedit**:confused:

---

### Post by papapep on 2008-07-02
Amb el botó de la dreta del ratolí tampoc t'apareix la pestanya "Permisos"?

Potser el que estaria bé saber és com els has "passat a l'escriptori en forma d'enllaç directe", com tu dius, ja que igual el problema ve d'aquí.

---

### Post by Quepotser on 2008-07-02
Sí que m'apareix la pestanya "Permisos", i si la clico em surt allò de: "no s'han pogut determinar els permisos de <<nom-de-l'enllaç>>.

Doncs els he passat arrossegant-los, com sempre. Fins abans d'ahir havien anat de conya.

---

### Post by papapep on 2008-07-02
> Fins abans d'ahir havien anat de conya.

Ho trobo perfecte, però ara no van, oi? doncs alguna cosa ha passat pel mig.

Haurem d'anar pel "hard way" :-)

Fes a un terminal:

```
ls -la /home/el_teu_usuari/Escriptori/nom_de_l'enllaç
```

i enganxa aquí el resultat.

---

### Post by Quepotser on 2008-07-03
Bon dia: doncs el "hard way" ens diu:

lespedretes@lespedretes:~$ ls -la /home/lespedretes/Desktop/Enllaç a linux-drivers.org
ls: no s’ha pogut accedir a /home/lespedretes/Desktop/Enllaç: No such file or directory
ls: no s’ha pogut accedir a a: No such file or directory
ls: no s’ha pogut accedir a linux-drivers.org: No such file or directory
lespedretes@lespedretes:~$

---

### Post by papapep on 2008-07-03
A efectes de poder fer les proves sense passar-nos-hi massa temps, canvia el nom del fitxer a alguna cosa simple en plan "enllaç.org" o similar (sense espais pel mig), i torna a executar la ordre que t'he comentat.

---

### Post by Quepotser on 2008-07-03
Hola papapep. Faig el que em dius i heus ací el resultat:

lespedretes@lespedretes:~$ ls -la /home/lespedretes/Desktop/enllaç.org
ls: no s’ha pogut accedir a /home/lespedretes/Desktop/enllaç.org: No such file or directory
lespedretes@lespedretes:~$

---

### Post by papapep on 2008-07-03
....i si fas:

```
ls -la /home/lespedretes/Desktop/
```

què et surt?

---

### Post by Quepotser on 2008-07-03
Faig:

lespedretes@lespedretes:~$ ls -la /home/lespedretes/Desktop
total 6908
drwxr-xr-x  3 lespedretes lespedretes    4096 2008-07-03 20:47 .
drwxr-xr-x 69 lespedretes lespedretes    4096 2008-07-03 20:56 ..
-rw-r--r--  1 lespedretes lespedretes   34239 2008-06-18 15:44 46 0452646043.pdf
drwxr-xr-x  3 lespedretes lespedretes    4096 2008-07-03 13:48 Antarctica
-rw-r--r--  1 lespedretes lespedretes 5880167 2008-01-05 13:57 fascicle1webtancat.757.pdf
-rw-r--r--  1 lespedretes lespedretes  763471 2008-02-03 20:48 guia-ubuntu-02.pdf
-rw-r--r--  1 lespedretes lespedretes     147 2008-07-03 20:00 linux-drivers.org.desktop
-rw-r--r--  1 lespedretes lespedretes  251269 2008-02-03 19:28 Linux.pdf
-rw-------  1 lespedretes lespedretes   91524 2008-05-09 16:52 ubunturef_cat2.pdf
lespedretes@lespedretes:~$

---

### Post by papapep on 2008-07-03
Bé, anem avançant...

I si fas:

```
less /home/lespedretes/Desktop/linux-drivers.org.desktop
```

què surt?

---

### Post by Quepotser on 2008-07-03
Doncs ho faig i surt:

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=enllaç.org
Type=Link
URL=http://linux-drivers.org/
Icon=gnome-fs-bookmark
Name[ca_AD]=enllaç.org
/home/lespedretes/Desktop/linux-drivers.org.desktop (END)

---

### Post by papapep on 2008-07-03
No tinc ni idea de com t'ha passat, però si crees un fitxer de text de nom, per exemple "Enllaç a linux-drivers" amb el següent contingut a l'escriptori:

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Enllaç a linux-drivers
Type=Link
URL=http://linux-drivers.org/
Icon=gnome-fs-bookmark
```

T'hauria de funcionar perfectament l'enllaç (el nou, no l'antic que hauràs d'esborrar)

RECTIFICO: el fitxer s'hauria de dir "**Enllaç a linux-drivers.desktop**".

---

### Post by Quepotser on 2008-07-04
Bon dia un dia més.

Creo, amb el gedit, una fitxer anomenat "Enllaç a linux-drivers.org" i el deso a l'escriptori. Quan clico a la nova icona m'apareix:

-un document del gedit, que no t'he enganxat aquí per què és llarguíssim.

---

### Post by papapep on 2008-07-04
No has fet pas el que t'he comentat. Torna-t'ho a llegir, si us plau.
Si el resultat és massa llarg per a enganxar-lo, adjunta un fitxer de text amb el contingut amb la icona del clip.

---

### Post by Quepotser on 2008-07-04
Creo un document de text anomenat **Enllaç a linux-drivers.desktop** a l'escriptori. Clico a sobre de la icona que m'apareix a l'escriptori i em surt això (t'ho envio així perquè amb el clip no puc lligar-lo aquí):

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">

<html>

<head>

<title>Linux-drivers.org - Linux Hardware Compatibility Lists &amp; Linux Drivers</title>

<META http-equiv="Content-Type" content="text/html; charset=iso-8859-1">

<META name="verify-v1" content="wFc79Fgrw/MhLkVdIbPFe5leaZXnp6eT8pCjK6LuJis=">

<META name="Description" content="Directory of Resources for Linux Hardware Compatibility Lists and Linux Drivers: Video, Audio, Network, Internet, Printer, Scanner, USB, Notebooks and more">

<META name="Keywords" content="linux, treiber, driver, download, PCI, AGP, ISA, LAN, WAN, wireless, ethernet, bluetooth, network, video, modem, sound, chipset, display, multimedia, graphics, audio, tv, camera, scanner, webcam, printer, module, compatibility, notebook, laptop, hardware, CUPS, SANE, usb">

<META name="Author" content="Christian Hoeller">

<META name="Content-language" content="en">

<META name="Page-topic" content="Computer">

<META name="Page-type" content="Software">

<META name="Audience" content="Alle">

<META name="robots" content="INDEX,FOLLOW">

<LINK href="style/style.css" type="text/css" rel="stylesheet">

<link rel="icon" href="http://www.hoeller.net/favicon.ico" type="image/ico">

</head>

<body bgcolor="#FFFFFF">



<table width="960" border="0" cellpadding="0" cellspacing="0" summary="">

<tr>

<td align="left" bgcolor="#DF0451"><img src="jpgs/left.jpg" alt=""></td>

<td align="center" bgcolor="#DF0451"><a name="oben"><font class="deb">Linux Hardware Compatibility Lists &amp; Linux Drivers</font></a></td>

<td align="right" bgcolor="#DF0451"><img src="jpgs/right.jpg" alt=""></td>

</tr>

</table>



<table width="100%" border="0" cellpadding="0" cellspacing="0" summary="">

<tr>

<td valign="top">



<table width="760" border="0" cellpadding="15" cellspacing="3" summary="">

<tr>

<td width="560">

<ul>

<li>Linux Hardware Compatibility Lists</li>

<li><a href="notebooks.html">Linux &amp; Notebooks, PDAs, Handheld PCs and Mobile Phones</a></li>

<li><a href="multiple.html" target="_self">Multiple Drivers</a></li>

<li><a href="display.html">Graphics, Display, Video, TV &amp; DVD</a></li>

<li><a href="audio.html">Audio / Sound</a></li>

<li><a href="network.html">Network &amp; Internet</a></li>

<li><a href="printer_scanner.html">Printer &amp; Scanner</a></li>

<li><a href="usb_webcams.html">USB Support, Webcams &amp; Digital Cameras</a></li>

<li><a href="misc.html">Miscellaneous</a></li>

</ul>

</td>

<td width="200" align="center">

<a href="http://en.wikipedia.org/wiki/Tux"><img src="jpgs/tux_tr.jpg" alt="[IMG]: Tux - The official Linux Penguin" title="[IMG]: Tux - The official Linux Penguin" border="0"></a>

</td>

</tr>

</table>



<table width="700" border="0" cellpadding="1" cellspacing="0" summary="">

<tr>

<td><font class="small"><i>Linux</i> is a Registered Trademark of <i>Linus Torvalds</i>. All trademarks are property of their respective owners.</font></td>

</tr>

</table>



<table cellpadding="15" border="0" cellspacing="0" width="790" summary="">

<tr>

<td bgcolor="#FFFFFF">

<a href="contact.html" target="_top"><img src="gifs/cont.gif" border="0" alt="[Contact]" title="[Contact]"></a>&nbsp; &nbsp; &nbsp;<a href="about.html" target="_top"><img src="gifs/about.gif" border="0" alt="[About Linux-drivers.org]" title="[About Linux-drivers.org]"></a>&nbsp; &nbsp; &nbsp;<a href="discl/discl.html" target="_top"><img src="gifs/impr.gif" border="0" alt="[Impressum]" title="[Impressum]"></a>&nbsp; &nbsp; &nbsp;<a href="http://www.debian.org/"><img src="gifs/debian.gif" border="0" alt="[Powered by Debian GNU/Linux]" title="[Powered by Debian GNU/Linux]"></a>&nbsp; &nbsp; &nbsp;<a href="http://www.gnu.org/software/emacs/"><img src="gifs/emacs.gif" border="0" alt="[Powered by GNU Emacs]" title="[Powered by GNU Emacs]"></a>&nbsp; &nbsp; &nbsp;<a href="http://validator.w3.org/"><img src="gifs/w3c.gif"  border="0" alt="[Valid HTML 4.01!]" title="[Valid HTML 4.01!]"></a>&nbsp; &nbsp; &nbsp;<a href="http://jigsaw.w3.org/css-validator/"><img src="gifs/vcss.gif" border="0" alt="[Valid CSS!]" title="[Valid CSS!]"></a>

</td>

</tr>

</table>



<table cellpadding="0" cellspacing="0" width="760" summary="">

<tr>

<td bgcolor="#FFFFFF" width="450">

<!-- SiteSearch Google -->

<form method="get" action="http://www.google.com/custom" target="_top">

<table border="0" bgcolor="#ffffff" summary="">

<tr><td nowrap="nowrap" valign="top" align="left" height="32">

<a href="http://www.google.com/">

<img src="http://www.google.com/logos/Logo_25wht.gif" border="0" alt="Google" align="middle"></a>

</td>

<td nowrap="nowrap">

<input type="hidden" name="domains" value="Linux-drivers.org">

<input type="text" name="q" size="31" maxlength="255" value="">

<input type="submit" name="sa" value="Search">

</td>

</tr>

<tr>

<td>&nbsp;</td>

<td nowrap="nowrap">

<table summary="">

<tr>

<td>

<input type="radio" name="sitesearch" value="" checked="checked">

<font size="-1" color="#000000">Web</font>

</td>

<td>

<input type="radio" name="sitesearch" value="Linux-drivers.org">

<font size="-1" color="#000000">Linux-drivers.org</font>

</td>

</tr>

</table>

<input type="hidden" name="client" value="pub-5103916465428295">

<input type="hidden" name="forid" value="1">

<input type="hidden" name="channel" value="0709071175">

<input type="hidden" name="ie" value="ISO-8859-1">

<input type="hidden" name="oe" value="ISO-8859-1">

<input type="hidden" name="flav" value="0000">

<input type="hidden" name="sig" value="rvOK2siTy60Bso86">

<input type="hidden" name="cof" value="GALT:#008000;GL:1;DIV:#336699;VLC:663399;AH:center;BGC:FFFFFF;LBGC:336699;ALC:0000FF;LC:0000FF;T:000000;GFNT:0000FF;GIMP:0000FF;LH:50;LW:382;L:http://www.linux-drivers.org/jpgs/ldorg_logo.jpg;S:http://www.linux-drivers.org;FORID:1">

<input type="hidden" name="hl" value="en">

</td></tr></table>

</form>

<!-- SiteSearch Google -->

</td>

<td width="310"><a href="http://www.linuxbasis.org/index.html"><img src="jpgs/lborg.jpg" width="288" height="46" alt="[Linux Distributions, Howtos, Downloads, Security, News]" title="[Linux Distributions, Howtos, Downloads, Security, News]" border="0"></a></td>

</tr>

</table>



<table cellpadding="0" cellspacing="0" width="760" summary="">

<tr>

<td bgcolor="#FFFFFF" align="right">

<font class="small">(<i>last update</i>: 2008-07-02)</font>

</td>

</tr>

</table>



<table bgcolor="#000000" cellpadding="0" cellspacing="0" width="760" summary="">

<tr>

<td>

<table border="0" cellpadding="3" cellspacing="1" summary="">

<tr>

<td width="100%" bgcolor="#FFFFFF">

<h2><b>Linux Hardware Compatibility Lists</b></h2>



<a

href="http://kmuto.jp/debian/hcl/">Debian GNU/Linux device driver check page</a>&nbsp; - This database verifies the PCI devices at this time (X drivers, ISA, USB, IEEE1394 or any other devices are out of its focus). Paste your result of 'lspci -n' taken from GNU/Linux OS (such as Debian, Knoppix, RedHat, and so on) to the box, then push 'Check' button.<br><br>

<a

href="http://en.opensuse.org/Hardware">openSUSE Hardware Compatibility List</a>&nbsp; - The following pages are used by the openSUSE community to record the compatibility of various hardware and full systems with SUSE Linux. Please share your experience by adding your hardware, especially if you had some issue that you overcame.<br><br>

<a

href="http://club.mandriva.com/xwiki/bin/view/KB/HardwareIndex">Mandriva Knowledge base</a>&nbsp; - offers a Hardware compatibility list and general Linux driver issues, general and special Linux hardware information and driver sites.<br><br>

<a

href="https://hardware.redhat.com/">Red Hat Hardware Catalog</a>&nbsp; - Database containing certified hardware for <i>Red Hat</i> products.<br><br>

<a

href="http://wiki.ubuntuusers.de/Hardwaredatenbank">UbuntuUsers Hardwaredatenbank</a>&nbsp; - Auf dieser Seite soll eine Hardwaredatenbank fuer Ubuntu Linux entstehen. Sie koennen hier unter Ubuntu Linux verwendete (neuere) Hardware hinzufuegen, welche gut laeuft.<br><br>

<a

href="http://www.linuxquestions.org/hcl/">LinuxQuestions.org HCL</a>&nbsp; - This is the Linux Hardware Compatibility List from <i>LinuxQuestions.org</i>.<br><br>

<a

href="http://www.tldp.org/HOWTO/Hardware-HOWTO/">Linux Hardware Compatibility HOWTO</a>&nbsp; -  This document attempts to list most of the hardware known to be either supported or unsupported under Linux.<br><br>

<a

href="http://www.linux.org/vendor/hardware/index.html">Linux Hardware Components</a>&nbsp; - The manufacturers and distributors listed on this site sell hardware and peripherals that are Linux-friendly. If you're looking for drivers or need to know if your hardware is supported, this is a good place to find out.<br><br>

<a

href="http://www.linuxcompatible.org/compatlist3.html">LinuxCompatible.org Compatibility List</a>&nbsp; - This is a user submitted compatibility database for hardware running under GNU/Linux.<br><br>

<a

href="http://www.fsf.org/resources/hw">FSF Hardware Database</a>&nbsp; - Free Software Foundation's listing of hardware that supports free software.<br><br>

<a

href="http://www.linux-hardware.org/hardware/liste2.php">Linux-Hardware.org</a>&nbsp; - Die <i>Linux Hardware Datenbank</i> soll Usern einen Ueberblick verschaffen, welche Hardware von welcher Distribution unterstuezt wird. Sie ist so angelegt, dass sie problemlos fuer alle Distributionen genutzt und von Usern ergaenzt werden kann.<br><br>

<a

href="http://hardware4linux.info/">Hardware4linux.info</a>&nbsp; - is a web site to lookup and report hardware compatibility and incompatibility with Linux distributions. The idea is to collaboratively rate which hardware is working or not working under Linux distributions.<br><br>

<a

href="http://hp-linux.cern.ch/support/centp.php3">Linux Support for HP PC's</a>&nbsp; - This page provides an overview of Linux support for HP PC's and peripeherals. Don't base purchasing decisions on the information provided here. This site's main goal is to provide information for people already owning an HP PC.<br><br>

<a

href="http://www.tuxhardware.de/">Tuxhardware.de</a>&nbsp; - <i>(TU)X-beliebige Hardware.</i> Tuxhardware.de ist ein Online- Shop in Deutschland der Produkte mit LINUX- Eignung anbietet. Hier finden Sie u.a. auch Installationsanleitungen, Tipps &amp; Tricks und Links zu Treibern.<br><br>

<a

href="http://www.linuxprinting.org/printer_list.cgi">Unix printer compatiblity database listing</a>&nbsp; - The <i>LinuxPrinting.org</i> printer database contains a wealth of information about specific printers, along with extensive driver information, basic specifications, and an associated set of configuration tools. You can just go straight to a particular printer, or you can list all printers from a given manufacturer. Looking for a printer to buy? Take a look at: &quot;<a href="http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters">Suggested Printers for Free Software Users</a>&quot;.<br><br>

<a

href="http://gimp-print.sourceforge.net/p_Supported_Printers.php3">Gutenprint Supported Printers</a>&nbsp; - <i>Gutenprint</i>, formerly called <i>Gimp-Print</i>, offers high quality drivers for Canon, Epson, Lexmark, Sony, Olympus, and PCL printers for use with Ghostscript, CUPS, Foomatic, and the Gimp.<br><br>

<a

href="http://www.turboprint.info/printers.html">TurboPrint Supported Printers</a>&nbsp; - This is the list of <i>TurboPrint Supported Printers</i>. It includes almost every Canon, Epson &amp; HP and many Brother printers. <i>TurboPrint</i> makes it possible to use the latest color printers with Linux. It is designed to produce maximum quality photo prints as well as high-speed text documents. Printer set-up and configuration is as simple as on Windows or MacOS. <i>TurboPrint</i> is a high-quality printer driver system for Linux built on existing standards (lpr or CUPS printer spooler, ghostscript interpreter for Postscript) thus achieving easy integration and maximum compatibility with existing applications.<br><br>

<a

href="http://www.turboprint.de/printers.html">Von TurboPrint unterstuetzte Drucker</a>&nbsp; - <i>TurboPrint</i> ermoeglicht den Einsatz moderner Farbdrucker unter Linux. Mit TurboPrint erzielen Sie sowohl die bestmoegliche Druckqualitaet bei fotorealistischen Ausdrucken, als auch eine schnelle Ausgabe von Text-Dokumenten. Drucker-Einrichtung und Konfiguration sind durch grafische Menues genauso einfach wie in MS Windows. <i>TurboPrint</i> unterstuetzt fast alle Canon, Epson &amp; HP und viele Brother Drucker.<br><br>

<a

href="http://www.sane-project.org/sane-supported-devices.html">SANE: Supported Devices</a>&nbsp; - shows if your scanner is supported and if yes, by which backend. If it's not supported, it may at least point to documentation or test programs. The search engine contains information from the latest stable SANE release, the development (&quot;CVS&quot;) version of SANE and from external backends. The database is updated once per day.<br><br>

<a

href="http://www.hamrick.com/vuescan/vuescan.htm#supported">VueScan: Supported Scanners</a>&nbsp; - is a continuously upgraded list of <i>VueScan</i> supported scanners. VueScan supports more than 500 different scanners, and these are organized by vendor name. <i>VueScan</i> is a scanning utility that works with most high- quality flatbed and film scanners to produce scans that have excellent color fidelity and color balance. A free trial version is available.<br><br>

<a

href="http://www.teaser.fr/~hfiguiere/linux/digicam.html">Digital Camera Support for UNIX, Linux and BSD</a>&nbsp; - trys to explain how to find out if your camera may work or not under a UNIX system. This site includes a table summarize for digital cameras, how they are supported under UNIX operating systems.<br><br>

<a

href="http://www.gphoto.org/proj/libgphoto2/support.php">Supported Cameras in gPhoto</a>&nbsp; - On this page, you find a list of the supported camera models of the current release of <a href="http://gphoto.sourceforge.net/">gPhoto</a> (=digital camera software applications for Unix-like systems. gPhoto2 is a free, redistributable, ready to use set of digital camera software applications for Unix-like systems). Support for additional cameras may be in the current libgphoto2 SVN trunk code. They will be added to the next release. If your camera is neither supported in the current release nor in current SVN trunk, it is possible that it is an old camera for which the original gPhoto driver has not been ported yet (mostly due to lack of demand) or it is a new camera for which there is no support at all.<br><br>

<a

href="http://www.lavrsen.dk/twiki/bin/view/PWC/WorkingWebcamsWithPWC">Working Webcams with PWC</a>&nbsp; - This is a web-based collaboration area for the next generation <i>Philips Web Camera Linux Kernel Module</i>. On this page, you find a list of the supported Webcams.<br><br>

<a

href="http://www.alsa-project.org/main/index.php/Matrix:Main">ALSA Soundcard Matrix</a>&nbsp; - <i>ALSA</i> (&quot;Advanced Linux Sound Architecture&quot;) supported audio- cards or chipsets. <i>ALSA</i> provides audio and MIDI functionality to the Linux operating system.<br><br>

<a

href="http://www.opensound.com/osshw.html">OSS Sound Card List</a>&nbsp; - <i>OSS</i> supported audio- cards or chipsets. This list is not 100% complete. There are dozens of sound cards that are based on some standard sound chips (or motherboard chipset) made by vendors like Intel, VIA, Cirrus/Crystal, Analog Devices, Realtek, Yamaha, C'Media, Trident, Sigmatel and many others. Such cards may not be listed in the following list but they are still supported.<br><br>

<a

href="http://www.xfree86.org/4.3.0/Status.html">Driver Status for XFree86 4.3.0</a>&nbsp; - provides information about the status of the driver and hardware support in XFree86 4.3.0 compared with that in XFree86 3.3.6.<br><br>

<a

href="http://www.linuxtv.org/wiki/index.php/Supported_Hardware">LinuxTV - Supported Hardware (ATSC, DVB-C, DVB-S, DVB-T devices)</a>&nbsp; - This page is intended to help the &quot;end user&quot; determine whether the device they own, or one that they are considering purchasing, is supported or not under Linux. Before purchasing a DVB device, you should check whether it is listed as supported within the appropriate section of the wiki.<br><br>

<a

href="http://www.qbik.ch/usb/devices/devices.php">Linux USB Device overview</a>&nbsp; - Audio, Modems, Joysticks, Hub devices, Keyboards, Mouse, Cameras, Mass Storage, Multi- functional devices, Printer, Scanner, UPS, Networking, USB-to-Serial converter, Video, Vendor specific devices that don't fall under a certain category.<br><br>

<a

href="http://www.linux-ide.org/chipsets.html">Linux-IDE.org</a>&nbsp; - Support and information about IDE &amp; RAID- Controller. This page offers a list of companies that have support for ATA-33, ATA-66, ATA-100, ATA-133 chipset, SATA 1.0 and Native &quot;PURE HARDWARE ATA RAID&quot; support in Linux.<br><br>

<a

href="http://wiki.uni-konstanz.de/wiki/bin/view/Wireless/ListeFunkkarten">WLAN Karten/Chipsaetze</a>&nbsp; - bietet einen Ueberblick ueber (fast) alle Wireless Funkkarten sowie eine zusaetzliche <a href="http://wiki.uni-konstanz.de/wiki/bin/view/Wireless/ListeChipsatz">Liste der Chipsaetze</a>.<br><br>

<a

href="http://linux-wless.passys.nl/">Linux wireless LAN support</a>&nbsp; - is an attempt to create a, more or less complete listing of wireless devices with information about the chipset they are based on and whether or not they are supported in Linux.<br><br>

<a

href="http://www.seattlewireless.net/ClientAdapters/802.11g">802.11g Client Adapters</a>&nbsp; - offers a list with 802.11g Client Adapters, their chipsets, available drivers and much more infos.<br><br>

<a

href="http://madwifi.org/wiki/Compatibility">Hardware supported by MadWifi</a>&nbsp; - This page (and its sub-pages) lists hardware that has been reported to be based on one of Atheros' chipsets. Usually these reports also contain comments on whether the device in question is supported by MadWifi.<br><br>

<a 

href="http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/">List for devices known to work with <i>NdisWrapper</i></a>&nbsp; - With <i>NdisWrapper</i>, virtually every miniPCI (builtin), PCI, PCMCIA (Cardbus only) or USB wireless network card works in Linux. Some vendors do not release specifications of the hardware or provide a Linux driver for their wireless network cards. This project implements Windows kernel API and NDIS (Network Driver Interface Specification) API within Linux kernel. A Windows driver for wireless network card is then linked to this implementation so that the driver runs natively, as though it is in Windows, without binary emulation. Although <i>NdisWrapper</i> is intended for wireless network cards, other devices are known to work: e.g., USB to serial port device, ethernet card, home phone network device etc.<br><br>

<a

href="http://www.tuxmobil.org/laptop_manufacturer.html">Laptop Manufacturers - Linux Status</a>&nbsp; - This is an overview of more than 150 laptop and notebook manufacturers and their current Linux support status. Besides Linux also other UniXes are mentioned and some hints about laptops with other CPUs than from Intel are included. The survey will be updated constantly.<br><br>

<a

href="http://www.linux-on-laptops.com/">Linux on Laptops</a>&nbsp; - is an index of information and documentation of interest to those who now use or are considering using Linux on a laptop.<br><br>

<a

href="http://www.tuxmobil.org/pcmcia_linux.html">PCMCIA/CF Card Survey</a>&nbsp; - <i>TuxMobil</i>'s Linux Hardware Compatibility List for PCMCIA/PC-Card/CF-Card and CardBus cards sorted by Manufacturer. You may find as well some tips and tricks to get PCMCIA/CF/CardBus cards to work with your Linux laptop, notebook or PDA.<br><br>

<a

href="http://www.tuxmobil.org/hardware.html">Linux Status of Mobile Hardware</a>&nbsp; - Here are Hardware Compatibility Lists - HCLs for Linux with hardware and accessories used in laptops, notebooks, PDAs, mobile phones. Hardware like internal modems, miniPCI cards, IrDA ports, Bluetooth and wireless connectivity. Also portable scanners and printers, mobile CD and DVD writers and much more is covered.<br><br>

<a

href="http://tuxmobil.org/pda_linux.html">Linux with PDAs and Handheld PCs</a>&nbsp; - You want to use Linux or another UniX with your PDA or handheld computer? Here are links to usage documentation about Linux with different PDAs. You may find documentation about non-Linux PDAs as well as dedicated Linux PDAs (like the Agenda VR3, the SHARP Zaurus and the Samsung Yopy).<br><br>

<a

href="http://tuxmobil.org/phones_linux.html">Linux and Mobile (Cellular, Smart) Phones</a>&nbsp; - You want to use Linux or another UniX with your mobile (cellular) phone? Here are links to usage documentation about Linux with different mobile phones. You may find documentation about non-Linux phones as well as dedicated Linux phones.<br><br>

<a

href="http://www.opensync.org/wiki/DeviceCompatibilityList">OpenSync Device Compatibility Listing</a>&nbsp; - OpenSync is a PIM (Personal Information Management) data synchronization framework that consists of several plug-ins that can be used to connect to different devices and systems. This is a table containing the status of support for various devices.<br><br>

<a

href="http://groups.google.com/group/comp.os.linux.hardware/topics">comp.os.linux.hardware</a>&nbsp; - Description: &quot;Hardware compatibility with the Linux operating system&quot;. Search the Usenet archiv of the Newsgroup <i>comp.os.linux.hardware</i> for helpful information with hardware problems and drivers. And at least if you can not find a solution there in the archiv, I recommend to post your question yourself with your favored <a href="http://www.newsreaders.com/">newsreader</a>.<br><br>

<a

href="http://groups.google.de/group/de.comp.os.unix.linux.hardware/topics?hl=de">de.comp.os.unix.linux.hardware</a>&nbsp; - Diese Usenet/News Gruppe dient der Diskussion von Fragen zur Kompatibilitaet und Einbindung gewisser Hardwarekomponenten in eine Linux-Installation auf den verschiedenen Rechnerplattformen, fuer die Linux verfuegbar ist. Das Usenet ist wohl <b>die</b> Anlaufstelle bei speziellen Fragen zu Hardware mit Linux, wenn in den Weiten des WWW bisher keine Loesung gefunden werden konnte. <a href="http://www.dcoul.de/faq/">FAQ der Gruppen der de.comp.os.unix.linux Hierarchie (dcoul).</a><br><br>



</td>

</tr>

</table>

</td>

</tr>

</table>



<table width="760" border="0" cellpadding="15" cellspacing="1" summary="">

<tr>

<td align="center"><a href="#oben" target="_self"><img src="gifs/pfeil.gif" border="0" alt="[ Up to the" title="[ Up to the"></a> <a href="#oben" target="_self">Menu</a> <a href="#oben" target="_self"><img src="gifs/pfeil.gif" border="0" alt="]" title="]"></a></td>

</tr>

</table>



<table cellpadding="15" cellspacing="0" width="760" summary="">

<tr>

<td bgcolor="#FFFFFF">

<a href="contact.html" target="_top"><img src="gifs/cont.gif" border="0" alt="[Contact]" title="[Contact]"></a>&nbsp; &nbsp; &nbsp;<a href="about.html" target="_top"><img src="gifs/about.gif" border="0" alt="[About Linux-drivers.org]" title="[About Linux-drivers.org]"></a>&nbsp; &nbsp; &nbsp;<a href="discl/discl.html" target="_top"><img src="gifs/impr.gif" border="0" alt="[Impressum]" title="[Impressum]"></a>&nbsp; &nbsp; &nbsp;<a href="http://www.debian.org/"><img src="gifs/debian.gif" border="0" alt="[Powered by Debian GNU/Linux]" title="[Powered by Debian GNU/Linux]"></a>&nbsp; &nbsp; &nbsp;<a href="http://www.gnu.org/software/emacs/"><img src="gifs/emacs.gif" border="0" alt="[Powered by GNU Emacs]" title="[Powered by GNU Emacs]"></a>&nbsp; &nbsp; &nbsp;<a href="http://validator.w3.org/"><img src="gifs/w3c.gif"  border="0" alt="[Valid HTML 4.01!]" title="[Valid HTML 4.01!]"></a>&nbsp; &nbsp; &nbsp;<a href="http://jigsaw.w3.org/css-validator/"><img src="gifs/vcss.gif" border="0" alt="[Valid CSS!]" title="[Valid CSS!]"></a>

</td>

</tr>

</table>



</td>

<td width="200" valign="top">

&nbsp;<br>&nbsp;<br>



<table bgcolor="#000000" cellpadding="0" cellspacing="0" width="160" summary="">

<tr>

<td>

<table border="0" cellpadding="0" cellspacing="1" summary="">

<tr>

<td width="100%" bgcolor="#FFFFFF">

<img src="gifs/1px_w.gif" width="160" height="1" alt="" border="0">



<script type="text/javascript"><!--

google_ad_client = "pub-5103916465428295";

google_ad_width = 160;

google_ad_height = 600;

google_ad_format = "160x600_as";

google_ad_type = "text";

google_ad_channel ="7791912638";

google_color_border = "FFFFFF";

google_color_bg = "FFFFFF";

google_color_link = "0000FF";

google_color_text = "000000";

google_color_url = "0000FF";

//--></script>

<script type="text/javascript"

  src="http://pagead2.googlesyndication.com/pagead/show_ads.js">

</script>



<br>&nbsp;<br>



<script type="text/javascript"><!--

google_ad_client = "pub-5103916465428295";

google_ad_width = 160;

google_ad_height = 600;

google_ad_format = "160x600_as";

google_ad_type = "text";

google_ad_channel ="6528724275";

google_color_border = "FFFFFF";

google_color_bg = "FFFFFF";

google_color_link = "0000FF";

google_color_text = "000000";

google_color_url = "0000FF";

//--></script>

<script type="text/javascript"

  src="http://pagead2.googlesyndication.com/pagead/show_ads.js">

</script>





<br>&nbsp;<br>



<script type="text/javascript"><!--

google_ad_client = "pub-5103916465428295";

google_ad_width = 160;

google_ad_height = 600;

google_ad_format = "160x600_as";

google_ad_type = "text";

google_ad_channel ="5731160308";

google_color_border = "FFFFFF";

google_color_bg = "FFFFFF";

google_color_link = "0000FF";

google_color_text = "000000";

google_color_url = "0000FF";

//--></script>

<script type="text/javascript"

  src="http://pagead2.googlesyndication.com/pagead/show_ads.js">

</script>



<br>&nbsp;<br>



<script type="text/javascript"><!--

google_ad_client = "pub-5103916465428295";

google_ad_width = 160;

google_ad_height = 90;

google_ad_format = "160x90_0ads_al_s";

google_ad_channel = "4122900049";

google_color_border = "FFFFFF";

google_color_bg = "FFFFFF";

google_color_link = "0000FF";

google_color_text = "000000";

google_color_url = "0000FF";

//--></script>

<script type="text/javascript"

  src="http://pagead2.googlesyndication.com/pagead/show_ads.js">

</script>



</td>

</tr>

</table>



</td>

</tr>

</table>



</td>

</tr>

</table>



</body>

</html>

Espero haver-ho fet bé aquesta vegada, si no, es que no te entès.

---

### Post by papapep on 2008-07-04
Si el text que has enganxat a l'anterior post, l'enganxes dins un fitxer de text, el podràs adjuntar al fòrum, que és el que t'explicava jo abans, amb el clip.

Respecte el contingut que has adjuntat, si t'hi fixes bé, és el codi html de la pàgina a la que vols anar, linux-drivers.org.
Com és que es visualitza el codi html de la pàgina en vers de veures la pàgina com cal amb el navegador??? Ni la més remota idea...

Si obres el navegador i hi vas directament, et funciona bé?

Si tornes a crear l'adreça d'interès i l'arrossegues a l'escriptori per a crear l'enllaç (esborra abans els antics), et segueix fallant?

---

### Post by Quepotser on 2008-07-04
Hola papapep. Em preguntes:

Si obres el navegador i hi vas directament, et funciona bé?

-Si perfectament.

Si tornes a crear l'adreça d'interès i l'arrossegues a l'escriptori per a crear l'enllaç (esborra abans els antics), et segueix fallant?.

-Ho he fet diverses vegades i sempre ha fet exactament el mateix: fallar. Podria ser que tinguès alguna cosa a veure amb el MIME? 

En quant a la cosa d'adjuntar el fitxer de texte, no ho he fet perquè la "Manage Attachements" no m'ha deixat fer-ho de cap de les maneres.

---

### Post by Quepotser on 2008-07-06
Bon dia a tothom. Ahir, que disposava d'una mica més de temps, vaig estar fent algunes coses que m'havien passat pel cap i, si més no, vaig aconseguir arreglar l'error que es produia al **amsn**. Ho vaig esmenar fent dues coses (amb lo qual no sé quina és la que va anar bé).
La primera fou instal.lar la novíssima versió 0.97.1 del programa i la segona consistí en esborrar el compte que emdonava problemes i tornar-lo a posar. Oli en un llum, va anar de conya.
Seguint el mateix raonament vaig reinstal.lar el **Nautilus** i el **Ubuntu Desktop** (No vai gosar esborrar-los previament), però la cosa ja no va funcionar. Passaría alguna cosa si esborro aquests programes i els torna a instal.lar?

---

