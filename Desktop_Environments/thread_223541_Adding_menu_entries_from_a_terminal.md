---
title: "Adding menu entries from a terminal"
date: 2006-07-26
forum: Desktop Environments
---

### Post by JKing on 2006-07-26
I'm trying to write a shell script that will compile a particular application and then add a menu item for it; the problem is that I don't know how the Applications menu is populated.  

I've searched the Web and come up with various things that seem like they might be related, but have so far had no luck to speak of.  I know that the entries are defined with *.desktop files and have created such an appropriate file, but I'd appreciate some suggestions as to where I should go from there.

---

### Post by simonn on 2006-07-26
Hat you have heard is correct. Use an existing .desktop file as a template - look in /usr/share/applications.

Put them in /usr/local/share/applications.

---

### Post by JKing on 2006-07-26
Doing this does not seem to add the entry to the Applications menu, though.  Is there anything I could be doing wrong?

---

### Post by mlind on 2006-07-26
What are the contents of your .desktop file ?

---

### Post by jgcamp99 on 2006-07-26
Is there an item in Applications, Accessories called Alacarte Menu Editor ? That's what I wind up using to add/Remove and Edit entries in the Applications drop down for Gnome. If you don't have that, then it would have to added from the Add/Remove drop down, once it opens, there is an Accessories section that you can downlaod and install.

---

### Post by trent dillman on 2006-07-27
...

---

### Post by aysiu on 2006-07-27
The directory is /usr/share/applications

