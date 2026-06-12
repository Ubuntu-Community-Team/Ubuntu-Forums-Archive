---
title: "Help for little girl's Ubuntu in time for Xmas !"
date: 2008-12-21
forum: General Help
---

### Post by its_jon on 2008-12-21
Hi...

I have a PC that looks like this
[http://www.computer-reclaim.co.uk/compaq-ipaq-p3-866mhz-187-p.asp](http://www.computer-reclaim.co.uk/compaq-ipaq-p3-866mhz-187-p.asp)
that I have installed ubuntu on for a little girl for xmas.

I have tux paint working... she loves that on my ubuntu machine !

I installed it along with tux racer, neverball ect.... changed the whole theme pink etc etc....

trouble is that tuxracer and neverball don't display correct/ very badly....

I only see a few fuzzy lines of the games in the bottom half of the screen.... as if its an old tv on the blink.

I assume Ubuntu may not have installed the correct graphics driver possibly? or a problem with open GL ?

I checked the admin/hardware drivers  ..... nothing there "no proprietary drivers are in use on the system"

shooting in the dark... don't know what to do next ?

help :)

---

### Post by Topsiho on 2008-12-21
I find on the link that you mentioned:

256MB SDRAM
...
Onboard Intel Graphics

256 MB is the bare minimum RAM that is needed for Ubuntu, and probably some of that is needed (taken) for/by the onboard Intel graphics card.

You could try and install xubuntu instead, which is a more lightweight distribution.

And of course the graphics card may not support opn GL, than you are stuck I am afraid.

Topsiho

---

### Post by sigurnjak on 2008-12-21
I belive you problem could be on board video . Check if you can assign more ram to video in bios or put in a another video card . Your system may only have pci slots and no agp , but any card could be improvement over  old on board video . Also little more ram may help and switching to lxde could help.

---

### Post by its_jon on 2008-12-21
system monitor reports 375.4mb ram on this machine although it does look exactly the same as the one in the picture.

Its a PIII

---

### Post by Ender41 on 2008-12-21
> **its_jon said:**
> Hi...

I have a PC that looks like this
[http://www.computer-reclaim.co.uk/compaq-ipaq-p3-866mhz-187-p.asp](http://www.computer-reclaim.co.uk/compaq-ipaq-p3-866mhz-187-p.asp)
that I have installed ubuntu on for a little girl for xmas.

I have tux paint working... she loves that on my ubuntu machine !

I installed it along with tux racer, neverball ect.... changed the whole theme pink etc etc....

trouble is that tuxracer and neverball don't display correct/ very badly....

I only see a few fuzzy lines of the games in the bottom half of the screen.... as if its an old tv on the blink.

I assume Ubuntu may not have installed the correct graphics driver possibly? or a problem with open GL ?

I checked the admin/hardware drivers  ..... nothing there "no proprietary drivers are in use on the system"

shooting in the dark... don't know what to do next ?

help :)

 The only way to get those to run on that machine is to put a video card in it minimum of 128M nvidia or similar would be needed I think. Tux racer is very resource hungry, not sure on the other one but suspect it is similar. Just installed it on my wife's computer to check out things, it is choppy on hers though it runs. Hers is 64M video card, 512M ram 1Ghz cpu, from that test I think that unfortunately it is not something that will run well on your machine.

Ender

---

### Post by its_jon on 2008-12-21
screenshot of neverball startup screen

note system monitor in background / memory

---

### Post by Ender41 on 2008-12-21
> **its_jon said:**
> screenshot of neverball startup screen

note system monitor in background / memory

That is a video sync problem for sure. A separate video card may fix it but kids will get bored very quickly with games that play badly. Look for something else and forget those two to avoid frustration on her part. Have you looked at what is available in the edubuntu packages for instance.


Ender

---

### Post by its_jon on 2008-12-21
screenshot of neverball startup screen

note system monitor in background / memory

---

### Post by its_jon on 2008-12-21
> **Ender41 said:**
> That is a video sync problem for sure. A separate video card may fix it but kids will get bored very quickly with games that play badly. Look for something else and forget those two to avoid frustration on her part. Have you looked at what is available in the edubuntu packages for instance.


Ender

No problem people. thanks for the advice.... as long as I know its already as good as it can be.

