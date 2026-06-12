---
title: "Cannot remove an item from the task bar"
date: 2022-03-06
forum: Desktop Environments
---

### Post by oygle on 2022-03-06
This morning when I went to click a task bar item (Claws mail), another icon appeared on the task bar. The icon side is larger. Now I cannot get rid of it.  . A right click gives no options to remove it. See screendump. It's in the bottom left hand corner, the larger icon. I already had an icon for Claws, it is pinned to the task bar, yet this one is not and I cannot remove it.

Here are the contents:

```
$ cat   /home/********/.local/share/plasma_icons/claws-mail.desktop
```

> 
[Desktop Entry]
Version=1.0
Name=Claws Mail
GenericName=E-mail client
GenericName[ca]=Client de correu electrònic
GenericName[cs]=E-mailový klient
GenericName[da]=E-post klient
GenericName[es]=Cliente de correo electrónico
GenericName[fi]=Sähköpostiohjelma
GenericName[fr]=Client de messagerie électronique
GenericName[he]=&#1500;&#1511;&#1493;&#1495; &#1491;&#1493;&#1488;&#1524;&#1500;
GenericName[hu]=Levelez&#337;kliens
GenericName[id]=Pembaca E-mail
GenericName[ja]=E&#12513;&#12540;&#12523;&#12463;&#12521;&#12452;&#12450;&#12531;&#12488;
GenericName[lt]=El. pa&#353;to klientas
GenericName[pl]=Program poczty elektronicznej
GenericName[pt]=Cliente de e-mail
GenericName[ru]=&#1055;&#1086;&#1095;&#1090;&#1086;&#1074;&#1099;&#1081; &#1082;&#1083;&#1080;&#1077;&#1085;&#1090;
GenericName[sk]=Po&#353;tový klient
GenericName[sv]=E-postklient
GenericName[tr]=E-posta istemcisi
Exec=claws-mail %u
Icon=claws-mail
Categories=Network;Email;
Keywords=lightweight;fast;gui;extensible;plugin;pop;pop3;imap;imap4;nntp;news;
Comment=Lightweight and Fast GTK+ based Mail Client
Comment[ca]=Client de correu electrònic ràpid i lleuger basat en GTK+
Comment[cs]=Lehký a rychlý mailový klient zalo&#382;ený na GTK+
Comment[da]=Letvægts og hurtig GTK+ baseret e-post klient
Comment[es]=Cliente de correo rápido y ligero basado en GTK+
Comment[fi]=Kevyt ja nopea GTK+-pohjainen sähköpostiohjelma
Comment[fr]=Client de messagerie électronique, rapide et léger, en GTK+
Comment[he]=&#1500;&#1511;&#1493;&#1495; &#1491;&#1493;&#1488;&#1512; &#1511;&#1500; &#1502;&#1513;&#1511;&#1500; &#1493;&#1502;&#1492;&#1497;&#1512; &#1502;&#1489;&#1493;&#1505;&#1505; +GTK
Comment[hu]=Pehelysúlyú és gyors GTK+ alapú levelez&#337;kliens
Comment[id]=Pembaca e-mail berbasis GTK+ yang cepat dan ringan
Comment[ja]=&#36605;&#37327;&#12391;&#26089;&#12356;GTK+&#12505;&#12540;&#12473;&#12398;E&#12513;&#12540;&#12523;&#12463;&#12521;&#12452;&#12450;&#12531;&#12488;
Comment[lt]=Lengvas ir greitas el. pa&#353;to klientas GTK+ pagrindu
Comment[pl]=Program pocztowy u&#380;ywaj&#261;cy GTK+
Comment[pt]=Cliente de e-mail leve e rápido, baseado em GTK+
Comment[ru]=&#1041;&#1099;&#1089;&#1090;&#1088;&#1099;&#1081; &#1087;&#1086;&#1095;&#1090;&#1086;&#1074;&#1099;&#1081; &#1082;&#1083;&#1080;&#1077;&#1085;&#1090; &#1085;&#1072; &#1073;&#1072;&#1079;&#1077; GTK+
Comment[sk]=Od&#318;ah&#269;ený a rýchly po&#353;tový klient, zalo&#382;ený na GTK+
Comment[sv]=Lättviktig och snabb GTK+-baserad E-postklient
Comment[tr]=GTK+ temelli hafif ve h&#305;zl&#305; bir E-posta &#304;stemcisi
Terminal=false
Type=Application
StartupNotify=true
MimeType=x-scheme-handler/mailto;
X-Info=Claws Mail

