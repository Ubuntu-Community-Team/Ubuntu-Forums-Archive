---
title: "Swedish keybord-layout"
date: 2005-03-10
forum: Desktop Environments
---

### Post by Azyx on 2005-03-10
I have installed a minimal ubuntu according to this manual:
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

During the installation I always select Swedish language, swedish keyboard-layout ect. And before i start xserver it's work fine., all swedish letters is there. First time i tryed install I use english as install language, but swedish keybord-layout. And it also work before I start xserver. But when i start xserver, and have english as install language, the keyboard layout being English (There are different places on some sign as -, . / and some more, but if I use Swedish as install language the keyboard-layout being swedish, but some letters don´t work and a warningsound appeares when i press thies keys and the problem are both in terminal and GUI-program.

Is there anyone who know there i can change it to completly work with swedish keyboard AND letters? 

And I say it again, the ubuntu-base-system seems to work in both cases before i start xserver, but it's a problem with icewm, xserver och x-windows-system.

Thanx for any help.

---

### Post by lorap on 2005-03-10
hi friend!
think i'm right:
first go to Computer->Keyboard
then choose "Layout" option
then in the list of languages choose Swedis and press "Add" button
that's all i think
afterwhat place your mouse over the panel at the top
press right button and choose "Add to the panel" option in the list option with flags that lets switch between
languages
pavel
israel

p.s.:
by clicking in the languages icon you can switch between languages.

---

### Post by landotter on 2005-03-10
^^^^^^^^^^^^^

Works for me--I have a button on my panel to switch between English/Swedish and the Swedish vowels sharpied onto my keyboard. :D

---

### Post by lorap on 2005-03-10
sorry friend i just misunderstood.
i do have the same problem with hebrew but not with russian, in open office.
pavel

---

### Post by landotter on 2005-03-10
[QUOTE=lorap]sorry friend i just misunderstood.
i do have the same problem with hebrew but not with russian, in open office.
pavel[/QUOTE]
 from this thread: [http://www.ubuntuforums.org/showthread.php?t=18318&highlight=adding+language](http://www.ubuntuforums.org/showthread.php?t=18318&highlight=adding+language)

go to console window
 
 ./dpkg-reconfigure locales
 
 and choose all the language you want
 
 shutdown the machine
 boot....
 
 In GDM,choose language you want in "Language" button in lowerleft
corner.

You'll still need to click the panel applet for the correct keyboard layout.

For Openoffice make sure to install the correct languagepack in Synaptic, you can have more than one.

Go to Options/language settings and you can configure the language and spellcheck dictionary.

I don't see russian or hebrew myspell dictionaries listed for install w/synaptic, so for that you're on your own. ;)

---