how do I access the edubuntu packages ?

many thanks
john
Scotland

---

### Post by Ender41 on 2008-12-21
> **its_jon said:**
> No problem people. thanks for the advice.... as long as I know its already as good as it can be.

how do I access the edubuntu packages ?

many thanks
john
Scotland

 If you have synaptic installed just type edubuntu into the search box, it will show you what is available, you than then choose what to install.


Ender

---

### Post by its_jon on 2008-12-21
Just checking .... even the screensavers dont seem to work ?

I thought screensavers were designed to use very little processing power ?

---

### Post by exploder on 2008-12-21
Just a thought, you might want to try LinuxMint Elyssa on the pc. The onboard graphics should be supported. Just a suggestion.

---

### Post by its_jon on 2008-12-21
Hmmmm !!!

Just had a thought.

This machine had ubuntu installed for a different task.... the people I set it up for diddnt want the machine (long story)

But...... 

I vividly remember that everything seemed to work INCLUDING the GL screensavers.

I never had access to the internet at that time so never got round to installing games or updating the OS.

Only one main difference between then and now...... I found a better newer monitor .... so the monitor has changed.

Im sure I could have a monitor issue ? as I guess ubuntu still thinks its supplying a singnal to the old monitor ?

Where and what would I check ?

thanks for your patience everyone.

---

### Post by tukuyomi on 2008-12-21
Can you post the content of the file /etc/X11/xorg.conf please?

---

### Post by its_jon on 2008-12-21
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by tukuyomi on 2008-12-21
Try to explicitly tell Xorg to use the best resolution for your screen (below is an example).
Edit /etc/X11/xorg.conf with
```
$ gksudo gedit /etc/X11/xorg.conf
```and add these lines on the Section "Screen":
```
Section "Screen"
[...]
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection
```

---

### Post by its_jon on 2008-12-21
Thanks very much everyone !.....

That fixed it !.....

Thanks tukuyomi....

:)

neverball and racer are displaying correctly but impossibly slow... guess thats a memory allocation issue so I will have a look in the bios to see if I can do anything there...

thanks everyone.....

will post a screenshot of the finished girly theme when its finished...

all the best for the festive season.

---

### Post by hyper_ch on 2008-12-21
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by its_jon on 2008-12-21
> **hyper_ch said:**
> It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

thanks for the pointers.....

partly my problem was that I did not quite know how to describe the problem in the first place... as it turned out my problem was a monitor issue (I think ?) ... at first I tried to find out the exact PC model no. then the graphics chip set... but rather than post the wrong info in the title and possibly describe the problem wrongly .....well..you know.
My apologies for the personal angle....

---

### Post by its_jon on 2008-12-21
All set for Xmas..... Thanks

---

### Post by redilyn on 2008-12-21
Nice theme.

I would change the top panel font to white for better vis.

If you are interested in doing that. Try the following:

create the file .gtkrc-2.0 in your home dir then put the following in that file.
```

style "panel"
{
fg[NORMAL]               = "#ffffff"
#  fg[PRELIGHT]            = "#000000"
#  fg[ACTIVE]               = "#ffffff"
#  fg[SELECTED]            = "#000000"
#  fg[INSENSITIVE]            = "#8A857C"

#  bg[NORMAL]               = "#000000"
#  bg[PRELIGHT]            = "#dfdfdf"
#  bg[ACTIVE]               = "#D0D0D0"
#  bg[SELECTED]            = "#D8BB75"
#  bg[INSENSITIVE]            = "#EFEFEF"

# base[NORMAL]            = "#ffffff"
#  base[PRELIGHT]            = "#EFEFEF"
#  base[ACTIVE]            = "#D0D0D0"
#  base[SELECTED]            = "#DAB566"
#  base[INSENSITIVE]         = "#E8E8E8"

  text[NORMAL]            = "#ffffff"
#  text[PRELIGHT]            = "#000000"
#  text[ACTIVE]               = "#000000"
#  text[SELECTED]            = "#ffffff"
#  text[INSENSITIVE]            = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

```

Cheers

---

### Post by exploder on 2008-12-21
Looks like the PC turned out real nice! Glad you got everything to work. I might have to try something like that for my youngest son. Nice work!

---