Actions=GetMail;ComposeMail;SendFile;

[Desktop Action GetMail]
Exec=claws-mail --receive-all
Name=Get Mail
Name[ca]=Rebre
Name[es]=Recibir
Name[fr]=Relever
Name[he]=&#1492;&#1513;&#1490; &#1491;&#1493;&#1488;&#1512;
Name[pt]=Receber
Name[ru]=&#1055;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; &#1055;&#1086;&#1095;&#1090;&#1091;
Name[tr]=Posta Al

[Desktop Action ComposeMail]
Exec=claws-mail --compose
Name=Email...
Name[ca]=Correu...
Name[es]=Correo...
Name[fr]=Message...
Name[he]=&#1491;&#1493;&#1488;&#1524;&#1500;...
Name[pt]=Mensagem...
Name[ru]=&#1055;&#1080;&#1089;&#1100;&#1084;&#1086;...
Name[tr]=E-posta yaz...

[Desktop Action SendFile]
Exec=claws-mail --compose --attach %f
Name=Send file...
Name[ca]=Enviar arxiu...
Name[es]=Enviar fichero...
Name[fr]=Envoyer fichier...
Name[he]=&#1513;&#1500;&#1495; &#1511;&#1493;&#1489;&#1509;...
Name[pt]=Enviar ficheiro...
Name[ru]=&#1054;&#1090;&#1087;&#1088;&#1072;&#1074;&#1080;&#1090;&#1100; &#1092;&#1072;&#1081;&#1083;...
Name[tr]=Ekli e-posta yaz...


When I right click on it, there is no option to remove/delete it, only

Get Mail
Email
Send file
Properties
Add Widgets
Add Panel
Edit Panel

I tried deleting the file, and a restart produced it again. Tried the "Edit Panel" and nothing showing there to remove it. It does 'work', like if I click it, it goes into Claws, but I already have an icon for Claws that is pinned to the task bar. This one I can't get rid of.

A few solutions mentions GNOME tweaks, etc, but his is KDE, Plasma,etc.

```
$ sudo apt list --installed | grep "gnome"
```

> WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

