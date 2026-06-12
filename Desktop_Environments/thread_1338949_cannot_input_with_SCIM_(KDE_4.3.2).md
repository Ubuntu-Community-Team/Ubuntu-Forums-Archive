---
title: "cannot input with SCIM (KDE 4.3.2)"
date: 2009-11-27
forum: Desktop Environments
---

### Post by dasan on 2009-11-27
Now i switched into karmic and everything is working fine except SCIM input,,
in all previous versions i was using SCIM for malayalam input and it was working fine for all the previous versions including 9.04.
but after installation in 9.10 it works only with firefox..
what should i do to get working ..

---

### Post by Zorael on 2009-11-27
Could you paste the output of the following terminal commands?
```
$ echo GTK: $GTK_IM_MODULE, Qt: $QT_IM_MODULE, XMOD: $XMODIFIERS
$ im-switch -l
$ ls -l /etc/alternatives/xinput*
```

---

### Post by dasan on 2009-11-27
*[COLOR="Blue"]GTK_IM_MODULE, Qt: $QT_IM_MODULE, XMOD: $XMODIFIERS[/COLOR]*
GTK: scim, Qt: scim, XMOD: @im=SCIM
*[COLOR="Blue"]im-switch -l[/COLOR]*
Your input method setup under en_IN locale as below.
=======================================================
The configuration "/home/anand/.xinput.d/en_IN" is defined as a link pointing to
scim-bridge
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - auto mode
 link currently points to default
default - priority 10
default-xim - priority 0
none - priority 0
Current `best' version is default.
/bin/ls: cannot access /etc/alternatives/xinput-lang_LANG: Too many levels of symbolic links
=======================================================
The available input method configuration files are:
bac-skim default default-xim none scim scim-bridge scim-immodule th-xim
=======================================================
[I][COLOR="Blue"]
/etc/alternatives/xinput*[/COLOR][/I]
lrwxrwxrwx 1 root root 31 2009-11-27 11:20 /etc/alternatives/xinput-all_ALL -> /etc/X11/xinit/xinput.d/default
lrwxrwxrwx 1 root root 35 2009-11-08 19:31 /etc/alternatives/xinput-ja_JP -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 35 2009-11-08 19:31 /etc/alternatives/xinput-ko_KR -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 34 2009-11-14 20:33 /etc/alternatives/xinput-lang_LANG -> /etc/alternatives/xinput-lang_LANG
lrwxrwxrwx 1 root root 30 2009-11-08 20:50 /etc/alternatives/xinput-th_TH -> /etc/X11/xinit/xinput.d/th-xim
lrwxrwxrwx 1 root root 35 2009-11-08 19:31 /etc/alternatives/xinput-zh_CN -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 35 2009-11-08 19:31 /etc/alternatives/xinput-zh_HK -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 35 2009-11-08 19:31 /etc/alternatives/xinput-zh_SG -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 root root 35 2009-11-08 19:31 /etc/alternatives/xinput-zh_TW -> /etc/X11/xinit/xinput.d/scim-bridge



I tried skim also but it also didn't work
thanks for your concern.........

---

### Post by Zorael on 2009-11-30
That looks like it should work, actually. The only thing I would try is to change to scim-bridge.

Could you paste your **/etc/X11/xinit/xinput.d/scim-bridge**?

---

### Post by dasan on 2009-12-01
[COLOR="Blue"]cat /etc/X11/xinit/xinput.d/scim-bridge[/COLOR]
XIM=SCIM
if [ -e /usr/bin/skim ]; then
    XIM_PROGRAM=" "
else
    XIM_PROGRAM=/usr/bin/scim
fi
XIM_ARGS="-d"
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt4/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
elif [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
else
    QT_IM_MODULE=xim
fi

DEPENDS="scim | skim, scim-bridge-agent, scim-bridge-client-gtk | scim-bridge-client-qt"


it was working fine in previous version of KDE 
Now it only works with firefox not even with open office...

---

### Post by dasan on 2009-12-01
After long google 
i got another which is coming with Kde, From regions and language after enabling the keyboard layout i can type in malayalam everywhere  but it support only inscript not phonetic it is very difficult to learn too 
is there any way with which i can insert this phonetic mozhi-ml there ?
I am getting these packages from [here]("http://malayalam.kerala.gov.in/index.php/EnableMalayalam")
After installation i used to update since those packets are for 8.04

---

### Post by Zorael on 2009-12-01
There's some inconsistency here, but perhaps you've been tinkering around inbetween posts.

With that scim-bridge file you posted, scim should work in all GTK (Firefox, Pidgin, ...) and Qt (everything KDE, smplayer, ...) apps, but *IF* you have Skim installed, it won't work in apps that rely on XIM for input (OpenOffice.org, xterm, ...). You don't even have to be using Skim, just have it installed and it won't set the correct variables. The rationale for making the file like this eludes me.

Backup your scim-bridge file and change it to look like this;
```
XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"

