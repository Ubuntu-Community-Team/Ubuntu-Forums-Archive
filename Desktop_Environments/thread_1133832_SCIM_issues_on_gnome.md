---
title: "SCIM issues on gnome"
date: 2009-04-23
forum: Desktop Environments
---

### Post by adamitj on 2009-04-23
I'm having an issue with SCIM (Smart Common Input Method) with my Ubuntu 8.10 32-bit.

My desktop is always running Skype (from medibuntu) and Netbeans 6.5.1. Well, everytime a skype chat starts a conversation window appears, and them a keyboard icon at the left side of clock appears, and my Netbeans editor hang ups the keyboard and I cannot type anything. The only way to put it back to work is restarting Netbeans.

I don't know if this is a Java/Swing problem in linux, but I need to solve it. I thought in remove SCIM (sudo apt-get --purge remove scim), but I'm afraid it can cause more problems than I have now.

Does anyone knows how to disable SCIM or whether I'll got problems removing it?

P.S: I have both english and portuguese languages installed, but I use english most of time.

---

### Post by Zorael on 2009-04-23
Yes, you can set the default input method to something else.
```
$ sudo im-switch -c
```
Try to pick 'none' or 'default'. Do it as non-root to make sure you don't have user-specific settings pointing to scim.
```
$ im-switch -c
```
If you want to choose method for a given locale (like en_US, ja_JP), add the **-z lang_CODE** argument. On my Kubuntu installations, the default seems to be all_ALL (and not en_US). Not supplying a locale should make it default to the current.
```
$ sudo im-switch -c -z en_GB
```
Lastly, the methods they're pointing to are files located in **/etc/X11/xinit/xinput.d/**, if you want to take a gander at how they differ.

---

### Post by adamitj on 2009-04-30
I can't put this to work because I changed my current default language, so when I did again the step below without sudo:

```
$ im-switch -c
```

And selected the 3rd option (none), everything started to work as it should be.

Thank you very much!

P.S.: This solves also the problem described in ***[Keyboard problems with Skype and Netbeans + vBox-ose]("http://ubuntuforums.org/showthread.php?t=1143760")***

---

### Post by ABCDPG3 on 2009-05-24
Seriously, this issue with SCIM has been causing me all kinds of pain.  Two of my most heavily-used applications, freemind and eagle, were rendered pretty much useless.

I left gentoo because I thought its high-level pathologies were too esoteric and poorly documented.  But this one SCIM problem is only *slightly* less distasteful than the very worst gentoo could muster.  So far, ubuntu's vaunted user-friendliness has cost me more time than it's saved...

(And don't even get me started on the intermittent hangs I've been getting since switching to ubuntu, or the complete lack of a respectable audio CD burner.)

I've only been with ubuntu for ~4 months, and I just can't tell if the problems I've been having are specific to poorly architected/implemented applications like SCIM or Compiz, or if it's indicative of some systematic deficit within the ubuntu team.

---

### Post by James Keating on 2009-06-04
My experience with installing SCIM in 9.04 (Jaunty) was mostly simple. I added full Japanese support through Administration/Language Support, and SCIM worked fine with the standard set of packages. 

However, I had one problem that I didn't recognize as being related to SCIM: I had constant trouble with losing keyboard input. If I used any input field or blank in my Web browser, the keyboard wouldn't respond again until I forced window manager to focus on the program again by clicking on the title bar or by right-clicking on the page and canceling. The problem with typing showed up mainly with Opera, which uses the Qt toolkit, and in TkDesk, which uses Tcl/Tk. I thought that this might be a problem with my window manager, FVWM, or with GDM, since GDM is the background to everything else. 

The problem was that SCIM defaulted to using XIM, though SCIM-bridge is better. Other posts here refer to editing the file /etc/X11/xinit/xinput.d/scim-bridge. You don't have to go there directly. In your home directory, there should be a hidden directory called .xinput.d, with a file that links to  /etc/X11/xinit/xinput.d/scim-bridge. My file is named en_US. All I had to do was edit it (as root) and change the module lines. For GTK-based programs, I changed them to prefer SCIM-bridge and then SCIM. For Qt-based programs, I changed the module lines to prefer SCIM, then XIM. The only Qt-based program I use is Opera, but Opera won't work with SCIM-bridge, even though the file /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so is present.  

