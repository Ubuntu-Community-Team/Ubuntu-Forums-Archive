---
title: "Deleted Trash Shortcut"
date: 2009-07-11
forum: Desktop Environments
---

### Post by urlacher3292 on 2009-07-11
I accidentally deleted the trash.desktop icon from my desktop. How can I replace the shortcut so that it functions in the same way as in the default installation. Kubuntu Jaunty with KDE 4.2.4 by the way.

---

### Post by prshah on 2009-07-11
> **urlacher3292 said:**
> I accidentally deleted the trash.desktop icon from my desktop. How can I replace the shortcut so that it functions in the same way as in the default installation. Kubuntu Jaunty with KDE 4.2.4 by the way.

In KDE, you can always add a Trash widget to the desktop / taskbar. Click the upper right "cashew" and choose "Add widgets" then choose trash can and drag it wherever you want.

---

### Post by benerivo on 2009-07-11
As well prshah's way, you could get the original (non-plasmoid) icon back by pasting this code in to a text editor and calling the file trash.desktop and putting it inside your Desktop folder.

```
[Desktop Entry]
Encoding=UTF-8
Name=Trash
Name[ar]=&#1587;&#1604;&#1577; &#1575;&#1604;&#1605;&#1607;&#1605;&#1604;&#1575;&#1578;
Name[be@latin]=&#346;mietnica
Name[bg]=&#1050;&#1086;&#1096;&#1095;&#1077;
Name[bn]=&#2438;&#2476;&#2480;&#2509;&#2460;&#2472;&#2494;
Name[bn_IN]=&#2438;&#2476;&#2480;&#2509;&#2460;&#2472;&#2494;
Name[ca]=Paperera
Name[ca@valencia]=Paperera
Name[cs]=Ko&#353;
Name[csb]=Kòsz
Name[da]=Affald
Name[de]=Mülleimer
Name[el]=&#922;&#940;&#948;&#959;&#962; &#945;&#960;&#959;&#961;&#961;&#953;&#956;&#940;&#964;&#969;&#957;
Name[en_GB]=Wastebin
Name[es]=Papelera
Name[et]=Prügikast
Name[eu]=Zakarontzia
Name[fa]=&#1586;&#1576;&#1575;&#1604;&#1607;
Name[fi]=Roskakori
Name[fr]=Corbeille
Name[fy]=Jiskefet
Name[ga]=Bruscar
Name[gl]=Lixo
Name[gu]=&#2709;&#2714;&#2736;&#2750;&#2730;&#2759;&#2719;&#2752;
Name[he]=&#1488;&#1513;&#1508;&#1492;
Name[hi]=&#2352;&#2342;&#2381;&#2342;&#2368;
Name[hne]=&#2328;&#2369;&#2352;&#2369;&#2357;&#2366;
Name[hsb]=Papjernik
Name[hu]=Szemétkosár
Name[is]=Rusl
Name[it]=Cestino
Name[ja]=&#12372;&#12415;&#31665;
Name[kk]=&#1256;&#1096;&#1110;&#1088;&#1110;&#1083;&#1075;&#1077;&#1085;&#1076;&#1077;&#1088;
Name[km]=&#6034;&#6075;&#6020;&#8203;&#6047;&#6086;&#6042;&#6070;&#6040;
Name[kn]=&#3221;&#3256;&#3244;&#3265;&#3231;&#3277;&#3231;&#3263;
Name[ko]=&#55092;&#51648;&#53685;
Name[ku]=Çop
Name[lt]=&#352;iuk&#353;liad&#279;&#382;&#279;
Name[lv]=Miskaste
Name[mai]=&#2352;&#2342;&#2381;&#2342;&#2368;
Name[mk]=&#1050;&#1086;&#1088;&#1087;&#1072;
Name[ml]=&#3354;&#3381;&#3377;&#3393;&#3405;*
Name[mr]=&#2325;&#2330;&#2352;&#2366;&#2346;&#2375;&#2335;&#2368;
Name[ms]=Sampah
Name[nb]=Søppelbøtte
Name[nds]=Affalltünn
Name[nl]=Prullenbak
Name[nn]=Papirkorg
Name[or]=&#2822;&#2860;&#2864;&#2893;&#2844;&#2856;&#2878; &#2858;&#2878;&#2852;&#2893;&#2864;
Name[pa]=&#2608;&#2673;&#2598;&#2624;
Name[pl]=Kosz
Name[pt]=Lixo
Name[pt_BR]=Lixo
Name[ro]=Gunoi
Name[ru]=&#1050;&#1086;&#1088;&#1079;&#1080;&#1085;&#1072;
Name[se]=Ruskalihtti
Name[si]=&#3465;&#3520;&#3501;&#3517;&#3505; &#3510;&#3524;&#3517;&#3540;&#3512;
Name[sk]=Kô&#353;
Name[sl]=Smeti
Name[sr]=&#1057;&#1084;&#1077;&#1115;&#1077;
Name[sr@latin]=Sme&#263;e
Name[sv]=Papperskorg
Name[ta]=&#2949;&#2965;&#2993;&#3021;&#2993;&#3007;&#2975;&#2990;&#3021;
Name[tg]=&#1057;&#1072;&#1073;&#1072;&#1076;
Name[th]=&#3606;&#3633;&#3591;&#3586;&#3618;&#3632;
Name[tr]=Çöp
Name[uk]=&#1057;&#1084;&#1110;&#1090;&#1085;&#1080;&#1082;
Name[wa]=Batch
Name[x-test]=xxTrashxx
Name[zh_CN]=&#22238;&#25910;&#31449;
Name[zh_TW]=&#36039;&#28304;&#22238;&#25910;&#31570;
Comment=Contains removed files
Comment[ar]=&#1578;&#1581;&#1608;&#1610; &#1575;&#1604;&#1605;&#1604;&#1601;&#1575;&#1578; &#1575;&#1604;&#1605;&#1586;&#1575;&#1604;&#1577;
Comment[be]=&#1059;&#1090;&#1088;&#1099;&#1084;&#1083;&#1110;&#1074;&#1072;&#1077; &#1074;&#1099;&#1076;&#1072;&#1083;&#1077;&#1085;&#1099;&#1103; &#1092;&#1072;&#1081;&#1083;&#1099;
Comment[be@latin]=Zacho&#365;vaje vydalenyja faj&#322;y
Comment[bg]=&#1057;&#1098;&#1076;&#1098;&#1088;&#1078;&#1072; &#1087;&#1088;&#1077;&#1084;&#1072;&#1093;&#1085;&#1072;&#1090;&#1080; &#1092;&#1072;&#1081;&#1083;&#1086;&#1074;&#1077;
Comment[bn]=&#2478;&#2497;&#2459;&#2503; &#2475;&#2503;&#2482;&#2494; &#2475;&#2494;&#2439;&#2482; &#2469;&#2494;&#2453;&#2503;
Comment[bn_IN]=&#2478;&#2497;&#2459;&#2503; &#2475;&#2503;&#2482;&#2494; &#2475;&#2494;&#2439;&#2482; &#2437;&#2472;&#2509;&#2468;&#2480;&#2509;&#2477;&#2497;&#2453;&#2509;&#2468; &#2480;&#2527;&#2503;&#2459;&#2503;
Comment[ca]=Conté els fitxers suprimits
Comment[ca@valencia]=Conté els fitxers suprimits
Comment[cs]=Obsahuje odstran&#283;né soubory
Comment[csb]=Kònténer rëmniãtëch lopków
Comment[cy]=Yn cynnwys ffeiliau sydd wedi eu gwaredu
Comment[da]=Indeholder slettede filer
Comment[de]=Enthält weggeworfene Dateien
Comment[el]=&#928;&#949;&#961;&#953;&#941;&#967;&#949;&#953; &#964;&#945; &#945;&#966;&#945;&#953;&#961;&#949;&#956;&#941;&#957;&#945; &#945;&#961;&#967;&#949;&#943;&#945;
Comment[es]=Contiene los archivos eliminados
Comment[et]=Sisaldab eemaldatud faile
Comment[eu]=Kendutako fitxategiak ditu
Comment[fi]=Sisältää poistetut tiedostot
Comment[fr]=Contiens les fichiers effacés
Comment[fy]=Befetter fuortsmiten triemmen
Comment[ga]=Comhaid bhainte atá ann
Comment[gl]=Contén ficheiros eliminados
Comment[gu]=&#2726;&#2754;&#2736; &#2709;&#2736;&#2759;&#2738; &#2731;&#2750;&#2695;&#2738; &#2727;&#2736;&#2750;&#2741;&#2759; &#2715;&#2759;
Comment[he]=&#1502;&#1499;&#1497;&#1500; &#1511;&#1489;&#1510;&#1497;&#1501; &#1513;&#1492;&#1493;&#1505;&#1512;&#1493;
Comment[hi]=&#2350;&#2367;&#2335;&#2366;&#2312; &#2327;&#2312; &#2347;&#2364;&#2366;&#2311;&#2354;&#2379;&#2306; &#2325;&#2379; &#2352;&#2326;&#2340;&#2366; &#2361;&#2376;
Comment[hne]=&#2350;&#2375;&#2335;&#2366;&#2351; &#2347;&#2366;&#2311;&#2354; &#2354; &#2352;&#2326;&#2341;&#2375;
Comment[hr]=Sadr&#382;i izbrisane datoteke
Comment[hsb]=Tu so namakaja zni&#269;ene dataje
Comment[hu]=Törölt fájlokat tartalmaz
Comment[is]=Inniheldur skrár sem hefur verið eytt
Comment[it]=Contiene i file cancellati
Comment[ja]=&#21066;&#38500;&#12373;&#12428;&#12383;&#12501;&#12449;&#12452;&#12523;&#12434;&#20445;&#31649;&#12375;&#12390;&#12356;&#12414;&#12377;
Comment[ka]=&#4328;&#4308;&#4312;&#4330;&#4304;&#4309;&#4321; &#4332;&#4304;&#4328;&#4314;&#4312;&#4314; &#4324;&#4304;&#4312;&#4314;&#4308;&#4305;&#4321;
Comment[kk]=&#1256;&#1096;&#1110;&#1088;&#1110;&#1083;&#1075;&#1077;&#1085; &#1092;&#1072;&#1081;&#1083;&#1076;&#1072;&#1088; &#1078;&#1072;&#1090;&#1072;&#1090;&#1099;&#1085; &#1086;&#1088;&#1099;&#1085;
Comment[km]=&#6040;&#6070;&#6035;&#8203;&#6063;&#6016;&#6047;&#6070;&#6042;&#8203;&#6026;&#6082;&#6043;&#8203;&#6036;&#6070;&#6035;&#8203;&#6041;&#6016;&#8203;&#6021;&#6081;&#6025;
Comment[kn]=&#3236;&#3270;&#3223;&#3270;&#3238;&#3265; &#3257;&#3262;&#3221;&#3250;&#3262;&#3238; &#3221;&#3233;&#3236;&#3223;&#3251;&#3240;&#3277;&#3240;&#3265; &#3257;&#3274;&#3202;&#3238;&#3263;&#3238;&#3270;
Comment[ko]=&#49325;&#51228;&#46108; &#54028;&#51068; &#48143; &#54260;&#45908;&#44032; &#51080;&#49845;&#45768;&#45796;
Comment[ku]=Di de pelên hatine rakirin jî hene
Comment[lt]=&#268;ia yra i&#353;trintos bylos
Comment[lv]=Satur izmestos failus
Comment[mai]=&#2350;&#2375;&#2335;&#2366;&#2319;&#2354; &#2327;&#2375;&#2354; &#2347;&#2364;&#2366;&#2311;&#2354;&#2360;&#2349;&#2325; &#2352;&#2366;&#2326;&#2376;&#2340; &#2309;&#2331;&#2367;
Comment[mk]=&#1057;&#1086;&#1076;&#1088;&#1078;&#1080; &#1080;&#1079;&#1073;&#1088;&#1080;&#1096;&#1072;&#1085;&#1080; &#1076;&#1072;&#1090;&#1086;&#1090;&#1077;&#1082;&#1080;
Comment[ml]=&#3368;&#3392;&#3349;&#3405;&#3349;&#3330; &#3354;&#3398;&#3375;&#3405;&#3375;&#3370;&#3398;&#3359;&#3405;&#3359; &#3371;&#3375;&#3378;&#3393;&#3349;&#3379;&#3405;* &#3337;&#3378;&#3405;&#3370;&#3398;&#3359;&#3393;&#3368;&#3405;&#3368;&#3393;
Comment[mr]=&#2325;&#2366;&#2338;&#2370;&#2339; &#2335;&#2366;&#2325;&#2354;&#2375;&#2354;&#2375; &#2347;&#2366;&#2311;&#2354; &#2360;&#2350;&#2366;&#2357;&#2367;&#2359;&#2381;&#2335;&#2368;&#2340; &#2310;&#2361;&#2375;
Comment[nb]=Inneholder filer som er fjernet
Comment[nds]=Bargt wegmaakt Dateien
Comment[nl]=Bevat de verwijderde bestanden
Comment[nn]=Inneheld sletta filer
Comment[or]=&#2821;&#2858;&#2872;&#2878;&#2864;&#2879;&#2852; &#2859;&#2878;&#2823;&#2866;&#2839;&#2881;&#2849;&#2876;&#2879;&#2837;&#2881; &#2855;&#2878;&#2864;&#2851; &#2837;&#2864;&#2879;&#2853;&#2878;&#2831;
Comment[pa]=&#2617;&#2591;&#2622;&#2568;&#2566;&#2562; &#2603;&#2622;&#2567;&#2610;&#2622;&#2562; &#2608;&#2673;&#2582;&#2598;&#2622; &#2617;&#2632;
Comment[pl]=Zawiera usuni&#281;te pliki
Comment[pt]=Contém os ficheiros removidos
Comment[pt_BR]=Contém arquivos removidos
Comment[ro]=Con&#539;ine fi&#537;ierele &#537;terse
Comment[ru]=&#1057;&#1086;&#1076;&#1077;&#1088;&#1078;&#1080;&#1090; &#1091;&#1076;&#1072;&#1083;&#1105;&#1085;&#1085;&#1099;&#1077; &#1092;&#1072;&#1081;&#1083;&#1099;
Comment[se]=Dáppe leat eret váldon fiillat
Comment[si]=&#3512;&#3482;&#3505; &#3517;&#3503; &#3484;&#3548;&#3505;&#3540; &#3463;&#3501;
Comment[sk]=Obsahuje vymazané súbory
Comment[sl]=Vsebujejo odstranjene datoteke
Comment[sr]=&#1057;&#1072;&#1076;&#1088;&#1078;&#1080; &#1091;&#1082;&#1083;&#1086;&#1114;&#1077;&#1085;&#1077; &#1092;&#1072;&#1112;&#1083;&#1086;&#1074;&#1077;
Comment[sr@latin]=Sadr&#382;i uklonjene fajlove
Comment[sv]=Innehåller borttagna filer
Comment[ta]=&#2949;&#2965;&#2993;&#3021;&#2993;&#2986;&#3021;&#2986;&#2975;&#3021;&#2975; &#2965;&#3019;&#2986;&#3021;&#2986;&#3009;&#2965;&#2995;&#3021; &#2951;&#2992;&#3009;&#2965;&#3021;&#2965;&#3007;&#2993;&#2980;&#3009;
Comment[te]=&#3108;&#3136;&#3128;&#3135;&#3125;&#3143;&#3128;&#3135;&#3112; &#3115;&#3144;&#3123;&#3149;&#3123;&#3112;&#3137; &#3093;&#3122;&#3135;&#3095;&#3135;&#3125;&#3137;&#3074;&#3103;&#3137;&#3074;&#3110;&#3135;
Comment[tg]=&#1044;&#1086;&#1088;&#1086;&#1080; &#1092;&#1072;&#1081;&#1083;&#1203;&#1086;&#1080; &#1085;&#1077;&#1089;&#1090;&#1082;&#1072;&#1088;&#1076;&#1072;&#1096;&#1091;&#1076;&#1072;
Comment[th]=&#3610;&#3619;&#3619;&#3592;&#3640;&#3649;&#3615;&#3657;&#3617;&#3607;&#3637;&#3656;&#3606;&#3641;&#3585;&#3621;&#3610;
Comment[tr]=Silinen dosyalar&#305; içerir
Comment[uk]=&#1052;&#1110;&#1089;&#1090;&#1080;&#1090;&#1100; &#1074;&#1080;&#1083;&#1091;&#1095;&#1077;&#1085;&#1110; &#1092;&#1072;&#1081;&#1083;&#1080;
Comment[uz]=Olib tashlangan fayllardan iborat
Comment[uz@cyrillic]=&#1054;&#1083;&#1080;&#1073; &#1090;&#1072;&#1096;&#1083;&#1072;&#1085;&#1075;&#1072;&#1085; &#1092;&#1072;&#1081;&#1083;&#1083;&#1072;&#1088;&#1076;&#1072;&#1085; &#1080;&#1073;&#1086;&#1088;&#1072;&#1090;
Comment[vi]=Ch&#7913;a t&#7853;p tin b&#7883; g&#7905; b&#7887;
Comment[wa]=I gn a dvins des fitchîs oistés
Comment[xh]=Iqulathe iifayile ezisusiweyo
Comment[x-test]=xxContains removed filesxx
Comment[zh_CN]=&#20648;&#23384;&#24050;&#21024;&#38500;&#30340;&#25991;&#20214;
Comment[zh_TW]=&#21253;&#21547;&#24050;&#31227;&#38500;&#30340;&#27284;&#26696;
Icon=user-trash-full
EmptyIcon=user-trash
Type=Link
URL=trash:/
OnlyShowIn=KDE;
```

---

### Post by urlacher3292 on 2009-07-11
Thank you both so much. I will try both of your ideas and find what I like best. Cool Michael Jackson icon by the way.

---

