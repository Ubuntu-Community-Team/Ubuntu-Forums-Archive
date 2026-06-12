---
title: "Unity Firefox icon questionmark"
date: 2012-11-07
forum: Desktop Environments
---

### Post by Tryfon on 2012-11-07
When I open firefox by clicking its respective icon on the unity bar another questionmark icon appears as active firefox instead of the one I click, as seen on the screenshot. How can I fix this?

[IMG]http://i48.tinypic.com/wtycg0.png[/IMG]

---

### Post by CaptainLinux on 2012-11-07
What happens if you try to run Firefox in safe mode?

```
firefox -safe-mode
```

---

### Post by Tryfon on 2012-11-07
No difference in safe mode.

---

### Post by hakermania on 2012-11-07
&#934;&#953;&#955;&#945;&#961;&#940;&#954;&#953; &#941;&#967;&#949;&#953;&#962; &#960;&#961;&#972;&#946;&#955;&#951;&#956;&#945;...:)

Please open a terminal and give the following command:
```

gsettings get com.canonical.Unity.Launcher favorites

```
It will output your desktop launchers attached to the unity launcher from top to bottom. Locate the equivalent application://something.desktop for firefox (it should be application://firefox.desktop) and locate this file via the terminal at /usr/share/applications/something.desktop. Do a
```

cat /usr/share/applications/something.desktop

```
and post the output here!

---

