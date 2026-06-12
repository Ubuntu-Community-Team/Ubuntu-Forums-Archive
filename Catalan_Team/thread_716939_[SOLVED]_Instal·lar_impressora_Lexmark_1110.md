---
title: "[SOLVED] Instal·lar impressora Lexmark 1110"
date: 2008-03-06
forum: Catalan Team
---

### Post by prostata on 2008-03-06
Seguint les explicacions que donen a per instalar una lexmark 1110 [http://www.ubuntu-es.org/index.php?q=node/18296](http://www.ubuntu-es.org/index.php?q=node/18296)

finalment no aconsegueix-ho la fita, em permeto adjuntar-vo les respostes de la konsola, per si algú em pot donar un cop de má.

gràcies.


josep@josep-desktop:~$ cd lexmark
josep@josep-desktop:~/lexmark$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
COPYING
README
z600cups-1.0-1.gz.sh
josep@josep-desktop:~/lexmark$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
josep@josep-desktop:~/lexmark$ tar -xvzf install.tar.gz
globals.tcl
install
lexinstall
lexinstall.tcl
license
setup.tcl
testpage
usb.tcl
xlexinstall
xlexinstall.tcl
z600cups-1.0-1.i386.rpm
z600llpddk-2.0-1.i386.rpm
josep@josep-desktop:~/lexmark$ alien -t z600cups-1.0-1.i386.rpm
Warning: alien is not running as root!
Warning: Ownerships of files in the generated packages will probably be wrong.
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
z600cups-1.0.tgz generated
josep@josep-desktop:~/lexmark$ alien -t z600llpddk-2.0-1.i386.rpm
Warning: alien is not running as root!
Warning: Ownerships of files in the generated packages will probably be wrong.
Warning: Skipping conversion of scripts in package z600llpddk: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
z600llpddk-2.0.tgz generated
josep@josep-desktop:~/lexmark$ sudo tar xvzf z600llpddk-2.0.tgz -C /
./
./usr/
./usr/lib/
./usr/lib/liblexz600core.so.0.0.0
./usr/lib/liblexprintjob.la
./usr/lib/liblexprinter.so.0.0.0
./usr/lib/liblexprintjob.a
./usr/lib/liblexz600core.a
./usr/lib/liblexprinter.a
./usr/lib/liblexz600core.la
./usr/lib/liblexprinter.la
./usr/lib/liblexprintjob.so.0.0.0
./usr/local/
./usr/local/z600llpddk/
./usr/local/z600llpddk/utility/
./usr/local/z600llpddk/utility/bnsi1.lut
./usr/local/z600llpddk/utility/lxbccln.out
./usr/local/z600llpddk/utility/lxbcalgn.out
./usr/local/z600llpddk/utility/bnsi3.lut
./usr/local/z600llpddk/utility/bnsi2.lut
./usr/include/
./usr/include/lexmark/
./usr/include/lexmark/cartridgeuserinterface.h
./usr/include/lexmark/cartridgemanager.h
./usr/include/lexmark/cleaningdata.h
./usr/include/lexmark/printerdevice.h
./usr/include/lexmark/errorcommunicator.h
./usr/include/lexmark/linuxinkjetprinter.h
./usr/include/lexmark/mediamanager.h
./usr/include/lexmark/clock.h
./usr/include/lexmark/printjobmanager.h
./usr/include/lexmark/portmonitor.h
./usr/include/lexmark/alignmentdata.h
josep@josep-desktop:~/lexmark$ sudo tar xvzf z600cups-1.0.tgz -C /
./
./usr/
./usr/share/
./usr/share/cups/
./usr/share/cups/model/
./usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz
./usr/lib/
./usr/lib/cups/
./usr/lib/cups/filter/
./usr/lib/cups/filter/rastertoz600
./usr/lib/cups/backend/
./usr/lib/cups/backend/z600
josep@josep-desktop:~/lexmark$ sudo ldconfig
josep@josep-desktop:~/lexmark$ cd /usr/share/cups/model
josep@josep-desktop:/usr/share/cups/model$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
josep@josep-desktop:/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart
open: Permission denied
 * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: warning: failed to kill 4614: Operation not permitted
cupsd: Child exited with status 1!
josep@josep-desktop:/usr/share/cups/model$ cd /usr/lib/cups/backend
josep@josep-desktop:/usr/lib/cups/backend$ ./z600
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
josep@josep-desktop:/usr/lib/cups/backend$ cd /etc
josep@josep-desktop:/etc$ gedit fstab
josep@josep-desktop:/etc$ sudo nautilus
Initializing gnome-mount extension
josep@josep-desktop:/etc$ sudo mount usbfs
mount: usbfs ya está montado o /proc/bus/usb está ocupado
mount: según mtab, usbfs ya está montado en /proc/bus/usb
josep@josep-desktop:/etc$

---

### Post by papapep on 2008-03-06
Doncs [aquí]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-1110") diu que t'hauria de funcionar sense tants invents, amb el controlador [HPLIP]("http://hpinkjet.sf.net/") que igual [Gutsy ja porta per defecte]("http://packages.ubuntu.com/gutsy/hplip") i no et cal ni instal·lar (no ho sé segur, però).

---

### Post by Miquel Ubuntero on 2008-03-07
Hola comapany.
Pots imprimir una fulla de configuració de l'impressora?
En cas afirmatiu. Moltes impressores a la fulla de configuració hi ha una informació referent al llenguatge d'impressió que fan servir. Sovint emulen les impressores H.P. (que és un standard molt estés)
Veuràs algo semblant a "controller/drive HPLJ4" o "xxxx Canon LBP1200", si fos aixís, ho tendries molt fàcil. Només caldria afegir l'impressora com si fos la que el llistat de configuració esmenta.
Si no saps com imprimir la fulla de configuració, cercau amb google, o be, si no te massas botons, proba d' engegar l'impressora premem qualsevol dels botons. Es questió d'anar provant.
Sort!

---

### Post by prostata on 2008-03-07
> **Miquel Ubuntero said:**
> Hola comapany.
Pots imprimir una fulla de configuració de l'impressora?
En cas afirmatiu. Moltes impressores a la fulla de configuració hi ha una informació referent al llenguatge d'impressió que fan servir. Sovint emulen les impressores H.P. (que és un standard molt estés)
Veuràs algo semblant a "controller/drive HPLJ4" o "xxxx Canon LBP1200", si fos aixís, ho tendries molt fàcil. Només caldria afegir l'impressora com si fos la que el llistat de configuració esmenta.
Si no saps com imprimir la fulla de configuració, cercau amb google, o be, si no te massas botons, proba d' engegar l'impressora premem qualsevol dels botons. Es questió d'anar provant.
Sort!

Bon dia; per començar dir que sempre he instal-lat aquesta impressora amb la mateixa rutina, però és ara que em dona problemes i és això el que em fa anar de cap. Si sempre ho he instal-lat així, perquè ara no tira?? i he repetit la rutina molts cops, amb molta cura, molt poc a popc per tal d'evita errors, pero...:(

D'altre costat: no se com imprimir una fulla de configuració, a google no he trobat res.
Si puc encendre l'impressora, si puc veure la configuració de la mateixa, si puc veure el driver, es dir puc veure tota la informació pero no imprimeix, ho envia al pool d'imprressió i ape!!, per si de cas adjuntu una captura de l'administrador d'impressió, per si aiò us dona més info.
Salutacions i gràcies pel vostre temps

---

### Post by prostata on 2008-03-07
ja ho tina arreglat, ja puc tornar a imprimir, s'ha fet la llum, els fòrums de linux son infinits i més tard o més dora, algú et dona la orientació definitiva.

---

### Post by papapep on 2008-03-07
Molt bé. I quina ha estat la solució?

---

### Post by prostata on 2008-03-08
doncs el problema i la solució son aquí:

./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

PS. és una de les respostes que em donà la konsola quan volia fer la instal-lació, mirat amb deteniment vaig comprendre on era tant el problema com la solució.

gràcies a tots....

---