Here is the rhythmbox.desktop file from there: ```
[Desktop Entry]
Encoding=UTF-8
Name=Rhythmbox Music Player
Name[bg]=&#1057;&#1083;&#1091;&#1096;&#1072;&#1085;&#1077; &#1085;&#1072; &#1084;&#1091;&#1079;&#1080;&#1082;&#1072; (Rhythmbox)
Name[ca]=Reproductor de música Rhythmbox
Name[cs]=P&#345;ehráva&#269; hudby Rhythmbox
Name[da]=Rhythmbox musikafspiller
Name[de]=Rhythmbox Musik-Player
Name[el]=Rhythmbox Music Player
Name[en_CA]=Rhythmbox Music Player
Name[en_GB]=Rhythmbox Music Player
Name[es]=Reproductor de música Rhythmbox
Name[eu]=Rhythmbox musika erreproduzigailua
Name[fi]=Rhythmbox-musiikkisoitin
Name[fr]=Lecteur de musique Rhythmbox
Name[gl]=Reproductor de música Rhythmbox
Name[hu]=Rhythmbox zenelejátszó
Name[ja]=Rhythmbox &#12511;&#12517;&#12540;&#12472;&#12483;&#12463;&#12539;&#12503;&#12524;&#12452;&#12516;&#12540;
Name[ko]=&#47532;&#46316;&#48149;&#49828; &#51020;&#50501; &#50672;&#51452;&#44592;
Name[lt]=Rhythmbox muzikos grotuvas
Name[mk]=&#1056;&#1080;&#1090;&#1072;&#1084;&#1073;&#1086;&#1082;&#1089; - &#1055;&#1091;&#1096;&#1090;&#1072;&#1095; &#1085;&#1072; &#1084;&#1091;&#1079;&#1080;&#1082;&#1072;
Name[nb]=Rhythmbox musikkavspiller
Name[ne]=&#2352;&#2367;&#2342;&#2350;&#2348;&#2325;&#2381;&#2360; &#2360;&#2306;&#2327;&#2367;&#2340; &#2346;&#2381;&#2354;&#2375;&#2351;&#2352;
Name[nl]=Rhythmbox muziekspeler
Name[no]=Rhythmbox musikkavspiller
Name[pa]=&#2608;&#2624;&#2597;&#2606;&#2604;&#2622;&#2581;&#2616; &#2616;&#2672;&#2583;&#2624;&#2596; &#2602;&#2610;&#2631;&#2565;&#2608;
Name[pt]=Reprodutor de Música Rhythmbox
Name[pt_BR]=Reprodutor de Músicas Rhythmbox
Name[sk]=Prehráva&#269; hudby Rhythmbox
Name[th]=&#3605;&#3633;&#3623;&#3648;&#3621;&#3656;&#3609;&#3648;&#3614;&#3621;&#3591; Rhythmbox
Name[uk]=&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1074;&#1072;&#1095; &#1084;&#1091;&#1079;&#1080;&#1082;&#1080; Rhythmbox
Name[vi]=B&#7897; phát nh&#7841;c Rhythmbox
Name[zh_CN]=Rhythmbox &#38899;&#20048;&#25773;&#25918;&#22120;
Name[zh_TW]=Rhythmbox &#38899;&#27138;&#25773;&#25918;&#31243;&#24335;
GenericName=Music Player
GenericName[ar]=&#1593;&#1575;&#1586;&#1601; &#1575;&#1604;&#1605;&#1608;&#1587;&#1610;&#1602;&#1609;
GenericName[az]=Musiqi Çal&#287;&#305;c&#305;s&#305;
GenericName[be]=&#1055;&#1088;&#1072;&#1081;&#1075;&#1088;&#1072;&#1074;&#1072;&#1083;&#1100;&#1085;&#1110;&#1082; &#1084;&#1091;&#1079;&#1099;&#1082;&#1110;
GenericName[bg]=&#1057;&#1083;&#1091;&#1096;&#1072;&#1085;&#1077; &#1085;&#1072; &#1084;&#1091;&#1079;&#1080;&#1082;&#1072;
GenericName[ca]=Reproductor de música
GenericName[cs]=P&#345;ehráva&#269; hudby
GenericName[cy]=Chwaraewr Cerddoriaeth
GenericName[da]=Musikafspiller
GenericName[de]=Musik-Player
GenericName[el]=Music Player
GenericName[en_CA]=Music Player
GenericName[en_GB]=Music Player
GenericName[es]=Reproductor de música
GenericName[et]=Muusikamängija
GenericName[eu]=Musika erreproduzigailua
GenericName[fi]=Musiikkisoitin
GenericName[fr]=Lecteur de musique
GenericName[ga]=Seinnteoir Ceoil
GenericName[gl]=Reproductor de música
GenericName[he]=&#1504;&#1490;&#1503; &#1492;&#1502;&#1493;&#1494;&#1497;&#1511;&#1492;
GenericName[hr]=Glazbeni program
GenericName[hu]=Zenelejátszó
GenericName[id]=Pemutar Musik
GenericName[is]=Tónlistarspilari
GenericName[it]=Lettore musicale
GenericName[ja]=&#12511;&#12517;&#12540;&#12472;&#12483;&#12463;&#12539;&#12503;&#12524;&#12452;&#12516;&#12540;
GenericName[ko]=&#51020;&#50501; &#50672;&#51452;&#44592;
GenericName[lt]=Muzikos grotuvas
GenericName[lv]=M&#363;zikas Atska&#326;ot&#257;js
GenericName[mk]=&#1055;&#1091;&#1096;&#1090;&#1072;&#1095; &#1085;&#1072; &#1052;&#1091;&#1079;&#1080;&#1082;&#1072;
GenericName[mn]=&#1061;&#1257;&#1075;&#1078;&#1084;&#1080;&#1081;&#1085; &#1090;&#1086;&#1075;&#1083;&#1091;&#1091;&#1083;&#1072;&#1075;&#1095;
GenericName[ms]=Pemain Muzik
GenericName[nb]=Musikkavspiller
GenericName[ne]=&#2360;&#2306;&#2327;&#2367;&#2340; &#2346;&#2381;&#2354;&#2375;&#2351;&#2352;
GenericName[nl]=Muziekspeler
GenericName[no]=Musikkavspiller
GenericName[pa]=&#2616;&#2672;&#2583;&#2624;&#2596; &#2602;&#2610;&#2631;&#2565;&#2608;
GenericName[pl]=Odtwarzacz muzyczny
GenericName[pt]=Reprodutor de Música
GenericName[pt_BR]=Reprodutor de Música
GenericName[ro]=Player muzical
GenericName[ru]=&#1052;&#1091;&#1079;&#1099;&#1082;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; &#1087;&#1088;&#1086;&#1080;&#1075;&#1088;&#1099;&#1074;&#1072;&#1090;&#1077;&#1083;&#1100;
GenericName[sk]=Prehráva&#269; hudby
GenericName[sr]=&#1052;&#1091;&#1079;&#1080;&#1095;&#1082;&#1080; &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;
GenericName[sr@Latn]=Muzi&#269;ki program
GenericName[sv]=Musikspelare
GenericName[th]=&#3605;&#3633;&#3623;&#3648;&#3621;&#3656;&#3609;&#3648;&#3614;&#3621;&#3591;
GenericName[tr]=Müzik Çal&#305;c&#305;
GenericName[uk]=&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1074;&#1072;&#1095;
GenericName[vi]=B&#7897; phát nh&#7841;c
GenericName[zh_CN]=&#38899;&#20048;&#25773;&#25918;&#22120;
GenericName[zh_TW]=&#38899;&#27138;&#25773;&#25918;&#31243;&#24335;
Comment=Play and organize your music collection
Comment[ar]=&#1593;&#1586;&#1601; &#1608; &#1578;&#1606;&#1592;&#1610;&#1605; &#1605;&#1580;&#1605;&#1608;&#1593;&#1578;&#1603; &#1575;&#1604;&#1605;&#1608;&#1587;&#1610;&#1602;&#1610;&#1577;
Comment[az]=Musiqi kolleksiyan&#305;z&#305; t&#601;rtib edin v&#601; dinl&#601;yin
Comment[be]=&#1055;&#1088;&#1072;&#1081;&#1075;&#1088;&#1072;&#1077; &#1081; &#1082;&#1072;&#1090;&#1072;&#1083;&#1103;&#1075;&#1110;&#1079;&#1091;&#1077; &#1074;&#1072;&#1096;&#1099;&#1103; &#1084;&#1091;&#1079;&#1099;&#1095;&#1085;&#1099;&#1103; &#1082;&#1072;&#1083;&#1077;&#1082;&#1094;&#1099;&#1110;
Comment[bg]=&#1057;&#1083;&#1091;&#1096;&#1072;&#1085;&#1077; &#1080; &#1086;&#1088;&#1075;&#1072;&#1085;&#1080;&#1079;&#1080;&#1088;&#1072;&#1085;&#1077; &#1085;&#1072; &#1042;&#1072;&#1096;&#1072;&#1090;&#1072; &#1084;&#1091;&#1079;&#1080;&#1082;&#1072;&#1083;&#1085;&#1072; &#1082;&#1086;&#1083;&#1077;&#1082;&#1094;&#1080;&#1103;
Comment[ca]=Reproduïu i organitzeu la vostra col·lecció de música
Comment[cs]=P&#345;ehrávání a organizace va&#353;í sbírky hudby
Comment[cy]=Chwarae a threfni eich casgliad cerddoriaeth
Comment[da]=Afspil musik og organisèr din musiksamling
Comment[de]=Ihre Musiksammlung wiedergeben und organisieren
Comment[el]=&#928;&#945;&#943;&#958;&#964;&#949; &#954;&#945;&#953; &#959;&#961;&#947;&#945;&#957;&#974;&#963;&#964;&#949; &#964;&#951;&#957; &#956;&#959;&#965;&#963;&#953;&#954;&#942; &#963;&#945;&#962; &#963;&#965;&#955;&#955;&#959;&#947;&#942;
Comment[en_CA]=Play and organize your music collection
Comment[en_GB]=Play and organise your music collection
Comment[es]=Organice y reproduzca su colección de música
Comment[et]=Mängi ja halda oma muusikakollektsiooni
Comment[eu]=Erreproduzitu eta antolatu musika bilduma
Comment[fi]=Soita ja järjestele musiikkikokoelmasi
Comment[fr]=Joue et organise votre collection musicale
Comment[ga]=Seinn agus eagraigh do chuid bailiú ceoil
Comment[gl]=Reproduce e organiza a súa colección de música
Comment[he]=&#1500;&#1504;&#1490;&#1497;&#1504;&#1492; &#1493;&#1488;&#1512;&#1490;&#1493;&#1503; &#1513;&#1500; &#1488;&#1493;&#1505;&#1507; &#1502;&#1493;&#1494;&#1497;&#1511;&#1492;
Comment[hr]=Organiziranje i sviranje va&#353;e glazbene zbirke
Comment[hu]=Zenék rendszerezése és lejátszása
Comment[id]=Putar dan atur koleksi musik
Comment[is]=Spila og sjá um tónlistarsafnið þitt
Comment[it]=Riproduce ed organizza la collezione musicale
Comment[ja]=&#12362;&#27671;&#12395;&#20837;&#12426;&#12398;&#27005;&#26354;&#12467;&#12524;&#12463;&#12471;&#12519;&#12531;&#12434;&#20877;&#29983;&#12375;&#12383;&#12426;&#31649;&#29702;&#12375;&#12414;&#12377;
Comment[ko]=&#51020;&#50501; &#47784;&#51020;&#51012; &#50672;&#51452;&#54616;&#44256; &#51221;&#47532;&#54633;&#45768;&#45796;
Comment[lt]=Grokite ir tvarkykite savo muzikos kolekcij&#261;
Comment[lv]=Atska&#326;o un organiz&#275; savu m&#363;zikas kolekciju
Comment[mk]=&#1057;&#1074;&#1080;&#1088;&#1080; &#1080; &#1086;&#1088;&#1075;&#1072;&#1085;&#1080;&#1079;&#1080;&#1088;&#1072;&#1112; &#1112;&#1072; &#1090;&#1074;&#1086;&#1112;&#1072;&#1090;&#1072; &#1084;&#1091;&#1079;&#1080;&#1095;&#1082;&#1072; &#1082;&#1086;&#1083;&#1077;&#1082;&#1094;&#1080;&#1112;&#1072;
Comment[mn]=&#1061;&#1257;&#1075;&#1078;&#1084;&#1080;&#1081;&#1085; &#1094;&#1091;&#1075;&#1083;&#1091;&#1091;&#1083;&#1075;&#1072;&#1072; &#1090;&#1086;&#1075;&#1083;&#1091;&#1091;&#1083;&#1078;, &#1079;&#1086;&#1093;&#1080;&#1086;&#1085; &#1073;&#1072;&#1081;&#1075;&#1091;&#1091;&#1083;
Comment[ms]=Mian dan pelihara koleksi muzik anda
Comment[nb]=Spill av og organiser din musikksamling
Comment[ne]=&#2340;&#2346;&#2366;&#2312;&#2306;&#2325;&#2379; &#2360;&#2306;&#2327;&#2367;&#2340; &#2360;&#2306;&#2325;&#2354;&#2344; &#2346;&#2381;&#2354;&#2375; &#2327;&#2352;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360; &#2352; &#2310;&#2351;&#2379;&#2332;&#2344; &#2327;&#2352;&#2381;&#2344;&#2369;&#2361;&#2379;&#2360;
Comment[nl]=Uw muziekcollectie beluisteren en beheren
Comment[no]=Spill av og organiser din musikksamling
Comment[pa]=&#2566;&#2602;&#2595;&#2624; &#2616;&#2672;&#2583;&#2624;&#2596; &#2602;&#2616;&#2672;&#2598; &#2586;&#2610;&#2622;&#2569; &#2565;&#2596;&#2631; &#2616;&#2672;&#2605;&#2622;&#2610;&#2635;
Comment[pl]=Odtwarzanie i organizowanie twojej kolekcji muzycznej
Comment[pt]=Reproduza e organize a sua colecção de música
Comment[pt_BR]=Reproduzir e organizar a sua coleção de músicas
Comment[ro]=Red&#259; &#351;i organizeaz&#259; colec&#355;ia dumneavoastr&#259; de melodii
Comment[ru]=&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;&#1072; &#1074;&#1086;&#1089;&#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1077;&#1076;&#1077;&#1085;&#1080;&#1103; &#1080; &#1091;&#1087;&#1088;&#1072;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103; &#1074;&#1072;&#1096;&#1077;&#1081; &#1084;&#1091;&#1079;&#1099;&#1082;&#1072;&#1083;&#1100;&#1085;&#1086;&#1081; &#1082;&#1086;&#1083;&#1083;&#1077;&#1082;&#1094;&#1080;&#1077;&#1081;.Comment[sk]=Prehráva&#357; a organizova&#357; Va&#353;u zbierku hudby
Comment[sr]=&#1054;&#1088;&#1075;&#1072;&#1085;&#1080;&#1079;&#1091;&#1112; &#1080; &#1080;&#1079;&#1074;&#1086;&#1076;&#1080; &#1089;&#1074;&#1086;&#1112;&#1091; &#1084;&#1091;&#1079;&#1080;&#1095;&#1082;&#1091; &#1079;&#1073;&#1080;&#1088;&#1082;&#1091;
Comment[sr@Latn]=Organizuj i izvodi svoju muzi&#269;ku zbirku
Comment[sv]=Spela och organisera din musiksamling
Comment[th]=&#3648;&#3621;&#3656;&#3609;&#3649;&#3621;&#3632;&#3592;&#3633;&#3604;&#3585;&#3634;&#3619;&#3585;&#3633;&#3610;&#3648;&#3614;&#3621;&#3591;&#3586;&#3629;&#3591;&#3588;&#3640;&#3603;
Comment[tr]=Müzik koleksiyonunuzu çal&#305;n ve yönetin
Comment[uk]=&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1074;&#1072;&#1085;&#1085;&#1103; &#1090;&#1072; &#1091;&#1087;&#1086;&#1088;&#1103;&#1076;&#1082;&#1091;&#1074;&#1072;&#1085;&#1085;&#1103; &#1079;&#1073;&#1110;&#1088;&#1082;&#1080; &#1084;&#1091;&#1079;&#1080;&#1095;&#1085;&#1080;&#1093; &#1090;&#1074;&#1086;&#1088;&#1110;&#1074;
Comment[vi]=Phát nh&#7841;c và t&#7893; ch&#7913;c các t&#7853;p nh&#7841;c c&#7911;a b&#7841;n.
Comment[zh_CN]=&#25773;&#25918;&#21644;&#32452;&#32455;&#24744;&#30340;&#38899;&#20048;&#25910;&#34255;
Comment[zh_TW]=&#25773;&#25918;&#21450;&#31649;&#29702;&#38899;&#27138;&#24235;
Exec=rhythmbox
Terminal=false
**Type=Application**
Icon=rhythmbox.png
X-GNOME-DocPath=rhythmbox/rhythmbox.xml
**Categories=GNOME;GTK;Application;AudioVideo**;X-Ximian-Main;X-Red-Hat-Base;
MimeType=application/x-ogg;application/ogg;audio/x-mp3;audio/x-scpls;audio/x-mp3;audio/x-mpeg;audio/mpeg;audio/x-mpegurl;application/x-flac
StartupNotify=true
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=rhythmbox
X-GNOME-Bugzilla-Component=general
X-Ubuntu-Gettext-Domain=rhythmbox
```

