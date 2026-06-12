---
title: "user .desktop apps  not visible on nautilus"
date: 2018-09-26
forum: Desktop Environments
---

### Post by csynt on 2018-09-26
hi,

I am trying to add wine + dosbox as custom .desktop  apps, using as location the   ~/.local/share/applications , 
but there is no way to find them under the "Select Application" on .exe files.
Is this a "feature" of gnome to ignore them? Am I missing something?

thx in advance.

---

### Post by deadflowr on 2018-09-26
Post the contents of one so we can see what syntax you've used.
Whether or not it needs more or has incorrect context.

---

### Post by csynt on 2018-09-26
Hi,

thanks!

this the wine's one:  (syntax as I found from [Gnome's]("https://developer.gnome.org/integration-guide/stable/desktop-files.html.en") site)

```

[Desktop Entry]
Type=Application
Terminal=false
Icon=wine
Name=wine
Exec=wine
Comment=wine
Name=wine
Comment=wine
Icon=wine

```

---

### Post by deadflowr on 2018-09-27
Looks like you have too much going on. I would start by cutting out all duplicate entries, to at least parse it down.
And ftr, wine has no true desktop app, it's more of like an argument to run programs.
As in there is no such program as wine as an app you would open with a nice graphical interface, but more it's a program which runs another app within it.
Hard to explain. ( or easy to explain, I'm just not feeling it)

Typically if you want to create wine desktop launchers you make them specific to the program that would be run with wine.
So generically one would look something like this
```
Name=some-name-of-whatever-program-to-run
Exec=wine /path/to/program/to/run
Type=Application
Icon=some-Icon-For-Program-to-run

```

*The Exec line may or may not require more options depending on circumstances.
 
Also,
If you are looking for a right click option to run wine programs, (or the ability to run programs with designated extensions [such as .exe or msi or whatever windows extensions there are now]
The desktop file for that still exists on your system, but it is not part of the main usage and buried in the wine docs folder at /usr/share/doc/wine/examples.
What you can do is simply copy the wine.desktop file over to your local/share/applications folder like so
```
cp /usr/share/doc/wine/examples/wine.desktop ~/.local/share/applications
```
That should give you the wine program loader as an option in the select applications menu.

As far as dosbox is concerned I think it runs the same basic idea, where if you want to run dosbox's apps out of the box you need to make the launcher specific to them.
You use the same basic Exec line where as you run it with dosbox and then the path to the app you want it to run.
I guess more buried at the bottom of this page:
[https://www.dosbox.com/wiki/DOSBoxShortcuts]("https://www.dosbox.com/wiki/DOSBoxShortcuts")

Hope it make sense of some kind.

---

### Post by monkeybrain20122 on 2018-09-29
when you install dropbox it automatically creates a .desktop file. Not sure why you need to make one.

As for wine, debian upstream apparently "deactivated" all wine .desktop files [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1711855](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1711855), see last post for explanation and how to re-activate them. Alternatively you can install wine from zorinos ppa [https://launchpad.net/~zorinos/+archive/ubuntu/wine-testing](https://launchpad.net/~zorinos/+archive/ubuntu/wine-testing)

---

### Post by mc4man on 2018-09-29
For .desktop files the Exec= line _must_ end in %<a letter> to become available thru the context menu. Possibles are %U or %u or %F or %f 
Normally there is a space between the end of the Exec= command & the %<a letter> ( but in rare cases no space..
For example, audacious.desktop uses > Exec=audacious %U

A rare case here for foobar2000 - 
> Exec=wine "C:\\Program Files (x86)\\foobar2000\\foobar2000.exe" /play  Z:%f

---

### Post by mc4man on 2018-09-29
The proper .desktop for Wine Windows Program Loader (with translations) is 
```
[Desktop Entry]
Type=Application
Name=Wine Windows Program Loader
Name[ar]=&#1605;&#1606;&#1592;&#1608;&#1605;&#1577; &#1608;&#1575;&#1610;&#1606; &#1604;&#1578;&#1588;&#1594;&#1610;&#1604; &#1576;&#1585;&#1575;&#1605;&#1580; &#1608;&#1606;&#1583;&#1608;&#1586;
Name[cs]=Zavad&#283;&#269; program&#367; pro Wine
Name[de]=Wine Windows-Programmstarter
Name[es]=Wine Cargador de programas de Windows
Name[lt]=Wine Windows program&#371; paleidykl&#279;
Name[nl]=Wine Windows programmalader
Name[sv]=Wine Windows Programstartare
Name[ro]=Wine - Înc&#259;rc&#259;torul de programe Windows
Name[ru]=Wine - &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1095;&#1080;&#1082; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;
Name[uk]=Wine - &#1079;&#1072;&#1074;&#1072;&#1085;&#1090;&#1072;&#1078;&#1091;&#1074;&#1072;&#1095; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;
Name[fr]=Wine - Chargeur de programmes Windows
Name[ca]=Wine - Carregador d'aplicacions del Windows
Name[pt]=Carregador de aplicativos Windows Wine
Name[pt_br]=Carregador de aplicativos Windows Wine
Name[it]=Wine Carica Programmi Windows
Name[da]=Wine, Programstarter til Windows-programmer
Name[nb]=Wine - for kjøring av Windows-programmer
Name[nn]=Wine - for køyring av Windows-program
Name[sr]=Wine - &#1076;&#1080;&#1079;&#1072;&#1095; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1072;
Name[sr@latin]=Wine - diza&#269; Windows programa
Name[hr]=Wine - diza&#269; Windows programa
Name[he]=Wine — &#1502;&#1512;&#1497;&#1509; &#1514;&#1499;&#1504;&#1497;&#1493;&#1514; Windows
Name[ja]=Wine Windows&#12503;&#12525;&#12464;&#12521;&#12512;&#12525;&#12540;&#12480;&#12540;
Exec=wine start /unix %f
MimeType=application/x-ms-dos-executable;application/x-msi;application/x-ms-shortcut;
Icon=wine
NoDisplay=true
StartupNotify=true
```

side note - 
The proper .desktop to run winecfg is this, the .desktop should be named wine-winecfg.desktop
```
[Desktop Entry]
Name=Configure Wine
Name[cs]=Nastavení Wine
Name[sv]=Konfigurera Wine
Name[da]=Konfigurer Wine
Name[de]=Konfiguriere Wine
Name[eu]=Konfiguratu Wine
Name[fi]=Winen asetukset
Name[fr]=Configurer Wine
Name[he]=&#1514;&#1510;&#1493;&#1512;&#1514; Wine
Name[pl]=Konfiguracja Wine
Name[ca]=Configureu el Wine
Name[it]=Configura Wine
Name[lt]=Wine nustatymai
Name[nl]=Wine configureren
Name[hu]=A Wine beállítása
Name[ru]=&#1053;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1072; Wine
Name[el]=&#929;&#973;&#952;&#956;&#953;&#963;&#951; Wine
Name[es]=Configurar Wine
Name[pt]=Configurar o Wine
Name[pt_br]=Configurar o Wine
Comment=Change application-specific and general Wine options
Comment[cs]=Upravit specifická nastavení aplikací a obecné nastavení Wine
Comment[sv]=Ändra programspecifika och allmänna Wine-alternativ
Comment[de]=Ändere Wine Optionen und Applikations-spezifische Einstellungen
Comment[fi]=Muuta yleisiä ja sovelluskohtaisia Winen asetuksia
Comment[pl]=Konfigurowanie ustawie&#324; aplikacji i ogólnych opcji Wine
Comment[ca]=Canvieu la configuració general del Wine i especifiqueu opcions per a programes concrets
Comment[pt_br]=Configurar as opções do Wine e dos programas nele instalados
Comment[es]=Cambia la configuración de Wine en general o de una aplicación específica
Comment[el]=&#913;&#955;&#955;&#945;&#947;&#942; &#947;&#949;&#957;&#953;&#954;&#974;&#957; &#961;&#965;&#952;&#956;&#943;&#963;&#949;&#969;&#957; &#964;&#959;&#965; Wine &#942; &#949;&#960;&#953;&#955;&#959;&#947;&#974;&#957; &#949;&#966;&#945;&#961;&#956;&#959;&#947;&#974;&#957;
Comment[ru]=&#1048;&#1079;&#1084;&#1077;&#1085;&#1077;&#1085;&#1080;&#1077; &#1086;&#1073;&#1097;&#1080;&#1093; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1086;&#1074; Wine &#1080; &#1085;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1072; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1086;&#1074; &#1076;&#1083;&#1103; &#1086;&#1090;&#1076;&#1077;&#1083;&#1100;&#1085;&#1099;&#1093; &#1087;&#1088;&#1080;&#1083;&#1086;&#1078;&#1077;&#1085;&#1080;&#1081;
Comment[hu]=Alkalmazásspecifikus és általános Wine beállítások módosítása
Comment[it]=Cambia le opzioni delle singole applicazioni e quelle generali di Wine
Comment[nl]=Verander instellingen voor specifieke programma's en Wine in het algemeen
Exec=winecfg
Terminal=false
Icon=wine-winecfg
Type=Application
Categories=Wine;
```

---

### Post by csynt on 2018-10-02
many thanks guys!!! 

sorry for my late reply , blame h/ware issues with the desktop :(

---

