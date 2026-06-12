---
title: "Desktop folder random location change"
date: 2008-05-07
forum: Desktop Environments
---

### Post by Tuxoid on 2008-05-07
I have no clue why it happened, but my Desktop folder is now my Home folder. I didn't do anything that I think would directly cause this; it just changed. I literally logged-out, logged back in, and my entire home folder was on my desktop (instead of what should be there). Not only am I concerned about how to fix this, I'd like to know why something like this would happen. The last significant thing I remember doing was changing from kdm to gdm. After switching display managers, the giant text on gdm went back to normal size. Then all of my program shortcuts disappeared off my desktop. I restart in hopes of it going back to normal, and instead, my entire home folder becomes my desktop folder. There is a file in my home directory called "Desktop". It's not a folder, it's a text file containing this:

```
[Desktop Entry]
Encoding=UTF-8
Type=Directory
BgImage=
Icon=desktop
Name=Desktop
Name[af]=Werkskerm
Name[ar]=&#1587;&#1591;&#1581; &#1575;&#1604;&#1605;&#1603;&#1578;&#1576;
Name[az]=Masa Üstü
Name[be]=&#1055;&#1088;&#1072;&#1094;&#1086;&#1118;&#1085;&#1099; &#1089;&#1090;&#1086;&#1083;
Name[bg]=&#1056;&#1072;&#1073;&#1086;&#1090;&#1077;&#1085; &#1087;&#1083;&#1086;&#1090;
Name[bn]=&#2465;&#2503;&#2488;&#2509;&#2453;&#2463;&#2474;
Name[br]=Gorretaol
Name[bs]=Radna površina
Name[ca]=Escriptori
Name[cs]=Pracovní plocha
Name[csb]=Pùlt
Name[cy]=Penbwrdd
Name[de]=Arbeitsfläche
Name[el]=&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;
Name[eo]=Tabulo
Name[es]=Escritorio
Name[et]=Töölaud
Name[eu]=Mahaigaina
Name[fa]=&#1585;&#1608;&#1605;&#1740;&#1586;&#1740;
Name[fi]=Työpöytä
Name[fo]=Skriviborð
Name[fr]=Bureau
Name[fy]=Buroblêd
Name[ga]=Deasc
Name[gl]=Escritorio
Name[he]=&#1513;&#1493;&#1500;&#1495;&#1503; &#1506;&#1489;&#1493;&#1491;&#1492;
Name[hi]=&#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2377;&#2346;
Name[hr]=Radna površina
Name[hsb]=D&#378;&#283;&#322;owy powjerch
Name[hu]=Munkaasztal
Name[is]=Skjáborð
Name[ja]=&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;
Name[kk]=&#1046;&#1201;&#1084;&#1099;&#1089; &#1199;&#1089;&#1090;&#1077;&#1083;&#1110;
Name[km]=&#6037;&#6098;&#6033;&#6083;&#6031;&#6075;
Name[ko]=&#45936;&#49828;&#53356;&#53681;
Name[lo]=&#3742;&#3767;&#3785;&#3737;&#3735;&#3765;&#3784;&#3776;&#3758;&#3761;&#3732;&#3751;&#3719;&#3713;
Name[lt]=Darbastalis
Name[lv]=Darbvirsma
Name[mk]=&#1056;&#1072;&#1073;&#1086;&#1090;&#1085;&#1072; &#1087;&#1086;&#1074;&#1088;&#1096;&#1080;&#1085;&#1072;
Name[mn]=&#1040;&#1078;&#1083;&#1099;&#1085; &#1090;&#1072;&#1074;&#1094;&#1072;&#1085;
Name[ms]=Ruang Kerja
Name[nb]=Skrivebord
Name[nds]=Schriefdisch
Name[ne]=&#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2346;
Name[nl]=Bureaublad
Name[nn]=Skrivebord
Name[oc]=BurèU
Name[pa]=&#2613;&#2631;&#2617;&#2652;&#2622;
Name[pl]=Pulpit
Name[pt]=Ambiente de Trabalho
Name[pt_BR]=Área de Trabalho
Name[ru]=&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;
Name[rw]=Ibiro
Name[se]=&#268;állinbeavdi
Name[sk]=Plocha
Name[sl]=Namizje
Name[sr]=&#1056;&#1072;&#1076;&#1085;&#1072; &#1087;&#1086;&#1074;&#1088;&#1096;&#1080;&#1085;&#1072;
Name[sr@Latn]=Radna površina
Name[ss]=Desktop 
Name[sv]=Skrivbord
Name[ta]=&#2990;&#3015;&#2994;&#3021;&#2990;&#3015;&#2970;&#3016;
Name[te]=&#3120;&#3074;&#3095;&#3128;&#3149;&#3104;&#3122;&#3074;
Name[tg]=&#1052;&#1080;&#1079;&#1080; &#1082;&#1086;&#1088;&#1251;
Name[th]=&#3614;&#3639;&#3657;&#3609;&#3607;&#3637;&#3656;&#3607;&#3635;&#3591;&#3634;&#3609;
Name[tr]=Masaüstü
Name[tt]=Östäl
Name[uk]=&#1057;&#1090;&#1110;&#1083;&#1100;&#1085;&#1080;&#1094;&#1103;
Name[uz]=&#1048;&#1096; &#1089;&#1090;&#1086;&#1083;&#1080;
Name[ven]=Desikithopo
Name[vi]=Màn hình n&#7873;n
Name[wa]=Sicribanne
Name[zh_CN]=&#26700;&#38754;
Name[zh_TW]=&#26700;&#38754;

X-Ubuntu-Gettext-Domain=desktop_kdebase
```

It's not normal. No other user on the machine has this file. Ironically, the file's icon is the same icon used on a desktop folder (brown wavy screen with two documents).

---

