---
title: "no xfce session?"
date: 2005-06-09
forum: Desktop Environments
---

### Post by czynski on 2005-06-09
i installed xfce3x from ubuntu's apt-get repositories but it doesn't show up in my sessions list during login. how else could i start xfce? anyone else had this prob?

---

### Post by drummer on 2005-06-09
First of all, I'd install the xfce4 package, it's newer, better features, etc, etc, than version 3. When installing, it should automatically create a session option when logging in. If not, you can make one yourself by doing this from a terminal:
```
sudo gedit /usr/share/xsessions/xfce.desktop
```
then put the following into the new file and save.
```
[Desktop Entry]
Encoding=UTF-8
Name=Xfce Session
Comment=Use this session to run Xfce as your desktop environment
Exec=startxfce4
Icon=
Type=Application

```
This is what I have for my Xfce4 session (plus some other lines for other languages, but I think those can be safely left out). If you're using the older version I'm pretty sure that the Exec=startxfce4 can be just changed to Exec=startxfce .. I would reccomend the latest version of Xfce though.

The full version of my xfce.desktop file with other languages:
```
[Desktop Entry]
Encoding=UTF-8
# The names/descriptions should really be better
Name=Xfce Session
Name[fr]=Session Xfce
Name[et]=Xfce 4 sessioon
Name[fi]=Xfce 4 -istunto
Name[he]=Xfce 4
Name[ko]=Xfce 4 &#49464;&#49496;
Name[lt]=Xfce 4 sesija
Name[nl]=Xfce 4 Sessie
Name[ro]=Sesiune Xfce 4
Name[ru]=&#1057;&#1077;&#1072;&#1085;&#1089; Xfce 4
Name[zh_CN]=Xfce  &#20250;&#35805;
Name[sk]=Sedenie Xfce
Name[zh_TW]=Xfce 4 &#24037;&#20316;&#38542;&#27573;
Name[eu]=Xfce Saioa
Name[hu]=Xfce Folyamat
Comment=Use this session to run Xfce as your desktop environment
Comment[et]=kasuta seda sessiooni, et Xfce käivituks sinu töökeskkonnana
Comment[fi]=Valitse tämä istunto käyttääksesi Xfce:tä työpöytäympäristönäsi
Comment[fr]=Sélectionner cette session pour utiliser Xfce comme environnment graphique
Comment[he]=&#1492;&#1513;&#1514;&#1502;&#1513; &#1489;&#1494;&#1492; &#1499;&#1491;&#1497; &#1500;&#1492;&#1508;&#1506;&#1497;&#1500; &#1488;&#1514; Xfce &#1499;&#1513;&#1493;&#1500;&#1495;&#1503; &#1492;&#1506;&#1493;&#1489;&#1491;&#1492; &#1513;&#1500;&#1498;
Comment[ko]=&#49324;&#50857;&#51088; &#45936;&#49828;&#53356;&#53457; &#54872;&#44221;&#51004;&#47196; Xfce&#47484; &#51060;&#50857;&#54633;&#45768;&#45796;.
Comment[lt]=Pasirinkite ši&#261; sesij&#261;, nor&#279;dami patekti &#303; Xfce aplink&#261;
Comment[nl]=Deze optie start de Xfce 4 Desktop Environment
Comment[sk]=Použi&#357; toto sedenie k spusteniu Xfce ako vášho pracovného prostredia
Comment[ro]=Alege&#355;i aceast&#259; sesiune pentru a utiliza mediul desktop Xfce
Comment[ru]=&#1047;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072;&#1077;&#1090; &#1088;&#1072;&#1073;&#1086;&#1095;&#1091;&#1102; &#1089;&#1088;&#1077;&#1076;&#1091; Xfce 
Comment[zh_CN]=&#20351;&#29992;&#27492;&#20250;&#35805;&#26469;&#36816;&#34892; Xfce &#20316;&#20026;&#24744;&#30340;&#26700;&#38754;&#29615;&#22659;
Comment[zh_TW]=&#20351;&#29992;&#36889;&#20491;&#24037;&#20316;&#38542;&#27573;&#36617;&#20837; Xfce 4 &#20316;&#28858;&#24744;&#30340;&#26700;&#38754;&#29872;&#22659;
Comment[eu]=Erabili saioa hau Xfce idazmahai ingurunea erabiltzeko
Comment[hu]=Ezt a folyamatkezel&#337;t használd az Xfce munkakörnyezet használatához
Exec=startxfce4
Icon=
Type=Application

```

---

