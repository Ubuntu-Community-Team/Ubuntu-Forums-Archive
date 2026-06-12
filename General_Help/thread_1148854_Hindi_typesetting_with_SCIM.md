---
title: "Hindi typesetting with SCIM"
date: 2009-05-04
forum: General Help
---

### Post by mrcactu5 on 2009-05-04
How do I add aspirated consonants?  Or vowels. So far I can only do &#2325; &#2327; &#2346; &#2348; &#2349;.  Well I can some syllables to, like &#2346;&#2367; &#2346;&#2368; &#2346;&#2375; &#2346;&#2379; &#2350;&#2378; 

Is there a page with all the Devanagari symbols and how to type them?

---

### Post by Zorael on 2009-05-06
You're using SKIM, I imagine?

Have you checked the scim-setup utility? At least with Anthy (Japanese input), even if you use SKIM you have to use SCIM's setup utility to manage Anthy-specific settings.

---

### Post by akshar_patel_47 on 2009-07-14
I'll tell you how I learnt to type using SKIM...

First of all use Hindi phonetic..

I started to type one letter after another and made a note of what it does and then plotted all the characters in an image using inkscape.

Now if you use phonetic all you got to do is to go with the sounds of the hindi words.

I wanted to ask if you can write using SKIM in OpenOffice?

---

### Post by Zorael on 2009-07-14
Yes, but you need to modify a file since for some non-apparent reason whoever created the installation script for skim didn't see it fit to make it use the *available* XIM wrapper. So, terminal time.

First make sure you have all the necessary packages.
```
$ sudo aptitude install ~nscim-bridge scim-gtk2-immodule scim-qtimm
```

Then enter the following and pay special attention to the marked-up output.
```
$ im-switch -l
Your input method setup under en_US locale as below.
=======================================================
No private "/home/zorael/.xinput.d/en_US or /home/zorael/.xinput.d/all_ALL" is defined.
=======================================================
The system wide default is pointed by "**/etc/alternatives/[COLOR="RoyalBlue"]xinput-all_ALL[/COLOR]**" .
**[COLOR="RoyalBlue"]xinput-all_ALL[/COLOR]** - status is manual.
 link currently points to **[COLOR="Lime"]skim[/COLOR]**
**default** - priority 10
**default-xim** - priority 0
**none** - priority 0
[COLOR="Lime"]skim[/COLOR] - priority 0
Current `best' version is **default**.
=======================================================
The available input method configuration files are:
/usr/bin/find: `/home/zorael/.xinput.d': No such file or directory
default default-xim none scim scim-bridge scim-immodule skim th-xim
=======================================================
```
The **skim** it refers to (and **default**, **default-xim** and **none**) are files located in **/etc/X11/xinit/xinput.d/**. You can change which one you're using by entering the following in a terminal. Omit **sudo** to make it a user-specific setting, which I guess is useful if you have several users and not all of them want to use skim to write in Hindi.
```
$ **sudo** im-switch -z **[COLOR="RoyalBlue"]all_ALL[/COLOR]** -c
```
Replace **[COLOR="RoyalBlue"]all_ALL[/COLOR]** with what the first command said was your system default. If you don't supply the '-z **[COLOR="RoyalBlue"]lang_LANG[/COLOR]**' argument at all, I believe it defaults to the currently running one, but I'm not sure, so may as well enter it.

In the menu that pops up, pick **[COLOR="Lime"]skim[/COLOR]**, and then modify **/etc/X11/xinit/xinput.d/[COLOR="Lime"]skim[/COLOR]** to look like the following. If I'm right, the lines in bold will differ / not exist. Anyway, just back it up first, and then replace it with this.
```
XIM=SCIM
[B]XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes[/B]

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

DEPENDS="skim, scim-bridge-client-gtk | scim-bridge-client-qt | scim-bridge-client-qt4 | scim-gtk2-immodule | scim-qtimm"
```
It doesn't really matter if you pick skim or default or none, as long as you modify the corresponding file in /etc/X11/xinit/xinput.d/.

Log out and restart X (alt+e at login prompt?), or make a full reboot. Then open up OpenOffice or xterm and see if your skim keybinds work.

---