### Post by Tryfon on 2012-11-08
Ok, I tried removing firefox and reinstalling but it didn't solve the problem. This is the content of my /usr/share/applications/firefox.desktop file:
> [Desktop Entry]
Version=1.0
Name=Firefox Web Browser
Name[ar]=&#1605;&#1578;&#1589;&#1601;&#1581; &#1575;&#1604;&#1608;&#1616;&#1576; &#1601;&#1614;&#1610;&#1614;&#1585;&#1601;&#1615;&#1603;&#1618;&#1587;
Name[ast]=Restolador web Firefox
Name[bn]=&#2475;&#2494;&#2479;&#2492;&#2494;&#2480;&#2475;&#2453;&#2509;&#2488; &#2451;&#2479;&#2492;&#2503;&#2476; &#2476;&#2509;&#2480;&#2494;&#2441;&#2460;&#2494;&#2480;
Name[ca]=Navegador web Firefox
Name[cs]=Firefox Webový prohlíže&#269;
Name[da]=Firefox - internetbrowser
Name[el]=&#928;&#949;&#961;&#953;&#951;&#947;&#951;&#964;&#942;&#962; Firefox
Name[es]=Navegador web Firefox
Name[et]=Firefoxi veebibrauser
Name[fa]=&#1605;&#1585;&#1608;&#1585;&#1711;&#1585; &#1575;&#1740;&#1606;&#1578;&#1585;&#1606;&#1578;&#1740; Firefox
Name[fi]=Firefox-selain
Name[fr]=Navigateur Web Firefox
Name[gl]=Navegador web Firefox
Name[he]=&#1491;&#1508;&#1491;&#1508;&#1503; &#1492;&#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496; Firefox
Name[hr]=Firefox web preglednik
Name[hu]=Firefox webböngész&#337;
Name[it]=Firefox Browser Web
Name[ja]=Firefox &#12454;&#12455;&#12502;&#12539;&#12502;&#12521;&#12454;&#12470;
Name[ko]=Firefox &#50937; &#48652;&#46972;&#50864;&#51200;
Name[ku]=Geroka torê Firefox
Name[lt]=Firefox interneto naršykl&#279;
Name[nb]=Firefox Nettleser
Name[nl]=Firefox webbrowser
Name[nn]=Firefox Nettlesar
Name[no]=Firefox Nettleser
Name[pl]=Przegl&#261;darka WWW Firefox
Name[pt]=Firefox Navegador Web
Name[pt_BR]=Navegador Web Firefox
Name[ro]=Firefox – Navigator Internet
Name[ru]=&#1042;&#1077;&#1073;-&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088; Firefox
Name[sk]=Firefox - internetový prehliada&#269;
Name[sl]=Firefox spletni brskalnik
Name[sv]=Firefox webbläsare
Name[ug]=Firefox &#1578;&#1608;&#1585;&#1603;&#1734;&#1585;&#1711;&#1736;
Name[uk]=&#1042;&#1077;&#1073;-&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088; Firefox
Name[vi]=Trình duy&#7879;t web Firefox
Name[zh_CN]=Firefox &#32593;&#32476;&#27983;&#35272;&#22120;
Name[zh_TW]=Firefox &#32178;&#36335;&#28687;&#35261;&#22120;
Comment=Browse the World Wide Web
Comment[ar]=&#1578;&#1589;&#1601;&#1581; &#1575;&#1604;&#1588;&#1576;&#1603;&#1577; &#1575;&#1604;&#1593;&#1606;&#1603;&#1576;&#1608;&#1578;&#1610;&#1577; &#1575;&#1604;&#1593;&#1575;&#1604;&#1605;&#1610;&#1577;
Comment[ast]=Restola pela Rede
Comment[bn]=&#2439;&#2472;&#2509;&#2463;&#2494;&#2480;&#2472;&#2503;&#2463; &#2476;&#2509;&#2480;&#2494;&#2441;&#2460; &#2453;&#2480;&#2497;&#2472;
Comment[ca]=Navegueu per la web
Comment[cs]=Prohlížení stránek World Wide Webu
Comment[da]=Surf på internettet
Comment[de]=Im Internet surfen
Comment[el]=&#924;&#960;&#959;&#961;&#949;&#943;&#964;&#949; &#957;&#945; &#960;&#949;&#961;&#953;&#951;&#947;&#951;&#952;&#949;&#943;&#964;&#949; &#963;&#964;&#959; &#948;&#953;&#945;&#948;&#943;&#954;&#964;&#965;&#959; (Web)
Comment[es]=Navegue por la web
Comment[et]=Lehitse veebi
Comment[fa]=&#1589;&#1601;&#1581;&#1575;&#1578; &#1588;&#1576;&#1705;&#1607; &#1580;&#1607;&#1575;&#1606;&#1740; &#1575;&#1740;&#1606;&#1578;&#1585;&#1606;&#1578; &#1585;&#1575; &#1605;&#1585;&#1608;&#1585; &#1606;&#1605;&#1575;&#1740;&#1740;&#1583;
Comment[fi]=Selaa Internetin WWW-sivuja
Comment[fr]=Naviguer sur le Web
Comment[gl]=Navegar pola rede
Comment[he]=&#1490;&#1500;&#1497;&#1513;&#1492; &#1489;&#1512;&#1495;&#1489;&#1497; &#1492;&#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496;
Comment[hr]=Pretražite web
Comment[hu]=A világháló böngészése
Comment[it]=Esplora il web
Comment[ja]=&#12454;&#12455;&#12502;&#12434;&#38322;&#35239;&#12375;&#12414;&#12377;
Comment[ko]=&#50937;&#51012; &#46028;&#50500; &#45796;&#45785;&#45768;&#45796;
Comment[ku]=Li torê bigere
Comment[lt]=Naršykite internete
Comment[nb]=Surf på nettet
Comment[nl]=Verken het internet
Comment[nn]=Surf på nettet
Comment[no]=Surf på nettet
Comment[pl]=Przegl&#261;danie stron WWW 
Comment[pt]=Navegue na Internet
Comment[pt_BR]=Navegue na Internet
Comment[ro]=Naviga&#539;i pe Internet
Comment[ru]=&#1044;&#1086;&#1089;&#1090;&#1091;&#1087; &#1074; &#1048;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;
Comment[sk]=Prehliadanie internetu
Comment[sl]=Brskajte po spletu
Comment[sv]=Surfa på webben
Comment[ug]=&#1583;&#1735;&#1606;&#1610;&#1575;&#1583;&#1609;&#1603;&#1609; &#1578;&#1608;&#1585;&#1576;&#1749;&#1578;&#1604;&#1749;&#1585;&#1606;&#1609; &#1603;&#1734;&#1585;&#1711;&#1609;&#1604;&#1609; &#1576;&#1608;&#1604;&#1609;&#1583;&#1735;
Comment[uk]=&#1055;&#1077;&#1088;&#1077;&#1075;&#1083;&#1103;&#1076; &#1089;&#1090;&#1086;&#1088;&#1110;&#1085;&#1086;&#1082; &#1030;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1091;
Comment[vi]=&#272;&#7875; duy&#7879;t các trang web
Comment[zh_CN]=&#27983;&#35272;&#20114;&#32852;&#32593;
Comment[zh_TW]=&#28687;&#35261;&#32178;&#38555;&#32178;&#36335;
GenericName=Web Browser
GenericName[ar]=&#1605;&#1578;&#1589;&#1601;&#1581; &#1608;&#1576;
GenericName[ast]=Restolador Web
GenericName[bn]=&#2451;&#2479;&#2492;&#2503;&#2476; &#2476;&#2509;&#2480;&#2494;&#2441;&#2460;&#2494;&#2480;
GenericName[ca]=Navegador web
GenericName[cs]=Webový prohlíže&#269;
GenericName[da]=Webbrowser
GenericName[el]=&#928;&#949;&#961;&#953;&#951;&#947;&#951;&#964;&#942;&#962; &#948;&#953;&#945;&#948;&#953;&#954;&#964;&#973;&#959;&#965;
GenericName[es]=Navegador web
GenericName[et]=Veebibrauser
GenericName[fa]=&#1605;&#1585;&#1608;&#1585;&#1711;&#1585; &#1575;&#1740;&#1606;&#1578;&#1585;&#1606;&#1578;&#1740;
GenericName[fi]=WWW-selain
GenericName[fr]=Navigateur Web
GenericName[gl]=Navegador Web
GenericName[he]=&#1491;&#1508;&#1491;&#1508;&#1503; &#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496;
GenericName[hr]=Web preglednik
GenericName[hu]=Webböngész&#337;
GenericName[it]=Browser web
GenericName[ja]=&#12454;&#12455;&#12502;&#12539;&#12502;&#12521;&#12454;&#12470;
GenericName[ko]=&#50937; &#48652;&#46972;&#50864;&#51200;
GenericName[ku]=Geroka torê
GenericName[lt]=Interneto naršykl&#279;
GenericName[nb]=Nettleser
GenericName[nl]=Webbrowser
GenericName[nn]=Nettlesar
GenericName[no]=Nettleser
GenericName[pl]=Przegl&#261;darka WWW
GenericName[pt]=Navegador Web
GenericName[pt_BR]=Navegador Web
GenericName[ro]=Navigator Internet
GenericName[ru]=&#1042;&#1077;&#1073;-&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088;
GenericName[sk]=Internetový prehliada&#269;
GenericName[sl]=Spletni brskalnik
GenericName[sv]=Webbläsare
GenericName[ug]=&#1578;&#1608;&#1585;&#1603;&#1734;&#1585;&#1711;&#1736;
GenericName[uk]=&#1042;&#1077;&#1073;-&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088;
GenericName[vi]=Trình duy&#7879;t Web
GenericName[zh_CN]=&#32593;&#32476;&#27983;&#35272;&#22120;
GenericName[zh_TW]=&#32178;&#36335;&#28687;&#35261;&#22120;
Keywords=Internet;WWW;Browser;Web;Explorer
Keywords[ast]=Internet;WWW;Restolador;Web;Esplorador
Keywords[ca]=Internet;WWW;Navegador;Web;Explorador;Explorer
Keywords[cs]=Internet;WWW;Prohlíže&#269;;Web;Explorer
Keywords[da]=Internet;Internettet;WWW;Browser;Browse;Web;Surf;Nettet
Keywords[de]=Internet;WWW;Browser;Web;Explorer;Webseite;Site;surfen;online;browsen
Keywords[el]=Internet;WWW;Browser;Web;Explorer;&#916;&#953;&#945;&#948;&#943;&#954;&#964;&#965;&#959;;&#928;&#949;&#961;&#953;&#951;&#947;&#951;&#964;&#942;&#962;;Firefox;&#934;&#953;&#961;&#949;&#966;&#959;&#967;;&#921;&#957;&#964;&#949;&#961;&#957;&#949;&#964;
Keywords[es]=Explorador;Internet;WWW
Keywords[fi]=Internet;WWW;Browser;Web;Explorer;selain;Internet-selain;internetselain;verkkoselain;netti;surffaa
Keywords[fr]=Internet;WWW;Browser;Web;Explorer;Fureteur;Surfer;Navigateur
Keywords[he]=&#1491;&#1508;&#1491;&#1508;&#1503;;&#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496;;&#1512;&#1513;&#1514;;&#1488;&#1514;&#1512;&#1497;&#1501;;&#1488;&#1514;&#1512;;&#1508;&#1497;&#1497;&#1512;&#1508;&#1493;&#1511;&#1505;;&#1502;&#1493;&#1494;&#1497;&#1500;&#1492;;
Keywords[hr]=Internet;WWW;preglednik;Web
Keywords[hu]=Internet;WWW;Böngész&#337;;Web;Háló;Net;Explorer
Keywords[it]=Internet;WWW;Browser;Web;Navigatore
Keywords[is]=Internet;WWW;Vafri;Vefur;Netvafri;Flakk
Keywords[ja]=Internet;WWW;Web;&#12452;&#12531;&#12479;&#12540;&#12493;&#12483;&#12488;;&#12502;&#12521;&#12454;&#12470;;&#12454;&#12455;&#12502;;&#12456;&#12463;&#12473;&#12503;&#12525;&#12540;&#12521;
Keywords[nb]=Internett;WWW;Nettleser;Explorer;Web;Browser;Nettside
Keywords[nl]=Internet;WWW;Browser;Web;Explorer;Verkenner;Website;Surfen;Online 
Keywords[pt]=Internet;WWW;Browser;Web;Explorador;Navegador
Keywords[pt_BR]=Internet;WWW;Browser;Web;Explorador;Navegador
Keywords[ru]=Internet;WWW;Browser;Web;Explorer;&#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;;&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088;;&#1074;&#1077;&#1073;;&#1092;&#1072;&#1081;&#1088;&#1092;&#1086;&#1082;&#1089;;&#1086;&#1075;&#1085;&#1077;&#1083;&#1080;&#1089;
Keywords[sk]=Internet;WWW;Prehliada&#269;;Web;Explorer
Keywords[sl]=Internet;WWW;Browser;Web;Explorer;Brskalnik;Splet
Keywords[uk]=Internet;WWW;Browser;Web;Explorer;&#1030;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;;&#1084;&#1077;&#1088;&#1077;&#1078;&#1072;;&#1087;&#1077;&#1088;&#1077;&#1075;&#1083;&#1103;&#1076;&#1072;&#1095;;&#1086;&#1075;&#1083;&#1103;&#1076;&#1072;&#1095;;&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088;;&#1074;&#1077;&#1073;;&#1092;&#1072;&#1081;&#1088;&#1092;&#1086;&#1082;&#1089;;&#1074;&#1086;&#1075;&#1085;&#1077;&#1083;&#1080;&#1089;;&#1087;&#1077;&#1088;&#1077;&#1075;&#1083;&#1103;&#1076;
Keywords[vi]=Internet;WWW;Browser;Web;Explorer;Trình duy&#7879;t;Trang web
Keywords[zh_CN]=Internet;WWW;Browser;Web;Explorer;&#32593;&#39029;;&#27983;&#35272;;&#19978;&#32593;;&#28779;&#29392;;Firefox;ff;&#20114;&#32852;&#32593;;&#32593;&#31449;;
Exec=firefox %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=firefox
Categories=GNOME;GTK;Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;x-scheme-handler/chrome;video/webm;application/x-xpinstall;
StartupNotify=true
Actions=NewWindow;

