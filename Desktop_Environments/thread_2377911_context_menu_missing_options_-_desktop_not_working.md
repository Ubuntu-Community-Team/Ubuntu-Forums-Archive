---
title: "context menu missing options - desktop not working"
date: 2017-11-17
forum: Desktop Environments
---

### Post by t825143 on 2017-11-17
Hi, 
I upgraded from ubuntu 17.04 to ubuntu 17.10
I use "ubuntu on xorg" as default DE
but when my desktop is loaded it is with a limited functionality

issues:
[LIST=1]
[*]I log in and no icons appear on the Desktop (I toggled ON in tweak / desktop icons) but no change 
[*]if i create a "file or folder" from nautilus in ~/Desktop it shows in nautilus Desktop folder but nothing appear on the Desktop itself 
[*]my context menu is missing a lot of options, I do not have the options to create a folder, a file or open with....etc.....(see screenshot below) 
[*]my mouse drag to select files (the shade thingy) does not work at all on the Desktop, if i click the left mouse and drag the mouse.... the select shade does not appear at all but I can select multiple files or folders from within nautilus 
[/LIST]

troubleshoot steps taken:
[LIST=1]
[*]tried to login on all DE available at the login screen _"classic gnome"_, _"ubuntu on xorg"_, _"gnome on xorg"_ all have the same symptoms described above only DE working is _Unity_ 
[*]a standard user that was upgraded with the admin account with issues..the standard account works fine on all DE 
[*]created a new admin user and all DE works fine 
[/LIST]

conclusion
my admin account have a limited functionality related to the Desktop
while other accounts that was upgraded or newly created works fine on all DE



how can I fix the desktop issues of this account ?




screenshot of the context menu available (right click)
[ATTACH=CONFIG]277555[/ATTACH]

---

### Post by goodyone on 2017-11-17
go to settings than to the dock and set up

---

### Post by again? on 2017-11-18
In a terminal run...
```
dconf write /org/gnome/desktop/background/show-desktop-icons true
```
If still not drawing the desktop try logging out and back in. 

No luck, try running...
```
nautilus-desktop
```

---

### Post by t825143 on 2017-11-18
thank you for the response

> **guber2 said:**
> In a terminal run...
```
dconf write /org/gnome/desktop/background/show-desktop-icons true
```
If still not drawing the desktop try logging out and back in. 
this did not solve the issue


> 
No luck, try running...
```
nautilus-desktop
```

tried this from terminal and all icons appeared and missing context menu are available

but I get this multiple times in the terminal window

[B](nautilus-desktop:724): CRITICAL **: nautilus_menu_provider_get_background_items: assertion 'NAUTILUS_IS_MENU_PROVIDER (provider)' failed

[ATTACH=CONFIG]277570[/ATTACH]
[/B]

but when I close the terminal everything go back to what it was



how can I make this permanent  ?

---

### Post by again? on 2017-11-18
Quick solution would be to add a nautilus-desktop entry to startup applications and log out.
[ATTACH=CONFIG]277574[/ATTACH]

If you want to look into it further here's some info.
When "/org/gnome/desktop/background/show-desktop-icons" is set to true, **nautilus-desktop** should autostart in 17.10 due to the 
AutostartCondition set in the file **/etc/xdg/autostart/nautilus-autostart.desktop**

In 17.04 /etc/xdg/autostart/nautilus-autostart.desktop uses **nautilus -n** to draw the desktop.
In 17.10 /etc/xdg/autostart/nautilus-autostart.desktop  uses **nautilus-desktop** to draw the desktop.
Error may have something to do with upgrading.

