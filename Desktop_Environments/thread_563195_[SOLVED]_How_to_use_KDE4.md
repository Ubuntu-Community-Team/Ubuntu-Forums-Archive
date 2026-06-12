---
title: "[SOLVED] How to use KDE4"
date: 2007-09-29
forum: Desktop Environments
---

### Post by lunamystry on 2007-09-29
I am just looking to make my computer freeze before the final release of Gutsy. Now I wanna try out KDE4 but I dont really understand the instructions given on the Kubuntu site. 

> To run it as a full session copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop, edit the Name entry in kde4.desktop to be called "KDE 4", put the four export lines at the top of /usr/lib/kde4/bin/startkde and start a new session in KDM with KDE 4.

I want to run KDE4 but i am not really sure what that means. Both the directories given have kde.desktop so I am guessing I have to rename the one I am copying to something else but what? 
I quoted the above from
[INDENT][http://kubuntu.org/announcements/kde4-beta2.php](http://kubuntu.org/announcements/kde4-beta2.php)[/INDENT]

---

### Post by miggols99 on 2007-09-29
Copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop and edit the name entry to be KDE 4.

Put these lines at the top:

export LD_LIBRARY_PATH=/usr/lib/kde4/lib
export KDEDIRS=/usr/lib/kde4
export PATH=/usr/lib/kde4/bin/:$PATH
export KDEHOME=~/.kde4

below

/usr/lib/kde4/bin/startkde

Then log out and choose KDE 4 in KDM...I recommend that you wait a week for the beta 3 to come out..it will be much more usable.

---

### Post by lunamystry on 2007-09-29
> **miggols99 said:**
> Copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop and edit the name entry to be KDE 4.

Put these lines at the top:

export LD_LIBRARY_PATH=/usr/lib/kde4/lib
export KDEDIRS=/usr/lib/kde4
export PATH=/usr/lib/kde4/bin/:$PATH
export KDEHOME=~/.kde4

below

/usr/lib/kde4/bin/startkde



Put the line at the top of what? and below what? :(

Oh in three weeks I'll probably not have internet to download all these things so i am enjoying myself with all the eyecandy i can find. COMPIZ is the best!

---

### Post by lunamystry on 2007-09-29
```
export LD_LIBRARY_PATH=/usr/lib/kde4/lib
export KDEDIRS=/usr/lib/kde4
export PATH=/usr/lib/kde4/bin/:$PATH
export KDEHOME=~/.kde4
[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=/usr/lib/kde4/bin/startkde
TryExec=/usr/lib/kde4/bin/startkde
Name=KDE
Name[hi]=&#2325;&#2375;&#2337;&#2368;&#2312;
Name[mn]=&#1050;&#1044;&#1069;
Name[ta]=K&#2959;&#2993;&#3021;&#2993;&#2965;&#3021; &#2965;&#3006;&#2997;&#2994;&#2985;&#3021;
Name[xh]=iKDE
Name[xx]=xxKDExx
Comment=The K Desktop Environment. A powerful Open Source graphical desktop environment
Comment[bs]=K Desktop Environment. Mo&#263;an grafi&#269;ki desktop otvorenog izvornog koda
Comment[ca]=L'entorn d'escriptori K. Un poderós entorn d'escriptori gràfic de Codi Font Obert
Comment[cy]=Yr Amgylchedd Penbwrdd K.  Amgylchedd penbwrdd graffegol pwerus, sy'n gôd-agored.
Comment[da]=K Skrivebordsmiljøet. Et kraftigt, åbent, grafisk skrivebordsmiljø
Comment[de]=Das K Desktop Environment. Eine mächtige, graphische Arbeitsumgebung und Open Source / Freie Software
Comment[el]=&#932;&#959; K Desktop Environment. &#904;&#957;&#945; &#960;&#945;&#957;&#943;&#963;&#967;&#965;&#961;&#959; &#949;&#955;&#949;&#973;&#952;&#949;&#961;&#951;&#962; &#960;&#961;&#959;&#941;&#955;&#949;&#965;&#963;&#951;&#962; &#947;&#961;&#945;&#966;&#953;&#954;&#972; &#960;&#949;&#961;&#953;&#946;&#940;&#955;&#955;&#959;&#957; &#949;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945;&#962; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;
Comment[es]=El Entorno de Escritorio K, un potente entorno de escritorio gráfico realizado de código abierto
Comment[et]=K töölaua keskkond on võimas vaba tarkvara graafiline töölaua keskkond
Comment[fi]=KDE-työpöytäympäristö (K Desktop Environment) on tehokas avoimen lähdekoodin graafinen työpöytäympäristö
Comment[fr]=The K Desktop Environment. Un environnement de bureau graphique, puissant et Open Source
Comment[he]=The K Desktop Environment. &#1505;&#1489;&#1497;&#1489;&#1514; &#1506;&#1489;&#1493;&#1491;&#1492; &#1490;&#1512;&#1508;&#1497;&#1514;, &#1489;&#1506;&#1500;&#1514;-&#1506;&#1493;&#1510;&#1502;&#1492; &#1489;&#1511;&#1493;&#1491; &#1508;&#1514;&#1493;&#1495;
Comment[hi]=&#2325;&#2375; &#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2377;&#2346; &#2357;&#2366;&#2340;&#2366;&#2357;&#2352;&#2339;. &#2319;&#2325; &#2358;&#2325;&#2381;&#2340;&#2367;&#2358;&#2366;&#2354;&#2368;, &#2323;&#2346;&#2344; &#2360;&#2379;&#2352;&#2381;&#2360; &#2330;&#2367;&#2340;&#2381;&#2352;&#2350;&#2351; &#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2377;&#2346; &#2357;&#2366;&#2340;&#2366;&#2357;&#2352;&#2339;
Comment[hu]=A KDE grafikus munkakörnyezet, egy szabad forráskódú grafikus ablakkezel&#337; környezet
Comment[it]=L'ambiente desktop KDE. Un potente ambiente desktop grafico Open Source
Comment[mn]=The K Desktop Environment. &#1061;&#1199;&#1095;&#1080;&#1088;&#1093;&#1101;&#1075; &#1085;&#1101;&#1101;&#1083;&#1090;&#1090;&#1101;&#1081; &#1101;&#1093; &#1082;&#1086;&#1076; &#1073;&#1199;&#1093;&#1080;&#1081; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082; &#1076;&#1101;&#1083;&#1075;&#1101;&#1094;&#1080;&#1081;&#1085; &#1086;&#1088;&#1095;&#1080;&#1085;
Comment[nb]=K Desktop Environment. Et kraftig grafisk skrivebordsmiljø med åpen kildekode.
Comment[nl]=De K Desktop Environment, een krachtige open source grafische desktop environment
Comment[nn]=K Desktop Environment. Eit kraftig grafisk skrivebordsmiljø med open kjeldekode.
Comment[pl]=&#346;rodowisko KDE. Pot&#281;&#380;ne &#347;rodowisko graficzne Wolnego Oprogramowania.
Comment[pt]=O K Desktop Environment. Um ambiente gráfico open source poderoso
Comment[pt_BR]=Acrônimo para K Desktop Environment (ou Ambiente de Trabalho K). Um poderoso ambiente de trabalho gráfico de código aberto
Comment[ro]=K Desktop Environment. Un mediu grafic cu surse deschise, foarte puternic
Comment[sk]=The K Desktop Environment. Výkonné, vo&#318;ne šírite&#318;né grafické pracovné prostredie
Comment[sl]=Namizno okolje K. Zmogljivo grafi&#269;no namizno okolje odprte kode
Comment[sr]=K Desktop Environment (KDE). &#1052;&#1086;&#1115;&#1085;&#1086; &#1075;&#1088;&#1072;&#1092;&#1080;&#1095;&#1082;&#1086; &#1088;&#1072;&#1076;&#1085;&#1086; &#1086;&#1082;&#1088;&#1091;&#1078;&#1077;&#1114;&#1077; &#1086;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;&#1086;&#1075; &#1082;&#1086;&#1076;&#1072;
Comment[sv]=K-skrivbordsmiljön. En kraftfull grafisk skrivbordsmiljö med öppen källkod
Comment[ta]= K&#2990;&#3015;&#2994;&#3021;&#2990;&#3015;&#2970;&#3016; &#2970;&#3010;&#2996;&#2994;&#3021;. &#2970;&#2965;&#3021;&#2980;&#3007;&#2997;&#3006;&#2991;&#3021;&#2984;&#3021;&#2980; &#2980;&#3007;&#2993;&#2984;&#3021;&#2980; &#2950;&#2979;&#3016;&#2990;&#3010;&#2994; &#2970;&#3007;&#2980;&#3021;&#2980;&#3007;&#2992; &#2997;&#2965;&#3016; &#2990;&#3015;&#2994;&#3021;&#2990;&#3015;&#2970;&#3016; &#2970;&#3010;&#2996;&#2994;&#3021;
Comment[tr]=KDE Masaüstü Yöneticisi. Güçlü bir grafiksel masaüstü ortam&#305;
Comment[uk]=The K Desktop Environment. &#1055;&#1086;&#1090;&#1091;&#1078;&#1085;&#1077; &#1075;&#1088;&#1072;&#1092;&#1110;&#1095;&#1085;&#1077; &#1089;&#1077;&#1088;&#1077;&#1076;&#1086;&#1074;&#1080;&#1097;&#1077; &#1079; &#1074;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080;&#1084;&#1080; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;&#1084;&#1080;
Comment[uz]=KDE (K Desktop Environment) - &#1082;&#1091;&#1095;&#1083;&#1080; Open Source &#1075;&#1088;&#1072;&#1092;&#1080;&#1082; &#1080;&#1096; &#1089;&#1090;&#1086;&#1083;&#1080; &#1084;&#1091;&#1203;&#1080;&#1090;&#1080;
Comment[vi]=môi tr&#432;&#7901;ng desktop K, môi tr&#432;&#7901;ng desktop &#273;&#7891; ho&#7841; mã ngu&#7891;n m&#7903; r&#7845;t m&#7841;nh
Comment[xx]=xxThe K Desktop Environment. A powerful Open Source graphical desktop environmentxx
Comment[zh_CN]=K &#26700;&#38754;&#29615;&#22659;&#12290;&#24378;&#22823;&#30340;&#24320;&#25918;&#28304;&#20195;&#30721;&#22270;&#24418;&#26700;&#38754;&#29615;&#22659;
usr/lib/kde4/bin/startkdeexport LD_LIBRARY_PATH=/usr/lib/kde4/lib
export KDEDIRS=/usr/lib/kde4
export PATH=/usr/lib/kde4/bin/:$PATH
export KDEHOME=~/.kde4
[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=/usr/lib/kde4/bin/startkde
TryExec=/usr/lib/kde4/bin/startkde
Name=KDE
Name[hi]=&#2325;&#2375;&#2337;&#2368;&#2312;
Name[mn]=&#1050;&#1044;&#1069;
Name[ta]=K&#2959;&#2993;&#3021;&#2993;&#2965;&#3021; &#2965;&#3006;&#2997;&#2994;&#2985;&#3021;
Name[xh]=iKDE
Name[xx]=xxKDExx
Comment=The K Desktop Environment. A powerful Open Source graphical desktop environment
Comment[bs]=K Desktop Environment. Mo&#263;an grafi&#269;ki desktop otvorenog izvornog koda
Comment[ca]=L'entorn d'escriptori K. Un poderós entorn d'escriptori gràfic de Codi Font Obert
Comment[cy]=Yr Amgylchedd Penbwrdd K.  Amgylchedd penbwrdd graffegol pwerus, sy'n gôd-agored.
Comment[da]=K Skrivebordsmiljøet. Et kraftigt, åbent, grafisk skrivebordsmiljø
Comment[de]=Das K Desktop Environment. Eine mächtige, graphische Arbeitsumgebung und Open Source / Freie Software
Comment[el]=&#932;&#959; K Desktop Environment. &#904;&#957;&#945; &#960;&#945;&#957;&#943;&#963;&#967;&#965;&#961;&#959; &#949;&#955;&#949;&#973;&#952;&#949;&#961;&#951;&#962; &#960;&#961;&#959;&#941;&#955;&#949;&#965;&#963;&#951;&#962; &#947;&#961;&#945;&#966;&#953;&#954;&#972; &#960;&#949;&#961;&#953;&#946;&#940;&#955;&#955;&#959;&#957; &#949;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945;&#962; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;
Comment[es]=El Entorno de Escritorio K, un potente entorno de escritorio gráfico realizado de código abierto
Comment[et]=K töölaua keskkond on võimas vaba tarkvara graafiline töölaua keskkond
Comment[fi]=KDE-työpöytäympäristö (K Desktop Environment) on tehokas avoimen lähdekoodin graafinen työpöytäympäristö
Comment[fr]=The K Desktop Environment. Un environnement de bureau graphique, puissant et Open Source
Comment[he]=The K Desktop Environment. &#1505;&#1489;&#1497;&#1489;&#1514; &#1506;&#1489;&#1493;&#1491;&#1492; &#1490;&#1512;&#1508;&#1497;&#1514;, &#1489;&#1506;&#1500;&#1514;-&#1506;&#1493;&#1510;&#1502;&#1492; &#1489;&#1511;&#1493;&#1491; &#1508;&#1514;&#1493;&#1495;
Comment[hi]=&#2325;&#2375; &#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2377;&#2346; &#2357;&#2366;&#2340;&#2366;&#2357;&#2352;&#2339;. &#2319;&#2325; &#2358;&#2325;&#2381;&#2340;&#2367;&#2358;&#2366;&#2354;&#2368;, &#2323;&#2346;&#2344; &#2360;&#2379;&#2352;&#2381;&#2360; &#2330;&#2367;&#2340;&#2381;&#2352;&#2350;&#2351; &#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2377;&#2346; &#2357;&#2366;&#2340;&#2366;&#2357;&#2352;&#2339;
Comment[hu]=A KDE grafikus munkakörnyezet, egy szabad forráskódú grafikus ablakkezel&#337; környezet
Comment[it]=L'ambiente desktop KDE. Un potente ambiente desktop grafico Open Source
Comment[mn]=The K Desktop Environment. &#1061;&#1199;&#1095;&#1080;&#1088;&#1093;&#1101;&#1075; &#1085;&#1101;&#1101;&#1083;&#1090;&#1090;&#1101;&#1081; &#1101;&#1093; &#1082;&#1086;&#1076; &#1073;&#1199;&#1093;&#1080;&#1081; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082; &#1076;&#1101;&#1083;&#1075;&#1101;&#1094;&#1080;&#1081;&#1085; &#1086;&#1088;&#1095;&#1080;&#1085;
Comment[nb]=K Desktop Environment. Et kraftig grafisk skrivebordsmiljø med åpen kildekode.
Comment[nl]=De K Desktop Environment, een krachtige open source grafische desktop environment
Comment[nn]=K Desktop Environment. Eit kraftig grafisk skrivebordsmiljø med open kjeldekode.
Comment[pl]=&#346;rodowisko KDE. Pot&#281;&#380;ne &#347;rodowisko graficzne Wolnego Oprogramowania.
Comment[pt]=O K Desktop Environment. Um ambiente gráfico open source poderoso
Comment[pt_BR]=Acrônimo para K Desktop Environment (ou Ambiente de Trabalho K). Um poderoso ambiente de trabalho gráfico de código aberto
Comment[ro]=K Desktop Environment. Un mediu grafic cu surse deschise, foarte puternic
Comment[sk]=The K Desktop Environment. Výkonné, vo&#318;ne šírite&#318;né grafické pracovné prostredie
Comment[sl]=Namizno okolje K. Zmogljivo grafi&#269;no namizno okolje odprte kode
Comment[sr]=K Desktop Environment (KDE). &#1052;&#1086;&#1115;&#1085;&#1086; &#1075;&#1088;&#1072;&#1092;&#1080;&#1095;&#1082;&#1086; &#1088;&#1072;&#1076;&#1085;&#1086; &#1086;&#1082;&#1088;&#1091;&#1078;&#1077;&#1114;&#1077; &#1086;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;&#1086;&#1075; &#1082;&#1086;&#1076;&#1072;
Comment[sv]=K-skrivbordsmiljön. En kraftfull grafisk skrivbordsmiljö med öppen källkod
Comment[ta]= K&#2990;&#3015;&#2994;&#3021;&#2990;&#3015;&#2970;&#3016; &#2970;&#3010;&#2996;&#2994;&#3021;. &#2970;&#2965;&#3021;&#2980;&#3007;&#2997;&#3006;&#2991;&#3021;&#2984;&#3021;&#2980; &#2980;&#3007;&#2993;&#2984;&#3021;&#2980; &#2950;&#2979;&#3016;&#2990;&#3010;&#2994; &#2970;&#3007;&#2980;&#3021;&#2980;&#3007;&#2992; &#2997;&#2965;&#3016; &#2990;&#3015;&#2994;&#3021;&#2990;&#3015;&#2970;&#3016; &#2970;&#3010;&#2996;&#2994;&#3021;
Comment[tr]=KDE Masaüstü Yöneticisi. Güçlü bir grafiksel masaüstü ortam&#305;
Comment[uk]=The K Desktop Environment. &#1055;&#1086;&#1090;&#1091;&#1078;&#1085;&#1077; &#1075;&#1088;&#1072;&#1092;&#1110;&#1095;&#1085;&#1077; &#1089;&#1077;&#1088;&#1077;&#1076;&#1086;&#1074;&#1080;&#1097;&#1077; &#1079; &#1074;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080;&#1084;&#1080; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;&#1084;&#1080;
Comment[uz]=KDE (K Desktop Environment) - &#1082;&#1091;&#1095;&#1083;&#1080; Open Source &#1075;&#1088;&#1072;&#1092;&#1080;&#1082; &#1080;&#1096; &#1089;&#1090;&#1086;&#1083;&#1080; &#1084;&#1091;&#1203;&#1080;&#1090;&#1080;
Comment[vi]=môi tr&#432;&#7901;ng desktop K, môi tr&#432;&#7901;ng desktop &#273;&#7891; ho&#7841; mã ngu&#7891;n m&#7903; r&#7845;t m&#7841;nh
Comment[xx]=xxThe K Desktop Environment. A powerful Open Source graphical desktop environmentxx
Comment[zh_CN]=K &#26700;&#38754;&#29615;&#22659;&#12290;&#24378;&#22823;&#30340;&#24320;&#25918;&#28304;&#20195;&#30721;&#22270;&#24418;&#26700;&#38754;&#29615;&#22659;
usr/lib/kde4/bin/startkde
```

Is that right?

---

### Post by lunamystry on 2007-09-30
May someone please help he run KDE4. I just have to see all those things it has. I first thought it was just Hype and nothing big was there but I tried to run plasma and it looks awesome but nothing happens it just gives a new wallpaper and I think a menu but i can't do anything with it. 

I followed the instructions from Kubuntu.org best I could but It still does not show at the start of kdm.

---

### Post by GeneralZod on 2007-09-30
Plasma was completely broken in the Beta 2 (Beta 2 was basically a huge waste of time), so that's pretty much what it's (not) supposed to look like.

Beta 3 will be released soon and should hopefully be in better shape, but I'm not sure if it will arrive while you still have an Internet connection.

If you want to "try it out" properly, I'd personally wait until at least KDE4.0, and preferably 4.1 - it's going to be quite a long time before it's as usable as KDE3.x.y.

Note that you should be able to run apps by right-clicking on the desktop, choosing "Run Command" and typing the name of the executable.

> 
 I just have to see all those things it has


What kind of things are you expecting? Many of the proposed features aren't fully implemented yet, let alone integrated.  Many people seem to have some over-optimistic opinions on what KDE4.0 will be like :)

---

### Post by lunamystry on 2007-09-30
Not much i guess. Plasma the superkaramba 'replacement' the multimedia enviroment and whatever eyecandy comes with it. I hope it is possible to download it from a mswin computer and install it. 

Thank you anyway. I will just enjoy compiz. :):guitar:

---

### Post by lunamystry on 2007-09-30
Okay I think i just messed up my PC. I hope its not a gutsy problem because I like gutsy thus far. 
When i close a window i get this error
[INDENT]Unable to save bookmarks in /home/lunamystry/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.[/INDENT]

When i try to edit something that like settings I get this
[INDENT]Will not save configuration.
Configuration file "/home/lunamystry/.kde/share/config/kcmshellrc" not writable.
Please contact your system administrator.[/INDENT]

What does all this mean? I deleted the four lines that i wrote in the /usr/lib/kde4/bin/startkde and my gutsy login window is replaced with the KDE.

---

### Post by miggols99 on 2007-09-30
It looks like your home folder isn't writable. I think it's something like:

sudo chown <name of user>:<name of user> /home/<name of user>

---

### Post by lunamystry on 2007-09-30
What does chown do? increase my knowledge of Konsole a bit

---

### Post by Happy_Man on 2007-09-30
It's not Konsole, it's bash and the CLI he's increasing your knowledge of. Konsole is just a way to get to a CLI from within a GUI environment. <-- Fact 1

Chown changes ownership of a folder or file <-- Fact 2

Hope that helped!

---

### Post by lunamystry on 2007-09-30
It wasn't the problem. I did it but still nothing, I still get the error and i change and still cant' change settings. I think the problem lies with KDE i did something to it when installing kde4. 

Is there a way to revert back to the default settings of KDE?

Oh and thank you for the information.

---

### Post by GeneralZod on 2007-09-30
What is the output of 

```

ls -l /home/lunamystry/.kde/share/config/kcmshellrc

```

and

```

echo $KDEHOME

```

?

---

### Post by lunamystry on 2007-09-30
> **GeneralZod said:**
> What is the output of 

```

ls -l /home/lunamystry/.kde/share/config/kcmshellrc

```

and

```

echo $KDEHOME

```

?

```
lunamystry@michelle:~$ ls -l /home/lunamystry/.kde/share/config/kcmshellrc
-rw------- 1 root root 104 2007-09-30 18:32 /home/lunamystry/.kde/share/config/kcmshellrc
lunamystry@michelle:~$ echo $KDEHOME

lunamystry@michelle:~$

```

---

### Post by GeneralZod on 2007-09-30
For some reason, KDEHOME isn't being set when you are starting KDE4 (it should be set to ~/.kde4 so as not to overwrite your settings, stored in ~/.kde), and also something is setting things in ~/.kde to root ownership.

How are you starting KDE4? You should be starting it from KDM, having followed all of the steps in the Kubuntu guide.  You should definitely not run it as root.

When you did the "chown" thing that miggols59 suggested, what precisely did you type?

---

### Post by miggols99 on 2007-09-30
Sorry wrong thread :oops:

---

### Post by lunamystry on 2007-09-30
> **GeneralZod said:**
> For some reason, KDEHOME isn't being set when you are starting KDE4 (it should be set to ~/.kde4 so as not to overwrite your settings, stored in ~/.kde), and also something is setting things in ~/.kde to root ownership.

How are you starting KDE4? You should be starting it from KDM, having followed all of the steps in the Kubuntu guide.  You should definitely not run it as root.

When you did the "chown" thing that miggols59 suggested, what precisely did you type?

```
 sudo chown lunamystry:lunamystry /home/lunamystry

```That was what I typed to change home ownership. 

I used the instructions from the kubuntu site to install KDE4. 

And now I have  removed KDE4 and i deleted the  four migrate lines that I was suppose to add to the top of startkde and also the file that I copied. The problem started before I removed KDE4 though.

---

### Post by lunamystry on 2007-09-30
How do I undo this?

[INDENT]```
    * export LD_LIBRARY_PATH=/usr/lib/kde4/lib
    * export KDEDIRS=/usr/lib/kde4
    * export PATH=/usr/lib/kde4/bin/:$PATH
    * export KDEHOME=~/.kde4

```[/INDENT]

---

### Post by Happy_Man on 2007-10-01
Just log out, and log back in again, without somehow running those commands (either in startup or in Konsole). It should fix itself.

---

### Post by lunamystry on 2007-10-02
Well it hasn't I have been switching off my PC but it still gives me an error. I looked at the folder that had KDE4 in it and it has a file bin so I was thinking I may have moved the files that allow me to edit somewhere else with the above commands. 

Should I change every kde4 in the commands to kde3  what would that do? may someone explain what the commands mean to please.

Thank you

---

### Post by GeneralZod on 2007-10-02
> **lunamystry said:**
> Well it hasn't I have been switching off my PC but it still gives me an error. I looked at the folder that had KDE4 in it and it has a file bin so I was thinking I may have moved the files that allow me to edit somewhere else with the above commands. 


What error?

> 
Should I change every kde4 in the commands to kde3  what would that do?


Definitely not :)