---

### Post by mlind on 2006-07-27
Most important difference between the .desktop file you posted and original rhythmbox.desktop is that orginal has
```

Icon=rhythmbox

```

Other differences are just few translations.

---

### Post by aysiu on 2006-07-27
> **mlind said:**
> Most important difference between the .desktop file you posted and original rhythmbox.desktop is that orginal has
```

Icon=rhythmbox

```

Other differences are just few translations.
I haven't modified the rhythmbox.desktop file. That is the original one.

---

### Post by z3r0-c0d3r on 2006-07-27
You have to put the .desktop file in /usr/share/applications

the format is

[Desktop Entry]
Encoding=UTF-8
Name=*Name of application*
Exec=*The command to run*
Icon=*Icon*
Info=*Extra info*
Categories=*Where the entry should be eg: under Internet in the applications menu is : Application;Network;*
Comment=*Comment*
Terminal=*Load with terminal or not, true or false*
Type=Application
StartupNotify=true

If you are unsure of categories here are a few:
Accessibility: Application;Accessibility;
Accessories: Application;Utility;
Games: Application;Game;
Graphics: Application;Graphics;
Internet: Application;Network;
Office: Application;Office;
Sounds & Video: Application;AudioVideo
System Tools: Application;System;

---

### Post by mlind on 2006-07-27
> **aysiu said:**
> I haven't modified the rhythmbox.desktop file. That is the original one.