My /etc/X11/xinit/xinput.d/scim-bridge now looks like:

XIM=SCIM
if [ -e /usr/bin/skim ]; then
    XIM_PROGRAM=" "
else
    XIM_PROGRAM=/usr/bin/scim-bridge
fi
XIM_ARGS="-d"
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
else
    GTK_IM_MODULE=scim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim
else
    QT_IM_MODULE=xim
fi
DEPENDS="scim | skim, scim-bridge-agent, scim-bridge-client-gtk | scim-bridge-client-qt"

This also fixed the focus problem with TkDesk. 

Qt programs need the packages scim-bridge-client-qt and scim-qtimm. 
Also, it may help to edit your file ~/.scim/global to add the line 
/DefaultConfigModule = kconfig

Before I found a proper fix for Opera, I was able to start it with
scim -d & XMODIFIERS="@im=SCIM" QT_IM_MODULE="scim" opera

You may need to use different choices (scim, skim), but fixing this file should fix the problem.

#####

Update for Lucid 10.04:

Ubuntu now uses IBus and no longer supports SCIM. Too bad IBus doesn't work with any Qt-based programs. 

My current language setup:

1. Under System, Administration, Language Support, choose Japanese.

2. Install programs that Ubuntu doesn't include by default (including essential packages ...)
edict
enamdict
gjiten
kanjidic
kdrill
poppler-data (to view Japanese PDFs)
gs-cjk-resource
cmap-adobe-japan1 
cmap-adobe-japan2
xpdf-japanese

I also installed more ttf fonts, but not all: Sazanami and Kochi gothic and mincho, VL Gothic, , Kiloji, Mikachan and ttf-mscorefonts (MS Gothic and Mincho, Osaka).
Other nice fonts are available at [http://www.wazu.jp/gallery/Fonts_Japanese2.html;](http://www.wazu.jp/gallery/Fonts_Japanese2.html;) download and put in your ~/.fonts directory. Not all have romaji, and not all even work. I kept: Aoyagi Kouzan(&#38738;&#26611;&#34913;&#23665;), Soseki and Reishoka (&#38738;&#26611;&#38583;&#26360;&#19979;), Aquafont, Armed Lemon, Azukifont, Cinecaption, Deshima (&#20986;&#23798;), several Epson fonts, HuiFont, Kouzan brush (two), Makiba, Mona, Moon, MtTare, nagurigaki, Ohisama, Onryou, SZG Memo, Sanafon (two), Sea, Sword, unifont 

3. the hidden home directory file ~/.xinput.d/en_US, which links to /etc/X11/xinit/xinput.d/scim-bridge, may need editing (as root)
I changed mine to prefer scim-bridge, then scim, and not xim:

XIM=SCIM
if [ -e /usr/bin/skim ]; then
    XIM_PROGRAM=" "
else
    XIM_PROGRAM=/usr/bin/scim-bridge
fi
XIM_ARGS="-d"
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
else
    GTK_IM_MODULE=scim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
else
    QT_IM_MODULE=scim
fi
DEPENDS="scim | skim, scim-bridge-agent, scim-bridge-client-gtk | scim-bridge-client-qt"

4. Opera, and possibly other QT-based applications, may have more trouble than before. If you can't get Opera to work again with scim, you can start it from the command line with 
	scim -d & XMODIFIERS="@im=SCIM" QT_IM_MODULE="scim" opera

To start it from the regular menu, I made a file called ~/.bin/opera-scim:

#!/bin/sh
QT_IM_MODULE="scim"; export QT_IM_MODULE
XIM_PROGRAM="scim -d"; export XIM_PROGRAM
opera

and then edited the menus to change the properties of the Opera item to run that file:
opera-scim %u

---

