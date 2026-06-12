---
title: "KDE Control Centre"
date: 2005-11-23
forum: Desktop Environments
---

### Post by ace2005 on 2005-11-23
Its arranged in a way i'm not used to, how do i change it so that it has a tree like thing on the left?

Make it look like what it looks like when i do sudo kcontrol

---

### Post by daller on 2005-11-23
I think the only thing you can do, is to change the path to system settings, so that it just opens kcontrol instead!

...according to "man systemsettings", there is no such argument!

---

### Post by apokryphos on 2005-11-23
If you really want to use the old kcontrol, then you can always just alt+F2 -> kcontrol.

---

### Post by ace2005 on 2005-11-23
[QUOTE=apokryphos]If you really want to use the old kcontrol, then you can always just alt+F2 -> kcontrol.[/QUOTE]


Thanks, thats a lot better

How come its changed??? Did the people who make Kubuntu do it??? or is it being introduced into KDE from now on????

---

### Post by ykpaiha on 2005-11-23
a way I turned this was to copy a link on your desktop 
in /usr/share/apps/systemview/
add a file call setting.desktop
copy and past the following:
```

[Desktop Entry]
Encoding=UTF-8
Type=Link
URL=settings:/
Icon=kcontrol
Name=Settings
Name[af]=Instellings
Name[ar]=&#1575;&#1604;&#1573;&#1593;&#1583;&#1575;&#1583;&#1575;&#1578;
Name[az]=Qur&#287;ular
Name[be]=&#1053;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1110;
Name[bg]=&#1053;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1080;
Name[bn]=&#2488;&#2503;&#2463;&#2495;&#2434;&#2488;
Name[br]=Dibarzho&#249;
Name[bs]=Postavke
Name[ca]=Prefer&#232;ncies
Name[cs]=Nastaven&#237;
Name[cy]=Gosodiadau
Name[da]=Ops&#230;tning
Name[de]=Einstellungen
Name[el]=&#929;&#965;&#952;&#956;&#943;&#963;&#949;&#953;&#962;
Name[eo]=Agordo
Name[es]=Preferencias
Name[et]=Seadistused
Name[eu]=Ezarpenak
Name[fi]=Asetukset
Name[fr]=Configuration
Name[fy]=Ynstellings
Name[ga]=Socruithe
Name[gl]=Opci&#243;ns
Name[he]=&#1492;&#1490;&#1491;&#1512;&#1493;&#1514;
Name[hi]=&#2357;&#2367;&#2344;&#2381;&#2351;&#2366;&#2360;
Name[hr]=Postavke
Name[hsb]=Nastajenja
Name[hu]=Be&#225;ll&#237;t&#225;sok
Name[is]=Stillingar
Name[it]=Impostazioni
Name[ja]=&#35373;&#23450;
Name[ko]=&#49444;&#51221;
Name[lt]=Parinktys
Name[mk]=&#1055;&#1086;&#1089;&#1090;&#1072;&#1074;&#1091;&#1074;&#1072;&#1114;&#1072;
Name[mn]=&#1058;&#1086;&#1093;&#1080;&#1088;&#1091;&#1091;&#1083;&#1075;&#1072;
Name[ms]=Tempatan
Name[nb]=Innstillinger
Name[nds]=Instellen
Name[nl]=Instellingen
Name[nn]=Innstillingar
Name[pa]=&#2613;&#2623;&#2613;&#2616;&#2597;&#2622;
Name[pl]=Ustawienia
Name[pt]=Prefer&#234;ncias
Name[pt_BR]=Configura&#231;&#245;es
Name[ro]=Set&#259;ri
Name[ru]=&#1053;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1072;
Name[se]=Heivehusat
Name[sk]=Nastavenia
Name[sl]=Nastavitve
Name[sr]=&#1055;&#1086;&#1089;&#1090;&#1072;&#1074;&#1082;&#1077;
Name[sr@Latn]=Postavke
Name[sv]=Inst&#228;llningar
Name[ta]=&#2949;&#2990;&#3016;&#2986;&#3021;&#2986;&#3009;&#2965;&#2995;&#3021;
Name[tg]=&#1058;&#1072;&#1085;&#1079;&#1080;&#1084;&#1086;&#1090;
Name[th]=&#3605;&#3633;&#3657;&#3591;&#3588;&#3656;&#3634;
Name[tr]=Ayarlar
Name[uk]=&#1059;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1080;
Name[uz]=&#1052;&#1086;&#1089;&#1083;&#1072;&#1084;&#1072;&#1083;&#1072;&#1088;
Name[vi]=Thi&#7871;t l&#7853;p
Name[wa]=Apontiaedjes
Name[zh_CN]=&#35774;&#32622;
Open=false
X-KDE-TreeModule=Directory
X-KDE-KonqSidebarModule=konqsidebar_tree

```
save it 
now on your panel you will get a setting icon under home and so on...
an other way is as well to copy it on your desktop (I use this way, the full folder ) and rename it as you wish (mine is called workshop)
you will easely access all your home and hd strait from there.

---

### Post by kairu0 on 2005-11-23
[QUOTE=ace2005]
How come its changed??? Did the people who make Kubuntu do it??? or is it being introduced into KDE from now on????[/QUOTE]

Unless I'm mistaken it's a Kubuntu thing. I don't think it's included in the KDE of other distributions.

Personally, I prefer kcontrol because it puts everything in a single window. By the way, don't make the mistake of running "sudo kcontrol."

---