Oops, I though JKing posted that .desktop file :rolleyes: 
Well, my rhythmbox .desktop file is not same as yours, but that's another story.

---

### Post by JKing on 2006-07-27
Here's the script I use to create the item:

```

wget -nc http://www.kde-look.org/content/files/12262-zsnes.zip
unzip -j 12262-zsnes.zip "home/tris/zsnes/zsens icon" -d ~/
echo "[Desktop Entry]" >> zsnes.desktop
echo "Type=Application" >> zsnes.desktop
echo "Encoding=UTF-8" >> zsnes.desktop
echo "Name=ZSNES" >> zsnes.desktop
echo "GenericName=SNES emulator" >> zsnes.desktop
echo "Exec=zsnes" >> zsnes.desktop
echo "Icon=/usr/share/icons/zsnes.png" >> zsnes.desktop
echo "Terminal=false" >> zsnes.desktop
echo "Categories=Game;" >> zsnes.desktop
echo "StartupNotify=false" >> zsnes.desktop
sudo mv "zsens icon" /usr/share/icons/zsnes.png
sudo mv zsnes.desktop /usr/share/applications/
rm 12262-zsnes.zip

```

I will have a look at /etc/xdg/menus/ as someone suggested; I tried to find where the XDG data files were stores earlier, but didnt think of looking there.  Perhaps there's something that changed in the files when I used Alacrate to do some clean-up.

---

### Post by JKing on 2006-07-27
Ah, now it's working all of a sudden!
Oh, well.  Thanks for the help and attention, everyone. :)

---