[Desktop Action NewWindow]
Name=Open a New Window
Name[ast]=Abrir una ventana nueva
Name[bn]=Abrir una ventana nueva
Name[ca]=Obre una finestra nova
Name[cs]=Otev&#345;ít nové okno
Name[da]=Åbn et nyt vindue
Name[de]=Ein neues Fenster öffnen
Name[el]=&#902;&#957;&#959;&#953;&#947;&#956;&#945; &#957;&#941;&#959;&#965; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#959;&#965;
Name[es]=Abrir una ventana nueva
Name[fi]=Avaa uusi ikkuna
Name[fr]=Ouvrir une nouvelle fenêtre
Name[gl]=Abrir unha nova xanela
Name[he]=&#1508;&#1514;&#1497;&#1495;&#1514; &#1495;&#1500;&#1493;&#1503; &#1495;&#1491;&#1513;
Name[hr]=Otvori novi prozor
Name[hu]=Új ablak nyitása
Name[it]=Apri una nuova finestra
Name[ja]=&#26032;&#12375;&#12356;&#12454;&#12451;&#12531;&#12489;&#12454;&#12434;&#38283;&#12367;
Name[ko]=&#49352; &#52285; &#50676;&#44592;
Name[ku]=Paceyeke nû veke
Name[lt]=Atverti nauj&#261; lang&#261;
Name[nb]=Åpne et nytt vindu
Name[nl]=Nieuw venster openen
Name[pt]=Abrir nova janela
Name[pt_BR]=Abrir nova janela
Name[ro]=Deschide o fereastr&#259; nou&#259;
Name[ru]=&#1054;&#1090;&#1082;&#1088;&#1099;&#1090;&#1100; &#1085;&#1086;&#1074;&#1086;&#1077; &#1086;&#1082;&#1085;&#1086;
Name[sk]=Otvori&#357; nové okno
Name[sv]=Öppna ett nytt fönster
Name[ug]=&#1610;&#1744;&#1709;&#1609; &#1603;&#1734;&#1586;&#1606;&#1749;&#1603; &#1574;&#1744;&#1670;&#1609;&#1588;
Name[uk]=&#1042;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080; &#1085;&#1086;&#1074;&#1077; &#1074;&#1110;&#1082;&#1085;&#1086;
Name[vi]=M&#7903; c&#7917;a s&#7893; m&#7899;i
Name[zh_CN]=&#26032;&#24314;&#31383;&#21475;
Name[zh_TW]=&#38283;&#21855;&#26032;&#35222;&#31383;
Exec=firefox -new-window
OnlyShowIn=Unity;

