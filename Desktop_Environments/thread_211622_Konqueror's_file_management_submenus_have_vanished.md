---
title: "Konqueror's file management submenus have vanished!"
date: 2006-07-08
forum: Desktop Environments
---

### Post by darenw on 2006-07-08
I have been using Konqueror just fine for several days, but at some point yesterday, when using it as a file manager, the right-click menu no longer shows "actions" submenu, and it seems that some others are missing too.  I never did anything deliberate to do this - i rely on "Open xterm here" (or however they word it).   but i have been busy in Synaptic trying lots of software, adding and then removing XFCE and Gnome packages. I suspect somehow that activity clobbered something belonging to Konqueror.   How to go about fixing this?

---

### Post by Jucato on 2006-07-09
Konqueror service menus are located in three places on a Kubuntu system:

/usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror/servicemenus
/usr/share/apps/konqueror/servicemenus
~/.kde/share/apps/konqueror/servicemenus

Are you missing all Actions servicemenus, or just the Open Terminal Here? Try checking on those three directories. In my Kubuntu system:
- the first one (kubuntu-default-settings) only contains the Email and Kubuntu Package service menus (install/remove .deb files)
- the second one (/usr/share) contains all the servicemenus
- the third (~/.kde) contains K3B related servicemenus, only for my user.

The Open Terminal Here is located in /usr/share/apps/konqueror/servicemenus, with the filename konsolehere.desktop. If it's missing, you might have to make one yourself. Here are the contents of that file:

> 
[Desktop Entry]
ServiceTypes=inode/directory
Actions=openTerminalHere;
X-KDE-AuthorizeAction=shell_access
Encoding=UTF-8
Type=Application

Name=Konsole
Name[ar]=&#1587;&#1591;&#1585; &#1575;&#1604;&#1571;&#1608;&#1575;&#1605;&#1585;
Name[az]=Konsol
Name[be]=&#1050;&#1072;&#1085;&#1089;&#1086;&#1083;&#1103;
Name[bg]=&#1050;&#1086;&#1085;&#1079;&#1086;&#1083;&#1072;
Name[bn]=&#2453;&#2472;&#2488;&#2507;&#2482;
Name[bs]=Konzola
Name[ca]=Consola
Name[el]=&#922;&#959;&#957;&#963;&#972;&#955;&#945;
Name[eo]=Konzolo
Name[et]=Konsool
Name[eu]=Kontsola
Name[fa]=&#1705;&#1606;&#1587;&#1608;&#1604;
Name[he]=&#1502;&#1505;&#1493;&#1507;
Name[hi]=&#2325;&#2306;&#2360;&#2379;&#2354;
Name[hr]=Konzola
Name[is]=Skjáhermir
Name[ja]=&#12467;&#12531;&#12477;&#12540;&#12523;
Name[ko]=KDE&#50857; &#53080;&#49556;
Name[lo]=&#3716;&#3757;&#3737;&#3778;&#3722;&#3749; - K
Name[mk]=&#1050;&#1086;&#1085;&#1079;&#1086;&#1083;&#1072;
Name[mn]=&#1050;&#1086;&#1085;&#1089;&#1086;&#1083;
Name[nb]=Konsoll
Name[nn]=Konsoll
Name[pa]=&#2581;&#2672;&#2600;&#2616;&#2635;&#2610;
Name[pl]=Konsola
Name[ro]=Consol&#259;
Name[ru]=&#1050;&#1086;&#1085;&#1089;&#1086;&#1083;&#1100;
Name[se]=Konsolla
Name[sk]=Konzola
Name[sl]=Konzola
Name[ta]=&#2965;&#3006;&#2985;&#3021;&#2970;&#3019;&#2994;&#3021;
Name[tg]=&#1050;&#1086;&#1085;&#1089;&#1086;&#1083;
Name[th]=&#3588;&#3629;&#3609;&#3650;&#3595;&#3621; K
Name[zu]=Ikhonsoli

