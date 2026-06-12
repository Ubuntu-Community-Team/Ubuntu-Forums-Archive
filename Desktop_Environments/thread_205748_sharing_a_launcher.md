---
title: "sharing a launcher"
date: 2006-06-28
forum: Desktop Environments
---

### Post by asalford on 2006-06-28
thanks in advance for reading this post. :D and I thank the ubuntu community for the help they have provided in the past.

I have created a bash script that I would like to share with all users by default.

I am running:
breezy 5.10 
gnome 2.12.1

I would like to put the launcher on the desktop (preferably) and share this with all users.  
I would entertain putting the launcher on the panel (less prefered)

I am obviously not putting the right search strings in google, because it has yielded little in the way of examples or howto's

would someone post how to do this or a link with an example?

---

### Post by aysiu on 2006-06-28
Put it in /usr/share/applications as a .desktop file.

For example, this is the xsane.desktop file in there: ```
[Desktop Entry]
Encoding=UTF-8
Name=XSane Image Scanner
Name[ru]=&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;&#1072; &#1076;&#1083;&#1103; &#1089;&#1082;&#1072;&#1085;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1103; &#1080;&#1079;&#1086;&#1073;&#1088;&#1072;&#1078;&#1077;&#1085;&#1080;&#1081;
Name[ca]=Programa d'escaneig d'imatges XSane
Name[da]=XSane - Billedskanning
Name[de]=XSane Scanprogramm
Name[es]=Programa de escaneo de imágenes XSane
Name[fr]=Programme d'acquisition d'images XSane
Name[fi]=XSane-kuvanlukuohjelma
Name[fa]=&#1576;&#1585;&#1606;&#1575;&#1605;&#1607; &#1575;&#1587;&#1705;&#1606; &#1578;&#1589;&#1575;&#1608;&#1740;&#1585; XSane
Name[pt]=Programa de digitalização XSane
Name[pt_BR]=Programa de Digitalização XSane
Name[it]=Xsane Programma di acquisizione di immagini
Name[nl]=XSane scannerprogramma
Name[hu]=XSane lapolvasó program
Comment=Scan, copy and fax images
Comment[ru]=&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;&#1072; &#1076;&#1083;&#1103; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099; &#1089;&#1086; &#1089;&#1082;&#1072;&#1085;&#1077;&#1088;&#1086;&#1084;. &#1052;&#1086;&#1078;&#1077;&#1090; &#1073;&#1099;&#1090;&#1100; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1072; &#1074; &#1082;&#1072;&#1095;&#1077;&#1089;&#1090;&#1074;&#1077; &#1082;&#1086;&#1087;&#1080;&#1088;&#1086;&#1074;&#1072;&#1083;&#1100;&#1085;&#1086;&#1075;&#1086; &#1072;&#1087;&#1087;&#1072;&#1088;&#1072;&#1090;&#1072;, &#1092;&#1072;&#1082;&#1089;&#1072;, &#1080; &#1076;&#1088;.
Comment[ca]=Un programa per a treballar amb escànners. Es pot utilitzar com una eina d'escanejat, copiat, OCR i fax.
Comment[de]=Ein Programm, um mit einem Scanner zu arbeiten. Kann zum scannen, kopieren, faxen, oder zur Texterkennung verwendet werden.
Comment[es]=Un programa para trabajar con escáners. Se puede utilizar como una herramienta para escanear, copiar, OCR y fax.
Comment[fr]=Un programme d'acquisition d'images pour votre scanner. Peut également photocopier, faxer ou faire de la reconnaissance de caractères.
Comment[fi]=Ohjelma kuvanlukijoiden käyttöön. Voidaan käyttää kuvanluku-, kopiointi-, tekstintunnistus- ja faksaustarkoituksiin.
Comment[fa]=&#1576;&#1585;&#1606;&#1575;&#1605;&#1607; &#1575;&#1740; &#1705;&#1607; &#1576;&#1575; &#1583;&#1587;&#1578;&#1711;&#1575;&#1607; &#1575;&#1587;&#1705;&#1606;&#1585; &#1588;&#1605;&#1575; &#1705;&#1575;&#1585; &#1605;&#1740;&#1705;&#1606;&#1583;
Comment[pt]=Um programa para trabalhar com o digitalizador. Pode ser usado para digitalizar, copiar, reconhecimento óptico de caracteres, fax.
Comment[pt_BR]=Um programa para trabalhar com o scanner. Pode ser usado para digitalizar, copiar, reconhecimento óptico de caracteres, fax.
Comment[it]=Un programma per lavorare con lo scanner. Può essere usato per acquisire, copiare, fare OCR, fax.
Comment[nl]=Een programma om met de scanner te werken. Kan gebruikt worden voor scannen, kopiëren, OCR en faxen.
Comment[hu]=Lapolvasót kezel&#337; program. Lapolvasó, másoló, fax és OCR eszközként is használható.
Exec=xsane
Icon=xsane
Terminal=false
Type=Application
Categories=GTK;Application;Graphics;RasterGraphics;Scanning;OCR;
StartupNotify=true
X-Ubuntu-Gettext-Domain=xsane
```

---

### Post by asalford on 2006-07-19
Thanks, that is exactly what the doctor ordered.  3x:)

---