A clue which might be of interest is that when I move the mouse over the question mark icon it displays "Mozilla Build of Firefox".

---

### Post by hakermania on 2012-11-08
Does the 
```

gsettings get com.canonical.Unity.Launcher favorites

```
show the firefox.desktop file?

---

### Post by Tryfon on 2012-11-08
Yes it does.

---

### Post by hakermania on 2012-11-08
If you head to /usr/share/applications with nautilus, does the firefox.desktop file have an icon?

---

### Post by Tryfon on 2012-11-09
Yes, it looks ok.

---

### Post by hakermania on 2012-11-09
What happens if you drag it from there (that looks ok) and drop it to the Unity Launcher?

As far as I know it should lock to the launcher and still look OK. Then you can launch firefox from there.

---

### Post by Tryfon on 2012-11-10
Tried what you suggested. It opens again in a questionmark icon. No change.

---

### Post by Tryfon on 2012-11-10
Problem solved. I locked the questionmark icon on the launchbar, then identified its .desktop file in ./local/share/applications/ and deleted it. Now everything works fine, thanks for the help.

---

### Post by hakermania on 2012-11-10
But you said that its desktop file was the firefox.desktop one itself.

---

### Post by brunojcm on 2013-07-05
I had the some problem, but the cause was different. I opened Firefox using unity dash and then locked it to the launcher, and run the following:

```
brunojcm@familia-desktop:~$ gsettings get com.canonical.Unity.Launcher favorites['nautilus-home.desktop', 'chromium-browser.desktop', 'gcalctool.desktop', 'gedit.desktop', 'gnome-terminal.desktop', 'ubuntuone-installer.desktop', 'remmina.desktop', **'/home/brunojcm/Desktop/firefox.desktop'**]

```

As you can see, and I don't know why, Unity dash was suggesting my desktop icon instead of global firefox.desktop. This desktop icon was working properly, but it seems that it cannot work properly on the launcher.

I did the following to fix:

```
brunojcm@familia-desktop:~$ rm /home/brunojcm/Desktop/firefox.desktop
```

I also re-added Firefox to my launcher.

---