[Desktop Action openTerminalHere]
Name=Open Terminal Here
Name[af]=Maak Terminaal Hier Oop
Name[ar]=&#1575;&#1601;&#1578;&#1581; &#1587;&#1591;&#1585; &#1575;&#1604;&#1571;&#1608;&#1575;&#1605;&#1585; &#1607;&#1606;&#1575;
Name[az]=Terminal&#305; Burada Aç
Name[be]=&#1040;&#1076;&#1095;&#1099;&#1085;&#1110;&#1094;&#1100; &#1090;&#1101;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083; &#1090;&#1091;&#1090;
Name[bg]=&#1054;&#1090;&#1074;&#1072;&#1088;&#1103;&#1085;&#1077; &#1085;&#1072; &#1082;&#1086;&#1085;&#1079;&#1086;&#1083;&#1072; &#1090;&#1091;&#1082;
Name[bn]=&#2447;&#2454;&#2494;&#2472;&#2503; &#2463;&#2494;&#2480;&#2509;&#2478;&#2495;&#2472;&#2494;&#2482; &#2454;&#2507;&#2482;&#2507; 
Name[br]=Digeriñ un termenell amañ
Name[bs]=Otvori terminal ovdje
Name[ca]=Obre un terminal aquí
Name[cs]=Otev&#345;ít terminál zde
Name[cy]=Agor Terfynell Yma
Name[da]=Åbn terminal her
Name[de]=Terminal öffnen
Name[el]=&#902;&#957;&#959;&#953;&#947;&#956;&#945; &#964;&#949;&#961;&#956;&#945;&#964;&#953;&#954;&#959;&#973; &#949;&#948;&#974;
Name[eo]=Startu terminalon &#265;i tie
Name[es]=Abrir terminal aquí
Name[et]=Ava siin terminal
Name[eu]=Ireki terminala hemen
Name[fa]=&#1662;&#1575;&#1740;&#1575;&#1606;&#1607; &#1585;&#1575; &#1575;&#1740;&#1606;&#1580;&#1575; &#1576;&#1575;&#1586; &#1705;&#1606;
Name[fi]=Avaa komentoikkuna tähän
Name[fr]=Ouvrir un terminal ici
Name[fy]=Terminal iepenje
Name[ga]=Oscail Teirminéal Anseo
Name[gl]=Abrir Terminal Aqui
Name[he]=&#1508;&#1514;&#1495; &#1502;&#1505;&#1493;&#1507; &#1499;&#1488;&#1503;
Name[hi]=&#2335;&#2352;&#2381;&#2350;&#2367;&#2344;&#2354; &#2351;&#2361;&#2366;&#2305; &#2326;&#2379;&#2354;&#2375;&#2306;
Name[hr]=Ovdje otvori terminal
Name[hu]=Parancsértelmez&#337; megnyitása itt
Name[is]=Opna skjáhermi hér
Name[it]=Apri terminale qui
Name[ja]=&#12371;&#12371;&#12391;&#12479;&#12540;&#12511;&#12490;&#12523;&#12434;&#38283;&#12367;
Name[km]=&#6036;&#6078;&#6016;&#8203;&#6047;&#6098;&#6032;&#6070;&#6035;&#6072;&#6041;&#8203;&#6033;&#6072;&#6035;&#6081;&#6087;
Name[lo]=&#3776;&#3735;&#3765;&#3745;&#3764;&#3776;&#3737;&#3749;&#3714;&#3757;&#3719; X
Name[lt]=Atverti &#269;ia terminal&#261;
Name[lv]=Atv&#275;rt termin&#257;li &#353;eit
Name[mk]=&#1054;&#1090;&#1074;&#1086;&#1088;&#1080; &#1090;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083; &#1090;&#1091;&#1082;&#1072;
Name[mn]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083; &#1085;&#1101;&#1101;&#1093;
Name[ms]=Buka Terminal Di Sini
Name[mt]=Ifta&#295; terminal hawn
Name[nb]=Åpne terminal her
Name[nds]=Terminal hier opmaken
Name[nl]=Terminal openen
Name[nn]=Opna terminal her
Name[nso]=Bula mafelelo Mo
Name[pa]=&#2591;&#2608;&#2606;&#2624;&#2600;&#2610; &#2567;&#2673;&#2597;&#2631; &#2582;&#2635;&#2610;&#2635;
Name[pl]=Otwórz tutaj terminal
Name[pt]=Abrir um Terminal Aqui
Name[pt_BR]=Abrir Terminal Aqui
Name[ro]=Deschide un terminal aici
Name[ru]=&#1054;&#1090;&#1082;&#1088;&#1099;&#1090;&#1100; &#1090;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083; &#1079;&#1076;&#1077;&#1089;&#1100;
Name[rw]= Gufungura Igihera Hano
Name[se]=Raba terminála dáppe
Name[sk]=Tu otvori&#357; terminál
Name[sl]=Tu odpri terminal
Name[sr]=&#1054;&#1090;&#1074;&#1086;&#1088;&#1080; &#1090;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083; &#1086;&#1074;&#1076;&#1077;
Name[sr@Latn]=Otvori terminal ovde
Name[ss]=Vula sikhungo lapha
Name[sv]=Öppna terminal här
Name[ta]=&#2990;&#3009;&#2985;&#3016;&#2991; &#2951;&#2969;&#3021;&#2965;&#3015; &#2980;&#3007;&#2993;
Name[tg]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083;&#1088;&#1086; &#1076;&#1072;&#1088; &#1080;&#1085;&#1207;&#1086; &#1073;&#1086;&#1079; &#1082;&#1091;&#1085;&#1077;&#1076;
Name[th]=&#3648;&#3611;&#3636;&#3604;&#3648;&#3607;&#3629;&#3619;&#3660;&#3617;&#3636;&#3609;&#3629;&#3621;&#3607;&#3637;&#3656;&#3609;&#3637;&#3656;
Name[tr]=Terminali Burada Aç
Name[tt]=Terminaln&#305; Monda Aças&#305;
Name[uk]=&#1042;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080; &#1090;&#1077;&#1088;&#1084;&#1110;&#1085;&#1072;&#1083;
Name[uz]=&#1058;&#1077;&#1088;&#1084;&#1080;&#1085;&#1072;&#1083;&#1085;&#1080; &#1096;&#1091; &#1077;&#1088;&#1076;&#1072; &#1086;&#1095;&#1080;&#1096;
Name[ven]=Vulani theminala hafhano
Name[vi]=M&#7903; m&#7897;t Thi&#7871;t b&#7883; cu&#7889;i &#7903; &#272;ây
Name[wa]=Drovi on terminå chal
Name[xh]=Vula Isiphelo Sendlela Apha
Name[zh_CN]=&#22312;&#27492;&#25171;&#24320;&#32456;&#31471;
Name[zh_TW]=&#22312;&#36889;&#35041;&#38283;&#21855;&#32066;&#31471;&#27231;
Name[zu]=Vula ithuluzi langaphandle lapha
Icon=konsole
Exec=konsole --workdir %f


That's what's on my system. Don't forget, you need root privileges for that.

Even if that terminal service menu were missing, you can still use that feature by using the default shortcut F4. You might actually find it more convenient to use that shortcut (one keystroke) rather than the action service menu (2 mouse clicks).

Hope that helps somehow.

Note: I posted this same reply in KDE-Forum, under the name Jucato.

---