> 
 may someone explain what the commands mean to please.


Which commands?

I'm sure this is all fixable, so relax and be patient :)

---

### Post by jamarsa on 2007-10-02
> **lunamystry said:**
> ```
 sudo chown lunamystry:lunamystry /home/lunamystry

``` sudo chown lunamystry:lunamystry /home/lunamystry

You should type:
 sudo chown **-R** lunamystry:lunamystry /home/lunamystry

This way, you will change **Recursively** ownership of all files hanging from your home folder, and not only the home folder. That is, including the file /home/lunamystry/.kde/share/config/kcmshellrc.

---

### Post by lunamystry on 2007-10-02
> **GeneralZod said:**
> What error?



Definitely not :)



Which commands?

I'm sure this is all fixable, so relax and be patient :)

I meant this error, WHICH IS NOW FIXED!!! >     Unable to save bookmarks in /home/lunamystry/.kde/share/apps/d3lphin/bookmarks .xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive.

Thank you.

---

### Post by lunamystry on 2007-10-02
> **jamarsa said:**
> You should type:
 sudo chown **-R** lunamystry:lunamystry /home/lunamystry

This way, you will change **Recursively** ownership of all files hanging from your home folder, and not only the home folder. That is, including the file /home/lunamystry/.kde/share/config/kcmshellrc.

Thank you for explaining the command as well.

---