chrome-gnome-shell/focal,focal,now 10.1-5 all [installed,automatic]
gir1.2-gnomebluetooth-1.0/focal-updates,now 3.34.3-0ubuntu1 amd64 [installed,automatic]
gir1.2-gnomedesktop-3.0/focal-updates,now 3.36.8-0ubuntu1 amd64 [installed,automatic]
gnome-accessibility-themes/focal,focal,now 3.28-1ubuntu1 all [installed,automatic]
gnome-control-center-data/focal-updates,focal-updates,now 1:3.36.5-0ubuntu3 all [installed,automatic]
gnome-control-center-faces/focal-updates,focal-updates,now 1:3.36.5-0ubuntu3 all [installed,automatic]
gnome-control-center/focal-updates,now 1:3.36.5-0ubuntu3 amd64 [installed,automatic]
gnome-desktop3-data/focal-updates,focal-updates,now 3.36.8-0ubuntu1 all [installed,automatic]
gnome-icon-theme/focal,focal,now 3.12.0-3 all [installed,automatic]
gnome-keyring-pkcs11/focal,now 3.36.0-1ubuntu1 amd64 [installed,automatic]
gnome-keyring/focal,now 3.36.0-1ubuntu1 amd64 [installed,automatic]
gnome-menus/focal,now 3.36.0-1ubuntu1 amd64 [installed,automatic]
gnome-online-accounts/focal-updates,now 3.36.1-0ubuntu1 amd64 [installed,automatic]
gnome-session-bin/focal,now 3.36.0-2ubuntu1 amd64 [installed,automatic]
gnome-session-canberra/focal,now 0.30-7ubuntu1 amd64 [installed,automatic]
gnome-session-common/focal,focal,now 3.36.0-2ubuntu1 all [installed,automatic]
gnome-settings-daemon-common/focal-updates,focal-updates,now 3.36.1-0ubuntu1.1 all [installed,automatic]
gnome-settings-daemon/focal-updates,now 3.36.1-0ubuntu1.1 amd64 [installed,automatic]
gnome-shell-common/focal-updates,focal-updates,now 3.36.9-0ubuntu0.20.04.2 all [installed,automatic]
gnome-shell-extension-prefs/focal-updates,now 3.36.9-0ubuntu0.20.04.2 amd64 [installed,automatic]
gnome-shell/focal-updates,now 3.36.9-0ubuntu0.20.04.2 amd64 [installed,automatic]
gnome-software-common/focal-updates,focal-updates,now 3.36.1-0ubuntu0.20.04.0 all [installed,automatic]
gnome-software-plugin-flatpak/focal-updates,now 3.36.1-0ubuntu0.20.04.0 amd64 [installed]
gnome-software/focal-updates,now 3.36.1-0ubuntu0.20.04.0 amd64 [installed,automatic]
gnome-startup-applications/focal,now 3.36.0-2ubuntu1 amd64 [installed,automatic]
gnome-theme-gilouche/focal,focal,now 11.1.2-2 all [installed]
gnome-themes-extra-data/focal,focal,now 3.28-1ubuntu1 all [installed,automatic]
gnome-themes-extra/focal,now 3.28-1ubuntu1 amd64 [installed]
gnome-tweaks/focal,focal,now 3.34.0-2ubuntu1 all [installed]
gnome-user-docs/focal-updates,focal-updates,now 3.36.2+git20200704-0ubuntu0.1 all [installed,automatic]
language-selector-gnome/focal-updates,focal-updates,now 0.204.2 all [installed,automatic]
libgnome-autoar-0-0/focal-updates,focal-security,now 0.2.3-2ubuntu0.4 amd64 [installed,automatic]
libgnome-bluetooth13/focal-updates,now 3.34.3-0ubuntu1 amd64 [installed,automatic]
libgnome-desktop-3-19/focal-updates,now 3.36.8-0ubuntu1 amd64 [installed,automatic]
libgnomecanvas2-0/focal,now 2.30.3-4 amd64 [installed,automatic]
libgnomecanvas2-common/focal,focal,now 2.30.3-4 all [installed,automatic]
libgnomekbd-common/focal,focal,now 3.26.1-1 all [installed,automatic]
libgnomekbd8/focal,now 3.26.1-1 amd64 [installed,automatic]
libpam-gnome-keyring/focal,now 3.36.0-1ubuntu1 amd64 [installed,automatic]
libsoup-gnome2.4-1/focal,now 2.70.0-1 amd64 [installed,automatic]
network-manager-gnome/focal-updates,now 1.8.24-1ubuntu3 amd64 [installed,automatic]
pinentry-gnome3/focal,now 1.1.0-3build1 amd64 [installed,automatic]
yaru-theme-gnome-shell/focal-updates,focal-updates,now 20.04.11.1 all [installed,automatic]


A number of these in file .xsession-errors; not sure if it is related

> file:///usr/share/plasma/plasmoids/org.kde.plasma.taskmanager/contents/ui/main.qml:455: TypeError: Type error
file:///usr/share/plasma/plasmoids/org.kde.plasma.taskmanager/contents/ui/Task.qml:374: Unable to assign [undefined] to QString

---

