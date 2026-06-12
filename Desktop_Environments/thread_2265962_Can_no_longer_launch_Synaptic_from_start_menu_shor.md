---
title: "Can no longer launch Synaptic from start menu shortcut"
date: 2015-02-18
forum: Desktop Environments
---

### Post by elpidiovaldez5 on 2015-02-18
Synaptic no longer launches from the menu.  The shorcut properties shows that the command is synaptic-pkexec.

The contents of /usr/share/applications/synaptic.desktop is:

[Desktop Entry]
Name=Synaptic Package Manager
GenericName=Package Manager
Comment=Install, remove and upgrade software packages
Exec=synaptic-pkexec
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;GTK;System;Settings;
NotShowIn=KDE;
X-Ubuntu-Gettext-Domain=synaptic


Strangely thare is another file with apparently the exact same name in the same folder ... how is this possible.  It is much bigger, containing:

[Desktop Entry]
Name=Synaptic Package Manager
Name[ar]=&#1605;&#1583;&#1610;&#1585; &#1575;&#1604;&#1581;&#1586;&#1605; &#1575;&#1604;&#1578;&#1588;&#1575;&#1576;&#1603;&#1610;
Name[be]=&#1050;&#1110;&#1088;&#1072;&#1118;&#1085;&#1110;&#1082; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072;&#1118; Synaptic
Name[be@latin]=Kira&#365;nik pakunka&#365; Synaptic
Name[bg]=&#1052;&#1077;&#1085;&#1080;&#1076;&#1078;&#1098;&#1088; &#1085;&#1072; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080; (Synaptic)
Name[br]=Ardoer pakadoù Synaptic
Name[bs]=Upravnik paketa „Synaptic“
Name[ca]=Gestor de paquets Synaptic
Name[ca@valencia]=Gestor de paquets Synaptic
Name[cs]=Správce balík&#367; Synaptic
Name[da]=Synaptic - pakkehåndtering
Name[de]=Synaptic-Paketverwaltung
Name[el]=&#916;&#953;&#945;&#967;&#949;&#943;&#961;&#953;&#963;&#951; &#960;&#945;&#954;&#941;&#964;&#969;&#957; Synaptic
Name[en_AU]=Synaptic Package Manager
Name[en_GB]=Synaptic Package Manager
Name[eo]=Paka&#309;mastrumilo Sinaptiko
Name[es]=Gestor de paquetes Synaptic
Name[et]=Synaptic paketihaldur
Name[eu]=Synaptic pakete-kudeatzailea
Name[fi]=Synaptic-pakettienhallinta
Name[fr]=Gestionnaire de paquets Synaptic
Name[gl]=Xestor de paquetes Synaptic
Name[he]=&#1502;&#1504;&#1492;&#1500; &#1492;&#1495;&#1489;&#1497;&#1500;&#1493;&#1514; Synaptic
Name[hi]=&#2360;&#2367;&#2344;&#2375;&#2346;&#2381;&#2335;&#2367;&#2325; &#2346;&#2376;&#2325;&#2375;&#2332; &#2346;&#2381;&#2352;&#2348;&#2344;&#2381;&#2343;&#2325;
Name[hu]=Synaptic csomagkezel&#337;
Name[ia]=Administrator de pacchettos Synaptic
Name[id]=Synaptic Manajer Paket
Name[it]=Gestore pacchetti
Name[ja]=Synaptic &#12497;&#12483;&#12465;&#12540;&#12472;&#12510;&#12493;&#12540;&#12472;&#12515;
Name[ko]=&#49884;&#45253;&#54001; &#54056;&#53412;&#51648; &#44288;&#47532;&#51088;
Name[ku]=Rêveberê Pakêtan Synaptic
Name[lt]=Paket&#371; tvarkykl&#279; Synaptic
Name[mk]=&#1052;&#1077;&#1085;&#1072;&#1119;&#1077;&#1088; &#1079;&#1072; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080; - &#1057;&#1080;&#1085;&#1072;&#1087;&#1090;&#1080;&#1082;
Name[ms]=Pengurus Pakej Synaptic
Name[nb]=Synaptic pakkebehandler
Name[nl]=Synaptic pakketbeheer
Name[no]=Synaptic Pakkeadministrasjon
Name[pl]=Synaptic Mened&#380;er Pakietów
Name[pt]=Gestor de Pacotes Synaptic
Name[pt_BR]=Gerenciador de pacotes Synaptic
Name[ro]=Synaptic - administrator de pachete
Name[ru]=&#1052;&#1077;&#1085;&#1077;&#1076;&#1078;&#1077;&#1088; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; Synaptic
Name[sk]=Synaptic - správca balíkov
Name[sl]=Upravljalnik paketov Synaptic
Name[sr]=&#1057;&#1080;&#1085;&#1072;&#1087;&#1090;&#1080;&#1082; — &#1091;&#1087;&#1088;&#1072;&#1074;&#1085;&#1080;&#1082; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072;
Name[sr@Latn]=Upravnik paketa „Synaptic“
Name[sv]=Pakethanteraren Synaptic
Name[te]=&#3128;&#3135;&#3112;&#3134;&#3114;&#3149;&#3103;&#3135;&#3093;&#3149; &#3114;&#3149;&#3119;&#3134;&#3093;&#3143;&#3100;&#3136; &#3112;&#3135;&#3120;&#3149;&#3125;&#3134;&#3129;&#3093;&#3074;
Name[th]=&#3648;&#3588;&#3619;&#3639;&#3656;&#3629;&#3591;&#3617;&#3639;&#3629;&#3592;&#3633;&#3604;&#3585;&#3634;&#3619;&#3649;&#3614;&#3585;&#3648;&#3585;&#3592; Synaptic
Name[tr]=Synaptic Paket Yöneticisi
Name[uk]=&#1052;&#1077;&#1085;&#1077;&#1076;&#1078;&#1077;&#1088; &#1087;&#1072;&#1082;&#1091;&#1085;&#1082;&#1110;&#1074; Synaptic
Name[xh]=UMlawuli woMqulu we-Synaptic
Name[zh_CN]=&#26032;&#31435;&#24471;&#36719;&#20214;&#21253;&#31649;&#29702;&#22120;
Name[zh_HK]=Synaptic &#22871;&#20214;&#31649;&#29702;&#21729;
Name[zh_TW]=Synaptic &#22871;&#20214;&#31649;&#29702;&#31243;&#24335;
GenericName=Package Manager
GenericName[ar]=&#1605;&#1583;&#1610;&#1585; &#1575;&#1604;&#1581;&#1586;&#1605;
GenericName[be]=&#1050;&#1110;&#1088;&#1072;&#1118;&#1085;&#1110;&#1082; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072;&#1084;&#1110;
GenericName[be@latin]=Kira&#365;nik pakunka&#365;
GenericName[bg]=&#1052;&#1077;&#1085;&#1080;&#1076;&#1078;&#1098;&#1088; &#1085;&#1072; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080;
GenericName[br]=Ardoer pakadoù
GenericName[bs]=Upravnik paketa
GenericName[ca]=Gestor de paquets
GenericName[ca@valencia]=Gestor de paquets
GenericName[cs]=Správce balík&#367;
GenericName[da]=Pakkehåndteringsprogram
GenericName[de]=Paketverwaltung
GenericName[el]=&#916;&#953;&#945;&#967;&#949;&#943;&#961;&#953;&#963;&#951; &#960;&#945;&#954;&#941;&#964;&#969;&#957;
GenericName[en_AU]=Package Manager
GenericName[en_GB]=Package Manager
GenericName[eo]=Paka&#309;mastrumilo
GenericName[es]=Gestor de paquetes
GenericName[et]=Paketihaldur
GenericName[eu]=Pakete-kudeatzailea
GenericName[fi]=Pakettienhallinta
GenericName[fr]=Gestionnaire de paquets
GenericName[gl]=Xestor de paquetes
GenericName[he]=&#1502;&#1504;&#1492;&#1500; &#1495;&#1489;&#1497;&#1500;&#1493;&#1514;
GenericName[hi]=&#2346;&#2376;&#2325;&#2375;&#2332; &#2346;&#2381;&#2352;&#2348;&#2344;&#2381;&#2343;&#2325;
GenericName[hu]=Csomagkezel&#337;
GenericName[ia]=Administrator de pacchettos
GenericName[id]=Manajer Paket
GenericName[it]=Gestore pacchetti
GenericName[ja]=&#12497;&#12483;&#12465;&#12540;&#12472;&#12510;&#12493;&#12540;&#12472;&#12515;
GenericName[ko]=&#54056;&#53412;&#51648; &#44288;&#47532;&#51088;
GenericName[ku]=Rêveberê Pakêtan
GenericName[lt]=Paket&#371; tvarkykl&#279;
GenericName[mk]=&#1052;&#1077;&#1085;&#1072;&#1119;&#1077;&#1088; &#1079;&#1072; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080;
GenericName[ms]=Pengurusan Pakej
GenericName[nb]=Pakkebehandler
GenericName[nl]=Pakketbeheer
GenericName[pl]=Mened&#380;er pakietów
GenericName[pt]=Gestor de Pacotes
GenericName[pt_BR]=Gerenciador de pacotes
GenericName[ro]=Administrator de pachete
GenericName[ru]=&#1052;&#1077;&#1085;&#1077;&#1076;&#1078;&#1077;&#1088; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;
GenericName[sk]=Správca balíkov
GenericName[sl]=Upravljalnik paketov
GenericName[sr]=&#1059;&#1087;&#1088;&#1072;&#1074;&#1085;&#1080;&#1082; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072;
GenericName[sr@Latn]=Upravnik paketa
GenericName[sv]=Pakethanterare
GenericName[te]=&#3114;&#3149;&#3119;&#3134;&#3093;&#3143;&#3100;&#3136; &#3112;&#3135;&#3120;&#3149;&#3125;&#3134;&#3129;&#3093;&#3074;
GenericName[th]=&#3648;&#3588;&#3619;&#3639;&#3656;&#3629;&#3591;&#3617;&#3639;&#3629;&#3592;&#3633;&#3604;&#3585;&#3634;&#3619;&#3649;&#3614;&#3585;&#3648;&#3585;&#3592;
GenericName[tr]=Paket Yöneticisi
GenericName[uk]=&#1052;&#1077;&#1085;&#1077;&#1076;&#1078;&#1077;&#1088; &#1087;&#1072;&#1082;&#1091;&#1085;&#1082;&#1110;&#1074;
GenericName[xh]=UMlawuli woMqulu
GenericName[zh_CN]=&#36719;&#20214;&#21253;&#31649;&#29702;&#22120;
GenericName[zh_HK]=&#22871;&#20214;&#31649;&#29702;&#21729;
GenericName[zh_TW]=&#22871;&#20214;&#31649;&#29702;&#31243;&#24335;
Comment=Install, remove and upgrade software packages
Comment[ar]=&#1579;&#1576;&#1617;&#1578;&#1548; &#1571;&#1586;&#1604; &#1608;&#1581;&#1583;&#1617;&#1579; &#1581;&#1586;&#1605; &#1575;&#1604;&#1576;&#1585;&#1575;&#1605;&#1580;
Comment[ast]=Instalar, desaniciar y anovar paquetes de software
Comment[be]=&#1059;&#1089;&#1090;&#1072;&#1083;&#1105;&#1118;&#1074;&#1072;&#1077;, &#1074;&#1099;&#1076;&#1072;&#1083;&#1103;&#1077; &#1110; &#1072;&#1073;&#1085;&#1072;&#1118;&#1083;&#1103;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099;
Comment[be@latin]=Instaluj, vydalaj i aktualizuj prahramnyja pakunki
Comment[bg]=&#1048;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1077;, &#1087;&#1088;&#1077;&#1084;&#1072;&#1093;&#1074;&#1072;&#1085;&#1077; &#1080; &#1072;&#1082;&#1090;&#1091;&#1072;&#1083;&#1080;&#1079;&#1080;&#1088;&#1072;&#1085;&#1077; &#1085;&#1072; &#1089;&#1086;&#1092;&#1090;&#1091;&#1077;&#1088;&#1085;&#1080; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080;
Comment[bn]=&#2488;&#2475;&#2463;&#2451;&#2527;&#2509;&#2479;&#2494;&#2480; &#2474;&#2509;&#2479;&#2494;&#2453;&#2503;&#2460; &#2439;&#2472;&#2488;&#2509;&#2463;&#2482;, &#2437;&#2474;&#2488;&#2494;&#2480;&#2467; &#2447;&#2476;&#2434; &#2438;&#2474;&#2455;&#2509;&#2480;&#2503;&#2465;
Comment[br]=Staliañ, dilemel ha hizivaat pakadoù
Comment[bs]=Instaliraj, ukloni i nadogradi softverske pakete
Comment[ca]=Instal·la, elimina i actualitza paquets de programari
Comment[ca@valencia]=Instal·la, elimina i actualitza paquets de programari
Comment[cs]=Nainstalovat, odstranit a aktualizovat balíky
Comment[da]=Installér, fjern og opgradér softwarepakker
Comment[de]=Software-Pakete installieren, entfernen und aktualisieren
Comment[el]=&#917;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951;, &#945;&#960;&#959;&#956;&#940;&#954;&#961;&#965;&#957;&#963;&#951; &#954;&#945;&#953; &#945;&#957;&#945;&#946;&#940;&#952;&#956;&#953;&#963;&#951; &#960;&#945;&#954;&#941;&#964;&#969;&#957; &#955;&#959;&#947;&#953;&#963;&#956;&#953;&#954;&#959;&#973;
Comment[en_AU]=Install, remove and upgrade software packages
Comment[en_GB]=Install, remove and upgrade software packages
Comment[eo]=Instali, forigi kaj promocii programarajn paka&#309;ojn
Comment[es]=Instalar, desinstalar y actualizar los paquetes de software
Comment[et]=Paigalda, eemalda ja uuenda tarkvarapakette
Comment[eu]=Instalatu, kendu eta bertsio-berritu software-paketeak
Comment[fi]=Asenna, poista ja päivitä ohjelmistopaketteja
Comment[fr]=Installer, désinstaller et mettre à jour les paquets de logiciels
Comment[gl]=Instalar, retirar e anovar os paquetes de software
Comment[he]=&#1492;&#1514;&#1511;&#1504;&#1492;, &#1492;&#1505;&#1512;&#1492; &#1493;&#1513;&#1491;&#1512;&#1493;&#1490; &#1495;&#1489;&#1497;&#1500;&#1493;&#1514; &#1514;&#1499;&#1504;&#1492;.
Comment[hi]=&#2360;&#2377;&#2347;&#2381;&#2335;&#2357;&#2375;&#2351;&#2352; &#2346;&#2376;&#2325;&#2375;&#2332;&#2379;&#2306; &#2325;&#2368; &#2360;&#2381;&#2341;&#2366;&#2346;&#2344;&#2366;, &#2309;&#2342;&#2381;&#2351;&#2340;&#2344; &#2325;&#2352;&#2375;&#2306; &#2351;&#2366; &#2313;&#2344;&#2381;&#2361;&#2375;&#2306; &#2361;&#2335;&#2366;&#2319;&#2306;.
Comment[hu]=Csomagok telepítése, törlése és frissítése
Comment[it]=Installa, rimuove e aggiorna i pacchetti software
Comment[ja]=&#12477;&#12501;&#12488;&#12454;&#12455;&#12450;&#12497;&#12483;&#12465;&#12540;&#12472;&#12398;&#12452;&#12531;&#12473;&#12488;&#12540;&#12523;&#12289;&#21066;&#38500;&#12414;&#12383;&#12399;&#12450;&#12483;&#12503;&#12464;&#12524;&#12540;&#12489;
Comment[ko]=&#49548;&#54532;&#53944;&#50920;&#50612; &#54056;&#53412;&#51648;&#47484; &#49444;&#52824;, &#51648;&#50864;&#44592;, &#50629;&#44536;&#47112;&#51060;&#46300;
Comment[ku]=Pakêtên nivîsbariyê saz bike, jê bibe û bilindbike
Comment[lt]=&#302;diekite, šalinkite ir atnaujinkite program&#371; paketus
Comment[mk]=&#1048;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1112;&#1090;&#1077;, &#1086;&#1090;&#1089;&#1090;&#1088;&#1072;&#1085;&#1077;&#1090;&#1077; &#1080;&#1083;&#1080; &#1085;&#1072;&#1076;&#1075;&#1088;&#1072;&#1076;&#1077;&#1090;&#1077; &#1089;&#1086;&#1092;&#1090;&#1074;&#1077;&#1088;&#1089;&#1082;&#1080; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080;
Comment[ms]=Pasang, buang dan tatar pakej perisian
Comment[nb]=Installer, fjern eller oppgrader programpakker
Comment[nl]=Softwarepakketten installeren, verwijderen en opwaarderen
Comment[no]=Installer, fjern eller oppgrader programvare pakker
Comment[pl]=Instalacja, usuwanie i aktualizacja pakietów z oprogramowaniem
Comment[pt]=Instalar, remover e actualizar pacotes
Comment[pt_BR]=Instalar, remover e atualizar pacotes de software
Comment[ro]=Instaleaz&#259;, dezinstaleaz&#259; &#537;i actualizeaz&#259; pachete de programe
Comment[ru]=&#1059;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1080;&#1090;&#1100;, &#1091;&#1076;&#1072;&#1083;&#1080;&#1090;&#1100; &#1080; &#1086;&#1073;&#1085;&#1086;&#1074;&#1080;&#1090;&#1100; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099;
Comment[sk]=Inštalova&#357;, odstráni&#357; alebo aktualizova&#357; softvérové balíky
Comment[sl]=Namestitev, odstranjevanje in nadgradnja programskih paketov
Comment[sr]=&#1048;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1112;&#1090;&#1077;, &#1091;&#1082;&#1083;&#1086;&#1085;&#1080;&#1090;&#1077; &#1080; &#1085;&#1072;&#1076;&#1086;&#1075;&#1088;&#1072;&#1076;&#1080;&#1090;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1077; &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1072;
Comment[sr@Latn]=Instaliraj, ukloni i nadogradi softverske pakete
Comment[sv]=Installera, ta bort och uppgradera programpaket
Comment[te]=&#3128;&#3134;&#3115;&#3149;&#3103;&#3149;*&#3125;&#3143;&#3120;&#3149; &#3114;&#3149;&#3119;&#3134;&#3093;&#3143;&#3100;&#3136;&#3122;&#3112;&#3137; &#3128;&#3149;&#3109;&#3134;&#3114;&#3135;&#3074;&#3098;&#3074;&#3105;&#3135;, &#3108;&#3146;&#3122;&#3095;&#3135;&#3074;&#3098;&#3074;&#3105;&#3135;, &#3081;&#3112;&#3149;&#3112;&#3108;&#3136;&#3093;&#3120;&#3135;&#3074;&#3098;&#3074;&#3105;&#3135;
Comment[th]=&#3605;&#3636;&#3604;&#3605;&#3633;&#3657;&#3591; &#3606;&#3629;&#3604;&#3606;&#3629;&#3609; &#3649;&#3621;&#3632;&#3611;&#3619;&#3633;&#3610;&#3619;&#3640;&#3656;&#3609;&#3649;&#3614;&#3585;&#3648;&#3585;&#3592;&#3595;&#3629;&#3615;&#3605;&#3660;&#3649;&#3623;&#3619;&#3660;
Comment[tr]=Yaz&#305;l&#305;m paketlerini kur, kald&#305;r veya yükselt
Comment[uk]=&#1042;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1085;&#1103;, &#1074;&#1080;&#1083;&#1091;&#1095;&#1077;&#1085;&#1085;&#1103; &#1090;&#1072; &#1086;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1085;&#1103; &#1087;&#1072;&#1082;&#1091;&#1085;&#1082;&#1110;&#1074; &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1085;&#1086;&#1075;&#1086; &#1079;&#1072;&#1073;&#1077;&#1079;&#1087;&#1077;&#1095;&#1077;&#1085;&#1085;&#1103;
Comment[xh]=Faka, susa uze uphucule imiqulu yesoftware
Comment[zh_CN]=&#23433;&#35013;&#65292;&#21024;&#38500;&#21644;&#21319;&#32423;&#36719;&#20214;&#21253;
Comment[zh_HK]=&#23433;&#35037;&#12289;&#31227;&#38500;&#21450;&#21319;&#32026;&#22871;&#20214;
Comment[zh_TW]=&#23433;&#35037;&#12289;&#31227;&#38500;&#21450;&#21319;&#32026;&#22871;&#20214;
Exec=synaptic
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;System;
X-KDE-SubstituteUID=true
OnlyShowIn=KDE;


