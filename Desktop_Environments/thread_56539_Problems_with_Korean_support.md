---
title: "Problems with Korean support"
date: 2005-08-12
forum: Desktop Environments
---

### Post by jrleek on 2005-08-12
So, I've had real trouble with Korean support on ubuntu 5.04.  (ALthough most everything else has been great.)  I did a standard installation, although I installed in English (my first language) and gave my keyboard layout as US English.  (This was not actually true, it's a Korean keyboard, but korean keyboards are not all thought different, so I didn't think about it.)
  Anyway, now I want to get Korean support working.  I can read Korean webpages, but I want to be able to type korean as well.  So I installed both Korean language support and the translation pack in Synaptic.  Then I went to System->Preferences->Keyboard.  Then I added the korean keyboard layout.  At which point, I got the following error: (3 times!)

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>

(Interestingly, my friend gets exactly the same error if he tries this with his Debian install.)

Just to complete the error report, I get:  

$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "us", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "en_US", "", "grp:alts_toggle,altwin:menu"

$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [en_US,ko]
 model = pc104
 overrideSettings = false
 options = [grp grp:alts_toggle,altwin  altwin:menu]

So, any ideas about what I can do?
Thanks
Jim

---

### Post by Marc Higgins on 2005-11-11
Hi Jim,

We are having some of the same issues here; we live & work in Seoul so Korean is fairly important to us & many korean sights don't work properly (in my view) because they are made with only MS java in mind & it's a bastardised java.

To be fair I have come across a number of US sights that are the same.

In terms of input methods the alternatives I know of are scim & nabi.

Have got scim running but Hoary doesn't seem to do korean properly, some 3 charicter letters can't be typed.

Have nabi working on a FC4 machine with gnome & it works a treat (apart from being a redhat machine). The only reason it's not an ubuntu machine is I haven't worked out Nabi on Breezy

Have had a few shots at getting nabi runing but i just end up with the input box & no thing to select for korean inut. My challenge is want to be able to do this not only in gnome but also xfce4 (xubuntu) & KDE

This is what i have installed.
imhangul (0.9.11-1)
language-pack-gnome-ko (20051011)
language-pack-gnome-ko-base (20051011)
language-pack-ko (20051011)
language-pack-ko-base (20051011)
language-support-ko (20051010)
libnspr4 (2:1.7.12-1ubuntu1)
mozilla-browser (2:1.7.12-1ubuntu1)
mozilla-firefox-locale-ko (1.0-1ubuntu1)
mozilla-locale-ko (1.7-1)
nabi (0.15-1)
openoffice.org2-help-ko (1.9.129-0.1ubuntu5)
openoffice.org2-l10n-ko (1.9.129-0.1ubuntu3)
ttf-alee (4.7ubuntu1)
ttf-unfonts (1.0.1-2ubuntu1)
xfonts-baekmuk (2.2-1ubuntu1)


Then I have  

#sudo dpkg-reconfigure locales

decided i didn't really need 50 differnet kinds of english but i did need Korean, so  i selected the following; 

en_US.UTF-8 UTF-8
ko_KR.UTF-8 UTF-8
ko_KR.EUC-KR EUC-KR

the quick way to achivev the same this is sudo nano /etc/locale.gen  edit it to look like this & save it

en_US.UTF-8 UTF-8
ko_KR.UTF-8 UTF-8
ko_KR.EUC-KR EUC-KR

then run 

 sudo locale-gen

But when i run nabi for the term i see;

Nabi: Can't load config file
Nabi: xim server started

It starts but there are no fonts

---