if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
elif [ -e /usr/lib/gtk-2.0/*/immodules/im-scim.so ]; then
    GTK_IM_MODULE=scim
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ] || [ -e /usr/lib/qt4/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
elif [ -e /usr/lib/qt3/plugins/inputmethods/libqscim.so ]; then
    QT_IM_MODULE=scim
else
    QT_IM_MODULE=xim
fi

DEPENDS="scim-bridge-client-gtk | scim-bridge-client-qt | scim-bridge-client-qt4 | scim-gtk2-immodule | scim-qtimm"
```
Now, provided that;
[list=1][*]You have the necessary scim and scim-bridge packages installed, such as by doing '**sudo aptitude install scim ~nscim-bridge**'
[list][*]While optional, you also have the necessary scim language module added, such as **scim-anthy** for Japanese, **scim-pinyin**, **scim-thai**, etc[/list]
[*]You have modified the **/etc/X11/xinit/xinput.d/scim-bridge** file to look as above
[*]You have set either your user input method or the system-wide default input method to **scim-bridge** via '**im-switch -c**'
[*]You have applied the settings by restarting your X session, such as by rebooting[/list]
...everything should work.

*After* having restarted, this command should output the following.
```
$ grep XIM /etc/X11/xinit/xinput.d/scim-bridge; echo GTK: $GTK_IM_MODULE, Qt: $QT_IM_MODULE, XMOD: $XMODIFIERS
[COLOR="Green"][B]XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
GTK: scim-bridge, Qt: scim-bridge, XMOD: @im=scim[/B][/COLOR]
```

It's largely an issue of getting all the variables right. Someone with knowhow should cook up a script to troubleshoot what could be set wrong.

---

### Post by dasan on 2009-12-02
sorry for late posting 
after everything i am getting it as 

[COLOR="Green"]XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
GTK: scim, Qt: scim, XMOD: @im=SCIM[/COLOR]

i tried  im switch -c this is the output

There are 9 candidates which provide IM for /home/anand/.xinput.d/en_IN:

  Selection    Alternative
  -----------------------------------------------
      1        bac-skim
 +    2        default
      3        default-xim
      4        none
      5        scim
*     6        scim-bridge
      7        scim-bridge~
      8        scim-immodule
      9        th-xim


but still scim couldn't get what we meant 

i couldn't make {GTK: scim, Qt: scim} these result as scim-bridge 

any way i decided to study inscript typing
thankz lot for your great help

---

### Post by platypeanArccow on 2010-05-23
Hi, I have a similar problem (I believe) to the one dasan had -- I cannot use skim in Qt apps.  The options I'm getting are as follows:

```

$ sudo im-switch -l
Your input method setup under en_US locale as below.
=======================================================
No private configuration can be defined for root account.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - manual mode
 link currently points to skim
default - priority 10
default-xim - priority 0
none - priority 0
skim - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
/usr/bin/find: `/home/fedya/.xinput.d': No such file or directory
default default-xim ibus ibus-kde lo-gtk nabi none scim scim~ scim-bridge scim-bridge~ scim-chewing scim-hangul scim-hangul_xim scim-immodule scim-pinyin skim skim~ th-gtk th-gtk-im-libthai th-xim 
=======================================================
$ sudo im-switch -c
No system wide default defined just for locale en_US .
Use "all_ALL" quasi-locale and set IM.
System wide default for all_ALL locale is marked with [+].
There are 4 choices for the alternative xinput-all_ALL (providing /etc/X11/xinit/xinput.d/all_ALL).

  Selection    Path                                 Priority   Status
------------------------------------------------------------
  0            /etc/X11/xinit/xinput.d/default       10        auto mode
  1            /etc/X11/xinit/xinput.d/default       10        manual mode
  2            /etc/X11/xinit/xinput.d/default-xim   0         manual mode
  3            /etc/X11/xinit/xinput.d/none          0         manual mode
* 4            /etc/X11/xinit/xinput.d/skim          0         manual mode

Press enter to keep the current choice
[*], or type selection number: 

```This confuses me since I have files called /etc/X11/xinit/xinput.d/scim, ***/scim-bridge, and several others.  The file ***/skim contains the same text as that for ***/scim-bridge recommended by Zorael.  Nevertheless, I cannot use skim in any apps that use Qt.  I have had this problem for a while, but I do most of my Japanese typing in GTk apps, so it hasn't been a huge nuisance (except with Kiten...) and so I haven't bothered trying to fix it.  I want to try to fix it now though.  [Edit: I'm currently using Lucid, with whatever version numbers that implies for everything else, though again I've had the problem for a while.]

---

### Post by dasan on 2010-05-23
@platypeanArccow
Its ok for me now  
In lucid

---

### Post by Zorael on 2010-05-23
> **platypeanArccow said:**
> Hi, I have a similar problem (I believe) to the one dasan had -- I cannot use skim in Qt apps.

Please post the terminal output of the following. One line for easy copy/pasting. It even includes code tags, yay. The output may be longer than a full screen.
```
IM=scim; echo -e "\n[CODE""]\nSettings:"; grep -nvH ^\# /etc/alternatives/xinput-all_ALL; echo -e "\nCurrent variables:\nGTK:\t$GTK_IM_MODULE\nQt:\t$QT_IM_MODULE\nXMOD:\t$XMODIFIERS\n\nInstalled packages:"; dpkg -l *$IM* | grep ^ii | awk '{ print $2 }'; echo -e "\nCurrent processes:"; ps aux | grep -i $IM | grep -v grep; echo "[/CODE""]"
```

And do note that SCIM (for which Skim is a front end) is sort of being phased out in favor of ibus. I use UIM myself. They should all work though, assuming you get it set up properly.

---

### Post by dasan on 2010-06-08
I got the cause of this problem.
In 10.04 also many of my friends has this problem
**while installing if you are selecting language as US English then there is no problems **
and later you can change it to any language and every thing will be fine

:p

---