The problem ocurred after loading some updates through update manager.  Any help would be appreciated.

---

### Post by CantankRus on 2015-02-18
What happens when you run in the terminal...
```
synaptic-pkexec
```

The other file is **synaptic-kde.desktop** and is installed by synaptic I assume for the kde environment.
You can see the actual file name by dragging and dropping into your text editor.

---

### Post by v3.xx on 2015-02-18
This happen to me on a fresh 12o4 install.  Synaptic-pkexec was broke and I never did find the fix.  So I ended up replacing pkexec with gksudo to solve the problem.
```
#Exec=synaptic-pkexec
Exec=gksudo synaptic
```

---

### Post by CantankRus on 2015-02-18
I think pkexec needs an authentication agent running.
eg in Ubuntu you have **polkit-gnome-authentication-agent-1** running.

---

### Post by elpidiovaldez5 on 2015-02-20
synaptic-pkexec runs properly from a terminal - It says authentication is needed, asks me for my password and then opens synaptic.

You say that the other file is for KDE.  I am running lubuntu.  That would not use the KDE file, would it ?

---

### Post by CantankRus on 2015-02-21
> **elpidiovaldez5 said:**
> synaptic-pkexec runs properly from a terminal - It says authentication is needed, asks me for my password and then opens synaptic.

You say that the other file is for KDE.  I am running lubuntu.  That would not use the KDE file, would it ?
Yes, pkexec will authenticate in terminal but when starting normally from the desktop file via a menu, an authentication agent has to provide a password dialog window.
eg try running in terminal...
```
pkexec --disable-internal-agent /usr/sbin/synaptic
```
I don't know how it all works together but that's what I would be looking at.
I have an up to date 14.04 Lubuntu install and opening synaptic from the menu brings up an authentication window.
Here is a similar thread to your problem..... [**_[COLOR="#B22222"]synaptic menu item not working[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2210892")

The synaptic package installs both **Synaptic Package Manager** files in /usr/share/applications whether you have kde installed or not.
The **synaptic-kde.desktop** won't show up in menus unless you're in a kde session because of the line in the .desktop file...
```
OnlyShowIn=KDE; 
```

---

### Post by elpidiovaldez5 on 2015-11-11
Thanks for that reply.  I now understand a little more about what is going on. Sorry for a very belated reply.  I went abroad for a long time and was not doing any computing.  When I got back I re-installed the OS from scratch and that fixed my problems.

---