Compare your file.
```
glen@GU17:~$ cat /etc/xdg/autostart/nautilus-autostart.desktop
[Desktop Entry]
Type=Application
Name[af]=Lêers
Name[an]=Fichers
Name[ar]=&#1575;&#1604;&#1605;&#1604;&#1601;&#1575;&#1578;
Name[as]=&#2475;&#2494;&#2439;&#2482;&#2488;&#2478;&#2498;&#2489;
Name[ast]=Ficheros
Name[be]=&#1060;&#1072;&#1081;&#1083;&#1099;
Name[bg]=&#1060;&#1072;&#1081;&#1083;&#1086;&#1074;&#1077;
Name[bn]=&#2475;&#2494;&#2439;&#2482;
Name[bn_IN]=&#2475;&#2494;&#2439;&#2482;
Name[bs]=Datoteke
Name[ca]=Fitxers
Name[ca@valencia]=Fitxers
Name[crh]=Dosyeler
Name[cs]=Soubory
Name[da]=Filer
Name[de]=Dateien
Name[el]=&#913;&#961;&#967;&#949;&#943;&#945;
Name[en_CA]=Files
Name[en_GB]=Files
Name[eo]=Dosieroj
Name[es]=Archivos
Name[et]=Failid
Name[eu]=Fitxategiak
Name[fa]=&#1662;&#1585;&#1608;&#1606;&#1583;&#1607;*&#1607;&#1575;
Name[fi]=Tiedostot
Name[fr]=Fichiers
Name[fur]=File
Name[ga]=Comhaid
Name[gd]=Faidhlichean
Name[gl]=Ficheiros
Name[gu]=&#2731;&#2750;&#2695;&#2738;&#2763;
Name[he]=&#1511;&#1489;&#1510;&#1497;&#1501;
Name[hi]=&#2347;&#2364;&#2366;&#2311;&#2354;
Name[hr]=Datoteke
Name[hu]=Fájlok
Name[id]=Berkas
Name[is]=Skrár
Name[it]=File
Name[ja]=&#12501;&#12449;&#12452;&#12523;
Name[kk]=&#1060;&#1072;&#1081;&#1083;&#1076;&#1072;&#1088;
Name[kn]=&#3221;&#3233;&#3236;&#3223;&#3251;&#3265;
Name[ko]=&#54028;&#51068;
Name[ky]=&#1060;&#1072;&#1081;&#1083;&#1076;&#1072;&#1088;
Name[ln]=Ba Fisyé
Name[lt]=Failai
Name[lv]=Datnes
Name[mk]=&#1044;&#1072;&#1090;&#1086;&#1090;&#1077;&#1082;&#1080;
Name[ml]=&#3371;&#3375;&#3378;&#3393;&#3349;&#3379;&#3405;*
Name[mr]=&#2347;&#2366;&#2311;&#2354;&#2381;&#2360;&#2381;
Name[ms]=Fail-fail
Name[nb]=Filer
Name[ne]=&#2347;&#2366;&#2311;&#2354;&#2361;&#2352;&#2370;
Name[nl]=Bestanden
Name[nn]=Filer
Name[oc]=Fichièrs
Name[or]=&#2859;&#2878;&#2823;&#2866;&#2839;&#2881;&#2849;&#2879;&#2837;
Name[pa]=&#2603;&#2622;&#2567;&#2610;&#2622;&#2562;
Name[pl]=Pliki
Name[pt]=Ficheiros
Name[pt_BR]=Arquivos
Name[ro]=Fi&#537;iere
Name[ru]=&#1060;&#1072;&#1081;&#1083;&#1099;
Name[sk]=Súbory
Name[sl]=Datoteke
Name[sr]=&#1044;&#1072;&#1090;&#1086;&#1090;&#1077;&#1082;&#1077;
Name[sr@latin]=Datoteke
Name[sv]=Filer
Name[ta]=&#2965;&#3019;&#2986;&#3021;&#2986;&#3009;&#2965;&#2995;&#3021;
Name[te]=&#3110;&#3128;&#3149;&#3108;&#3149;&#3120;&#3134;&#3122;&#3137;
Name[tg]=&#1060;&#1072;&#1081;&#1083;&#1203;&#1086;
Name[th]=&#3649;&#3615;&#3657;&#3617;
Name[tr]=Dosyalar
Name[ug]=&#1726;&#1734;&#1580;&#1580;&#1749;&#1578;&#1604;&#1749;&#1585;
Name[uk]=&#1060;&#1072;&#1081;&#1083;&#1080;
Name[vi]=T&#7853;p tin
Name[zh_CN]=&#25991;&#20214;
Name[zh_HK]=&#27284;&#26696;
Name[zh_TW]=&#27284;&#26696;
Name=Files
Exec=**nautilus-desktop**
OnlyShowIn=GNOME;Unity;
AutostartCondition=GSettings org.gnome.desktop.background show-desktop-icons
NoDisplay=true
```

---

### Post by t825143 on 2017-11-19
yes this what I figured it out too, I put an entry in startup and it worked...just it is not elegant...

looked in [B]/etc/xdg/autostart/nautilus-autostart.desktop
[/B]I have the file nautilus-autostart.desktop
and the content is _exactly_ as the one you inserted (line by line)

but I copied your code and created a new nautilus-autostart.desktop
reboot system..and now it worked...

so strange **.. **nautilus-autostart.desktop is a system wide and works fine for the other users except the upgraded admin account

thanks again..

RESOLVED

---

