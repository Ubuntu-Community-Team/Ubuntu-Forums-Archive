---
title: "date &amp; time broken"
date: 2006-11-21
forum: Desktop Environments
---

### Post by fireangel on 2006-11-21
Hey ubuntu-users!

Just recently installed ubuntu because I wanted to give it a try (I was using fedora core before that)

I played a little with the "Synaptec Package Manger" and somehow managed to break the Date & Time applet.

It's working fine except if you right click it and choose "Adjust Date and Time" ... nothing happens.

Even if I try System-> Administration -> Time & Date ... nothing happens.

What did I do? Which package is missing?

..::fireangel::..

---

### Post by ciscosurfer on 2006-11-21
Will it start if you enter a terminal and issue```
time-admin
```If not, then you need to recreate the .desktop file that loads it.  Are you using Dapper or Edgy (don't know if the following works for Dapper, it does for Edgy).[LIST=1]
[*]Enter a terminal and type in the following```
sudo gedit /usr/share/applications/time.desktop
```
[*]Copy the following information over (keep in mind, you probably don't use most of these language settings, but it won't hurt the file, so just copy the whole text over to the newly created file from above:[/LIST][INDENT][Desktop Entry]
Name=Time and Date
Name[ar]=&#1575;&#1604;&#1608;&#1602;&#1578; &#1608; &#1575;&#1604;&#1578;&#1617;&#1575;&#1585;&#1610;&#1582;
Name[be]=&#1044;&#1072;&#1090;&#1072; &#1081; &#1095;&#1072;&#1089;
Name[bg]=&#1044;&#1072;&#1090;&#1072; &#1080; &#1095;&#1072;&#1089;
Name[bn]=&#2488;&#2478;&#2527; &#2447;&#2476;&#2434; &#2468;&#2494;&#2480;&#2495;&#2454;
Name[bn_IN]=&#2488;&#2478;&#2527; &#2447;&#2476;&#2434; &#2468;&#2494;&#2480;&#2495;&#2454;
Name[ca]=Hora i data
Name[cs]=Datum a &#269;as
Name[cy]=Dyddiad ac Amser
Name[da]=Dato og klokkeslæt
Name[de]=Datum und Uhrzeit
Name[dz]=&#3910;&#3956;&#3851;&#3930;&#3964;&#3921;&#3851;&#3921;&#3908;&#3851;&#3930;&#3962;&#3942;&#3851;&#3906;&#4018;&#3908;&#3942;&#3853;
Name[el]=&#911;&#961;&#945; &#954;&#945;&#953; &#919;&#956;&#949;&#961;&#959;&#956;&#951;&#957;&#943;&#945;
Name[en_CA]=Time and Date
Name[en_GB]=Time and Date
Name[es]=Hora y fecha
Name[et]=Kellaaeg ja kuupäev
Name[eu]=Ordua eta data
Name[fa]=&#1586;&#1605;&#1575;&#1606; &#1608; &#1578;&#1575;&#1585;&#1740;&#1582;
Name[fi]=Aika ja päiväys
Name[fr]=Date et heure
Name[gl]=Hora e data
Name[gu]=&#2744;&#2734;&#2735; &#2693;&#2728;&#2759; &#2724;&#2750;&#2736;&#2752;&#2710;
Name[he]=&#1494;&#1502;&#1503; &#1493;&#1514;&#1488;&#1512;&#1497;&#1498;
Name[hi]=&#2360;&#2350;&#2351; &#2324;&#2352; &#2340;&#2366;&#2352;&#2368;&#2326;&#2364;
Name[hr]=Vrijeme i Datum
Name[hu]=Id&#337; és dátum
Name[id]=Tanggal dan Waktu
Name[it]=Ora e data
Name[ja]=&#26178;&#21051;&#12392;&#26085;&#20184;&#12398;&#35373;&#23450;
Name[ka]=&#4307;&#4320;&#4317; &#4307;&#4304; &#4311;&#4304;&#4320;&#4312;&#4326;&#4312;
Name[ko]=&#49884;&#44036;&#44284; &#45216;&#51676;
Name[lt]=Laiko ir datos nustatymai
Name[lv]=Laiks un datums
Name[mg]=Daty sy ora
Name[mk]=&#1042;&#1088;&#1077;&#1084;&#1077; &#1080; &#1076;&#1072;&#1090;&#1091;&#1084;
Name[ml]=&#3384;&#3374;&#3375;&#3381;&#3393;&#3330; &#3364;&#3392;&#3375;&#3364;&#3391;&#3375;&#3393;&#3330;
Name[ms]=Masa dan Tarikh
Name[nb]=Tid og dato
Name[ne]=&#2360;&#2350;&#2351; &#2352; &#2350;&#2367;&#2340;&#2368;
Name[nl]=Datum en tijd
Name[or]=&#2872;&#2862;&#2911; &#2831;&#2860;&#2818; &#2852;&#2878;&#2864;&#2879;&#2838;
Name[pa]=&#2616;&#2606;&#2622;&#2562; &#2565;&#2596;&#2631; &#2606;&#2623;&#2596;&#2624;
Name[pl]=Czas i data
Name[pt]=Data e Hora
Name[pt_BR]=Data e Hora
Name[ro]=Or&#259; &#351;i dat&#259;
Name[ru]=&#1044;&#1072;&#1090;&#1072; &#1080; &#1074;&#1088;&#1077;&#1084;&#1103;
Name[sk]=Dátum a &#269;as
Name[sq]=Ora dhe Data
Name[sr]=&#1042;&#1088;&#1077;&#1084;&#1077; &#1080; &#1076;&#1072;&#1090;&#1091;&#1084;
Name[sr@Latn]=Vreme i datum
Name[sv]=Tid och datum
Name[ta]=&#2980;&#3015;&#2980;&#3007; &#2990;&#2993;&#3021;&#2993;&#3009;&#2990;&#3021; &#2984;&#3015;&#2992;&#2990;&#3021;
Name[th]=&#3648;&#3623;&#3621;&#3634;&#3649;&#3621;&#3632;&#3623;&#3633;&#3609;&#3607;&#3637;&#3656;
Name[tr]=Zaman ve Tarih
Name[uk]=&#1044;&#1072;&#1090;&#1072; &#1081; &#1095;&#1072;&#1089;
Name[vi]=Ngày và Gi&#7901;
Name[wa]=Date et eure
Name[xh]=UMhla neXesha
Name[zh_CN]=&#26102;&#38388;&#21644;&#26085;&#26399;
Name[zh_HK]=&#26178;&#38291;&#21450;&#26085;&#26399;&#35373;&#23450;
Name[zh_TW]=&#26178;&#38291;&#21450;&#26085;&#26399;&#35373;&#23450;
Comment=Change system time, date, and timezone
Comment[ar]=&#1578;&#1594;&#1610;&#1610;&#1585; &#1608;&#1602;&#1578; &#1575;&#1604;&#1606;&#1617;&#1592;&#1575;&#1605; &#1608; &#1575;&#1604;&#1578;&#1617;&#1575;&#1585;&#1610;&#1582; &#1608; &#1575;&#1604;&#1605;&#1606;&#1591;&#1602;&#1577; &#1575;&#1604;&#1586;&#1617;&#1605;&#1606;&#1610;&#1617;&#1577;
Comment[be]=&#1047;&#1100;&#1084;&#1077;&#1085;&#1072; &#1089;&#1099;&#1089;&#1090;&#1101;&#1084;&#1085;&#1072;&#1075;&#1072; &#1095;&#1072;&#1089;&#1091;, &#1076;&#1072;&#1090;&#1099; &#1110; &#1095;&#1072;&#1089;&#1072;&#1074;&#1072;&#1075;&#1072; &#1087;&#1086;&#1103;&#1089;&#1091;
Comment[bg]=&#1055;&#1088;&#1086;&#1084;&#1103;&#1085;&#1072; &#1085;&#1072; &#1076;&#1072;&#1090;&#1072;&#1090;&#1072;, &#1095;&#1072;&#1089;&#1072; &#1080; &#1095;&#1072;&#1089;&#1086;&#1074;&#1080;&#1103; &#1087;&#1086;&#1103;&#1089; &#1085;&#1072; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;&#1090;&#1072;
Comment[bn]=&#2488;&#2495;&#2488;&#2509;&#2463;&#2503;&#2478;&#2503;&#2480; &#2488;&#2478;&#2527;, &#2468;&#2494;&#2480;&#2495;&#2454; &#2447;&#2476;&#2434; &#2488;&#2478;&#2527;&#2503;&#2480;-&#2437;&#2462;&#2509;&#2458;&#2482; &#2474;&#2480;&#2495;&#2476;&#2480;&#2509;&#2468;&#2472; &#2453;&#2480;&#2497;&#2472;
Comment[bn_IN]=&#2488;&#2495;&#2488;&#2509;&#2463;&#2503;&#2478;&#2503;&#2480; &#2488;&#2478;&#2527;, &#2468;&#2494;&#2480;&#2495;&#2454; &#2447;&#2476;&#2434; &#2488;&#2478;&#2527;&#2503;&#2480;-&#2437;&#2462;&#2509;&#2458;&#2482; &#2474;&#2480;&#2495;&#2476;&#2480;&#2509;&#2468;&#2472; &#2453;&#2480;&#2497;&#2472;
Comment[ca]=Canvieu l'hora, la data, i el fus horari del sistema
Comment[cs]=Zm&#283;nit systémový &#269;as, datum a &#269;asovou zónu.
Comment[cy]=Newid dyddiad, amser a chylchfa amser y system
Comment[da]=Skift klokkeslæt, dato og tidszone
Comment[de]=Systemzeit, Datum und Zeitzone festlegen
Comment[dz]=&#3938;&#3954;&#3928;&#3851;&#3939;&#3956;&#3906;&#3942;&#3851;&#3904;&#4017;&#3954;&#3851;&#3910;&#3956;&#3851;&#3930;&#3964;&#3921;&#3851;&#3921;&#3908;&#3851; &#3930;&#3962;&#3942;&#3851;&#3906;&#4018;&#3908;&#3942;&#3851; &#3910;&#3956;&#3851;&#3930;&#3964;&#3921;&#3851;&#3906;&#4019;&#3954;&#3908;&#3851;&#3942;&#4001;&#3962;&#3851;&#3930;&#3956;&#3851; &#3926;&#3942;&#3986;&#4017;&#3956;&#3938;&#3851;&#3926;&#3909;&#3964;&#3942;&#3851;&#3936;&#3926;&#3921;&#3853;
Comment[el]=&#913;&#955;&#955;&#945;&#947;&#942; &#974;&#961;&#945;&#962;, &#951;&#956;&#949;&#961;&#959;&#956;&#951;&#957;&#943;&#945;&#962; &#954;&#945;&#953; &#950;&#974;&#957;&#951;&#962; &#974;&#961;&#945;&#962; &#963;&#965;&#963;&#964;&#942;&#956;&#945;&#964;&#959;&#962;
Comment[en_CA]=Change system time, date, and timezone
Comment[en_GB]=Change system time, date, and timezone
Comment[es]=Cambiar hora, fecha y zona horaria
Comment[et]=Kellaaja, kuupäeva ja ajavööndi muutmine
Comment[eu]=Aldatu sistemako ordua, data eta ordu-zona.
Comment[fa]=&#1578;&#1594;&#1740;&#1740;&#1585; &#1586;&#1605;&#1575;&#1606; &#1587;&#1740;&#1587;&#1578;&#1605;&#1548; &#1578;&#1575;&#1585;&#1740;&#1582; &#1608; &#1605;&#1606;&#1591;&#1602;&#1607;*&#1740; &#1586;&#1605;&#1575;&#1606;&#1740;
Comment[fi]=Muuta järjestelmän aikaa, päiväystä ja aikavyöhykettä
Comment[fr]=Change la date, l'heure et le fuseau horaire.
Comment[gl]=Cambiar hora, data e fuso horario
Comment[gu]=&#2744;&#2751;&#2744;&#2765;&#2719;&#2734; &#2744;&#2734;&#2735;, &#2724;&#2750;&#2736;&#2752;&#2710;, &#2693;&#2728;&#2759; &#2719;&#2750;&#2696;&#2734; &#2717;&#2763;&#2728; &#2732;&#2726;&#2738;&#2763;
Comment[he]=&#1499;&#1497;&#1493;&#1493;&#1503; &#1492;&#1513;&#1506;&#1493;&#1503;, &#1492;&#1514;&#1488;&#1512;&#1497;&#1498; &#1493;&#1488;&#1497;&#1494;&#1493;&#1512; &#1492;&#1494;&#1502;&#1503; &#1513;&#1500; &#1492;&#1502;&#1506;&#1512;&#1499;&#1514;
Comment[hi]=&#2348;&#2342;&#2354;&#2375;&#2306; &#2340;&#2366;&#2352;&#2368;&#2326;&#2364;, &#2360;&#2350;&#2351; &#2324;&#2352; &#2360;&#2350;&#2351; &#2325;&#2381;&#2359;&#2375;&#2340;&#2381;&#2352;
Comment[hr]=Promijenite vrijeme, datum i vremensku zonu sustava.
Comment[hu]=Rendszerid&#337;, dátum és id&#337;zóna megváltoztatása
Comment[id]=Ubah tanggal, waktu, dan zona waktu komputer
Comment[it]=Cambia l'ora, la data e il fuso orario del sistema
Comment[ja]=&#12471;&#12473;&#12486;&#12512;&#26178;&#21051;&#12420;&#26085;&#20184;&#12289;&#12479;&#12452;&#12512;&#12478;&#12540;&#12531;&#12434;&#31649;&#29702;&#12375;&#12414;&#12377;
Comment[ka]=&#4321;&#4312;&#4321;&#4322;&#4308;&#4315;&#4323;&#4320;&#4312; &#4307;&#4320;&#4317;&#4312;&#4321;, &#4311;&#4304;&#4320;&#4312;&#4326;&#4312;&#4321;&#4304; &#4307;&#4304; &#4307;&#4320;&#4317;&#4312;&#4321; &#4310;&#4317;&#4316;&#4312;&#4321; &#4328;&#4308;&#4330;&#4309;&#4314;&#4304;
Comment[ko]=&#49884;&#44036;, &#45216;&#51676;&#50752; &#49884;&#44036;&#45824;&#47484; &#49444;&#51221;&#54633;&#45768;&#45796;
Comment[lt]=Keisti sistemos laik&#261;, dat&#261; ir laiko juost&#261;
Comment[lv]=Maina sist&#275;mas laiku, datumu un laika zonu
Comment[mg]=Hanova ny ora, daty, ary faitroran'ny rafitra
Comment[mk]=&#1055;&#1088;&#1086;&#1084;&#1077;&#1085;&#1077;&#1090;&#1077; &#1075;&#1086; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1089;&#1082;&#1086;&#1090;&#1086; &#1074;&#1088;&#1077;&#1084;&#1077;, &#1076;&#1072;&#1090;&#1091;&#1084; &#1080; &#1074;&#1088;&#1077;&#1084;&#1077;&#1085;&#1089;&#1082;&#1072; &#1079;&#1086;&#1085;&#1072;
Comment[ml]=&#3349;&#3330;&#3370;&#3405;&#3375;&#3394;&#3359;&#3405;&#3359;&#3377;&#3391;&#3368;&#3405;*&#3377;&#3398; &#3384;&#3374;&#3375;&#3330;, &#3364;&#3392;&#3375;&#3364;&#3391;, &#3359;&#3400;&#3330; &#3384;&#3403;&#3363;&#3405;* &#3374;&#3390;&#3377;&#3405;&#3377;&#3393;&#3349;
Comment[ms]=Tukar masa , tarikh dan zonwaktu sistem
Comment[nb]=Endre systemets tid, dato og tidssone
Comment[ne]=&#2346;&#2381;&#2352;&#2339;&#2366;&#2354;&#2368; &#2360;&#2350;&#2351;,&#2350;&#2367;&#2340;&#2368; &#2352; &#2360;&#2350;&#2351; &#2325;&#2381;&#2359;&#2375;&#2340;&#2381;&#2352;&#2354;&#2366;&#2312; &#2346;&#2352;&#2367;&#2357;&#2352;&#2381;&#2340;&#2344; &#2327;&#2352;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360;&#2381; 
Comment[nl]=Datum, tijd en tijdzone aanpassen
Comment[or]=&#2852;&#2856;&#2893;&#2852;&#2893;&#2864;&#2864; &#2872;&#2862;&#2911;, &#2852;&#2878;&#2864;&#2879;&#2838;, &#2831;&#2860;&#2818; &#2872;&#2862;&#2911; &#2862;&#2851;&#2893;&#2849;&#2867;&#2837;&#2881; &#2858;&#2864;&#2879;&#2860;&#2864;&#2893;&#2852;&#2856; &#2837;&#2864;&#2856;&#2893;&#2852;&#2881;
Comment[pa]=&#2616;&#2623;&#2616;&#2591;&#2606; &#2616;&#2606;&#2622;&#2562;, &#2606;&#2623;&#2596;&#2624; &#2565;&#2596;&#2631; &#2616;&#2606;&#2622;&#2562;-&#2582;&#2631;&#2596;&#2608; &#2596;&#2604;&#2598;&#2624;&#2610;
Comment[pl]=Zmiana czasu, daty i strefy czasowej
Comment[pt]=Alterar a hora, data e zona horária do sistema
Comment[pt_BR]=Altere a hora, a data e o fuso horário do sistema
Comment[ro]=Setare or&#259;, dat&#259; &#351;i fus orar
Comment[ru]=&#1059;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1072; &#1074;&#1088;&#1077;&#1084;&#1077;&#1085;&#1080;, &#1076;&#1072;&#1090;&#1099; &#1080; &#1095;&#1072;&#1089;&#1086;&#1074;&#1086;&#1075;&#1086; &#1087;&#1086;&#1103;&#1089;&#1072;.
Comment[sk]=Zmena dátumu, &#269;asu a &#269;asová zóna
Comment[sq]=Ndryshon orën e sistemit, datën, dhe zonën e orës
Comment[sr]=&#1055;&#1088;&#1086;&#1084;&#1077;&#1085;&#1080;&#1090;&#1077; &#1074;&#1088;&#1077;&#1084;&#1077;, &#1076;&#1072;&#1090;&#1091;&#1084; &#1080; &#1074;&#1088;&#1077;&#1084;&#1077;&#1085;&#1089;&#1082;&#1091; &#1079;&#1086;&#1085;&#1091; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;.
Comment[sr@Latn]=Promenite vreme, datum i vremensku zonu sistema.
Comment[sv]=Ändra systemtid, datum och tidszon.
Comment[ta]=&#2965;&#2979;&#3007;&#2985;&#3007; &#2984;&#3015;&#2992;&#2990;&#3021;, &#2980;&#3015;&#2980;&#3007; &#2990;&#2993;&#3021;&#2993;&#3009;&#2990;&#3021; &#2951;&#2975;&#2980;&#3021;&#2980;&#3007;&#2993;&#3021;&#2965;&#3015;&#2993;&#3021;&#2986; &#2984;&#3015;&#2992;&#2990;&#3021; &#2951;&#2997;&#3016;&#2965;&#2995;&#3016; &#2990;&#3006;&#2993;&#3021;&#2993;&#2997;&#3009;&#2990;&#3021;
Comment[th]=&#3605;&#3633;&#3657;&#3591;&#3648;&#3623;&#3621;&#3634;, &#3623;&#3633;&#3609;&#3607;&#3637;&#3656;, &#3649;&#3621;&#3632;&#3648;&#3586;&#3605;&#3648;&#3623;&#3621;&#3634;&#3586;&#3629;&#3591;&#3619;&#3632;&#3610;&#3610;
Comment[tr]=Sistem zaman&#305;, tarihi ve zaman dilimini de&#287;i&#351;tir
Comment[uk]=&#1047;&#1084;&#1110;&#1085;&#1080;&#1090;&#1080; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1085;&#1091; &#1076;&#1072;&#1090;&#1091;, &#1095;&#1072;&#1089; &#1110; &#1095;&#1072;&#1089;&#1086;&#1074;&#1080;&#1081; &#1087;&#1086;&#1103;&#1089;
Comment[vi]=S&#7917;a &#273;&#7893;i th&#7901;i gian, ngày và múi gi&#7901; trong h&#7879; th&#7889;ng
Comment[wa]=Candjî l' date, eure eyet coisse d' eureye do sistinme
Comment[xh]=Tshintsha ixesha lenkqubo, umhla nezowuni yexesha
Comment[zh_CN]=&#26356;&#25913;&#31995;&#32479;&#26102;&#38388;&#12289;&#26085;&#26399;&#21644;&#26102;&#21306;
Comment[zh_HK]=&#25913;&#35722;&#31995;&#32113;&#26178;&#38291;&#12289;&#26085;&#26399;&#21450;&#26178;&#21312;
Comment[zh_TW]=&#25913;&#35722;&#31995;&#32113;&#26178;&#38291;&#12289;&#26085;&#26399;&#21450;&#26178;&#21312;
Exec=time-admin
Icon=config-date
Terminal=false
Type=Application
Categories=GNOME;GTK;Application;System;Settings;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-system-tools
X-GNOME-Bugzilla-Component=time-admin
X-GNOME-Bugzilla-Version=2.15.5
StartupNotify=true
Encoding=UTF-8
X-Ubuntu-Gettext-Domain=gnome-system-tools

[/INDENT]4. Save and exit out of GEdit.
   5. Logout of your session, then log back in again.

You should be able to use the Time and Date panel now, either via the GUI or by entering **time-admin** in a terminal.

---

### Post by fireangel on 2006-11-22
time-admin worked for me!

then it installed something for internet synchronisation und now it works perfekt again!

BIG THX!

:D

---

### Post by ciscosurfer on 2006-11-22
> **fireangel said:**
> time-admin worked for me!

then it installed something for internet synchronisation und now it works perfekt again!

BIG THX!

:DAbsolutely!  Glad it worked out for you!

---

