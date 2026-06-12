---
title: "[SOLVED] Title bars and window frame disappears with compiz"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by johann_p on 2007-11-17
Have Nvidia card. If i enable compiz all window titles and frames disappear. Kill it and they are back.
Have looked at some related threads, and one recommended to install  compizconfig-settings-manager .. now the desktop effects menu entry seems to be gone from the system-preferences menu.

NVidia restricted driver is enabled and in use.

---

### Post by Zorael on 2007-11-17
You need a window decorator to get titlebars and similar when running Compiz.

Do you have the Window Decorations plugin enabled in the settings manager? You can start it from the run box or by making a permanent launcher; **ccsm**.

If you're running Ubuntu, your main decorator alternatives would be emerald or gtk-window-decorator. If you're running Kubuntu, your only realistic option would be emerald, since kde-window-decorator plain doesn't work for many of us.

gtk-window-decorator comes with the compiz-gnome package, which is part of the compiz meta-package, so you should have it by default. If it's not there, you could just install it through Synaptic.

Emerald comes with the emerald package, which you need to find and install if you want it.

Unlike gtk-window-decorator and kde-window-decorator, Emerald has its own skins, so your desktop will have to change its looks. You can download themes from inside the Emerald theme manager (emerald-theme-manager), or on certain sites on the interblag. Such as gnome-look.org.


As for Desktop Effects missing from the menus; I have no idea what could cause that. You can make launchers to call both 'ccsm' for the settings manager and 'compiz --replace' to invoke compiz. 'metacity --replace' to revert to Metacity (Gnome's standard window manager), and 'kwin --replace' to revert to KWin (KDE's).

If you have an Nvidia card, you may want to add '--loose-binding' as an argument when invoking compiz.
```
compiz --replace --loose-binding
```
This will, in many/all (?) cases grant a performance boost.

Furthermore, if you're running KDE, you may want to add '--ignore-desktop-hints' if you don't want to get 4x4 virtual desktops when you only want 4.
```
compiz --replace --loose-binding --ignore-desktop-hints
```

---

### Post by S3loth on 2007-11-17
^that works for me

---

### Post by johann_p on 2007-11-17
> **Zorael said:**
> You need a window decorator to get titlebars and similar when running Compiz.

Do you have the Window Decorations plugin enabled in the settings manager?

I checked an that plugin is selected in the ccsm dialog

> 
gtk-window-decorator comes with the compiz-gnome package, which is part of the compiz meta-package, so you should have it by default. If it's not there, you could just install it through Synaptic.

This has already been installed.

I am running GNOME btw.

This looks like a bug to me -- I do not think windows without a title bar should ever exist.

---

### Post by johann_p on 2007-11-17
> **S3loth said:**
> ^that works for me
Thats great to hear, but not very helpful for me, where it does not work.

---

### Post by Zorael on 2007-11-17
Windows without titlebars are a common issue, with the overwhelming majority of them stemming in the lack of window decorators.

Try this.

Make sure you have the AllowGLXWithComposite and AllowARGBGLXVisuals options enabled in your /etc/X11/xorg.conf. If you don't want to edit it yourself, run this command:
```
$ sudo nvidia-xconfig --allow-glx-with-composite --allow-argb-glx-visuals --composite
```

Then try installing Emerald (emerald package), just to troubleshoot - feel free to uninstall it after all this.

Lastly, invoke compiz and emerald, in that order:
```
$ compiz --replace & emerald --replace
```

Please run that last command in a terminal, and paste any interesting error output here.

---

### Post by johann_p on 2007-11-17
> **Zorael said:**
> Windows without titlebars are a common issue, with the overwhelming majority of them stemming in the lack of window decorators.

Try this.

Make sure you have the AllowGLXWithComposite and AllowARGBGLXVisuals options enabled in your /etc/X11/xorg.conf. If you don't want to edit it yourself, run this command:
```
$ sudo nvidia-xconfig --allow-glx-with-composite --allow-argb-glx-visuals --composite
```Then try installing Emerald (emerald package), just to troubleshoot - feel free to uninstall it after all this.


This was it it seems. BTW, the second option has to be --add-argb-glx-visuals.

Thank you!

---

### Post by Zorael on 2007-11-17
Er, yes, --add-argb-glx-visuals. My bad. :>

---

### Post by Necrome on 2007-11-21
> **johann_p said:**
> This was it it seems. BTW, the second option has to be --add-argb-glx-visuals.

Thank you!

Hello,

I have a different video card:

Mobile intel 945GM Express Chipset Family

so the command 

sudo nvidia-xconfig --allow-glx-with-composite --add-argb-glx-visuals --composite

does not work with me. Is it possible to post the xorg.conf file here or should i use a different command?

Thanks a lot..

---

### Post by rondamato on 2007-12-06
Hello,

I had this problem and it drove me NUTS!!!  I screwed around with the Compiz CP (called Prefs>Advanced Desktop Effects Settings on my Gnome/7.10 box) and when I closed it my titlebars were gone!  Arrgh!  What did I turn on (or off) to do this???

I dimly remembered running into the concept of "Window Decorators" before running X/Gnome on BSD, so I fired up the Compiz CP again.  Turns out that the "ghost in the mouse" accidentally unchecked the "Window Decorators" box (meaning me, of course).

I checked the box and restarted X with a CTRL-ALT-BKSP--same story.  Rebooted, still no titlebars.  I consoled out and typed "compiz --replace & emerald --replace".  After a few screen flashes my titlebars were back!  I rebooted and they were still there!

Now, I am a UNIX guy that grew up using the CLI only; no GUI for me, thanks!  I decided to give Gnome a try when I got the computer and vid card to run it correctly.  Therefore, while I understand the principals of writing a good xorg.conf, I know next to nothing about Gnome.  I don't even know why the command line I typed worked, let alone what "Emerald" even IS.  What I DO know is that Zorael is a genius, and his recommendations saved my machine and my sanity more than once.

If you read this, THANK YOU Zorael!

DoctorRon

---

### Post by rondamato on 2007-12-06
Zorael, you said:
----------------
```
compiz --replace --loose-binding
```
This will, in many/all (?) cases grant a performance boost.
----------------

I am running Gnome and simply called this from the console.  It DOES increase performance!

Questions: First of all, WHY does this work?  I understand exactly how vidcard chipsets work, as I was on a team to design an integrated vid chip years ago for Win95 so you can get techie on me if you want.  Second, is there a way to integrate this command argument into Compiz's conf so it will autorun this?  Do I just autorun the above argument like any other startup program?  The reason I ask is that I can see that it calls Compiz, but I (of course) lose all of my other Compiz prefs when I run Compiz in this manner.

So, I guess the question that I really want answered is this: Is there a way to put this command into a conf file to autorun the "loose-bindings" arg but to also keep my other Compiz plugins up?  I like the extra speed my NV5200 kicks out!

Thank you for your wisdom!

DoctorRon

---

### Post by zekopeko on 2007-12-06
i'm not an expert but if i remember corectly ubuntu launches compiz through a script called compiz.real or someting similar.
try looking in that script and adding the switch there

---

### Post by rondamato on 2007-12-16
Hello,

I tried to vi /usr/bin/compiz.real and it is a binary file, not a conf file as I also would have thought.  I run it (Compiz with the "loose-bindings" switch) b/c with my NVidia card it provides a noticeable performance boost in gfx work, shading speed, polygons per sec, and more--based on benchmarks.

This is a STUPID question, but I must ask it.  Is there a place where I can put a path to a file to be executed at the startup of my window manager?  I use Gnome.  I know how to do this in BSD but it seems to be different in Ubuntu.  Plus the code I want to execute is the aforementioned compiz with the "loose-bindings" switch.  Normally Compiz starts with the WM and its CP is accessed thru SYSTEM>PREFERENCES>ADVANCED DESKTOP EFFECTS SETTINGS.  I can open a term and run the command at a shellprompt and all is well after some screenblanks caused by vidprobes I think.  I just want to automate this!  Will I have to change anything in the "official" Compiz CP in Gnome/Ubuntu (Gibbon) so as to not conflict with starting Compiz from the shell and not from the "official" CP?

So, for the Windoze folks out there I'll put it like this--does Ubuntu have something like Windows' "Startup" folder where anything in it will be run at startup?  Or something like a win.ini where I can say [run=x]?  How about a path=/x/xx/xxx, y/yy/yyy command/statement?  Where would IT go to effect the machine--both for a single user and globally?  So typing "compiz" from any dir will invoke compiz, for example?

Sorry to ask so many dumb questions, but know that once I get these answers my Ubuntu understanding will leap up about 300% or so, so thank you!!!!!!


Ron

---

### Post by Zarin Denatrose on 2007-12-16
My card is a GeForce 7950 GT.

This problem seems to persist trough the fixes provided here. If I run the loose-bindings fix, it works as long as I keep the terminal window that ran it open. 
As soon as I close it, the window frames go away again.
Furthermore, no matter what method I use, Nautilus refuses to get its frames back.

---

### Post by Zorael on 2008-04-12
Resurrecting an old thread because I hate leaving questions unanswered. Lots of quotes so this will get lengthy. Hopefully you've gotten your problems fixed by now but perhaps this will help someone else, hmm? And my post count increases! Joy!

> **Necrome said:**
> Hello,

I have a different video card:

Mobile intel 945GM Express Chipset Family

so the command 

sudo nvidia-xconfig --allow-glx-with-composite --add-argb-glx-visuals --composite

does not work with me. Is it possible to post the xorg.conf file here or should i use a different command?

Thanks a lot..
I'm afraid I don't know how to set it up for Intel drivers. To know more (and if you subscribed to this thread so you actually read this, heh), could you post the output of calling compiz from a terminal?
```
$ compiz --replace &
```
If it starts but you lose window borders, you should be able to restore it by entering "**metacity --replace &**" for Gnome and "**kwin --replace & **" for KDE. If you omit the ampersand (&) it will break if you close the terminal.


> **rondamato said:**
> Zorael, you said:
----------------
```
compiz --replace --loose-binding
```
This will, in many/all (?) cases grant a performance boost.
----------------

I am running Gnome and simply called this from the console.  It DOES increase performance!

Questions: First of all, WHY does this work?  I understand exactly how vidcard chipsets work, as I was on a team to design an integrated vid chip years ago for Win95 so you can get techie on me if you want.  Second, is there a way to integrate this command argument into Compiz's conf so it will autorun this?  Do I just autorun the above argument like any other startup program?  The reason I ask is that I can see that it calls Compiz, but I (of course) lose all of my other Compiz prefs when I run Compiz in this manner.

So, I guess the question that I really want answered is this: Is there a way to put this command into a conf file to autorun the "loose-bindings" arg but to also keep my other Compiz plugins up?  I like the extra speed my NV5200 kicks out!

Thank you for your wisdom!

DoctorRon
> **http://forum.compiz-fusion.org/showthread.php?t=2985]With strict binding textures are bound whenever they are enabled, with loose binding they are enabled when created. The Nvidia driver seems a bit slow when binding textures, that's why this option gives a heavy performance increase on Nvidia.[/quote]
I guess that explains things, heh. Way out of my league though. See further down for the autorun thing.


[QUOTE=rondamato said:**
> Hello,

I tried to vi /usr/bin/compiz.real and it is a binary file, not a conf file as I also would have thought.  I run it (Compiz with the "loose-bindings" switch) b/c with my NVidia card it provides a noticeable performance boost in gfx work, shading speed, polygons per sec, and more--based on benchmarks.

This is a STUPID question, but I must ask it.  Is there a place where I can put a path to a file to be executed at the startup of my window manager?  I use Gnome.  I know how to do this in BSD but it seems to be different in Ubuntu.  Plus the code I want to execute is the aforementioned compiz with the "loose-bindings" switch.  Normally Compiz starts with the WM and its CP is accessed thru SYSTEM>PREFERENCES>ADVANCED DESKTOP EFFECTS SETTINGS.  I can open a term and run the command at a shellprompt and all is well after some screenblanks caused by vidprobes I think.  I just want to automate this!  Will I have to change anything in the "official" Compiz CP in Gnome/Ubuntu (Gibbon) so as to not conflict with starting Compiz from the shell and not from the "official" CP?

So, for the Windoze folks out there I'll put it like this--does Ubuntu have something like Windows' "Startup" folder where anything in it will be run at startup?  Or something like a win.ini where I can say [run=x]?  How about a path=/x/xx/xxx, y/yy/yyy command/statement?  Where would IT go to effect the machine--both for a single user and globally?  So typing "compiz" from any dir will invoke compiz, for example?

Sorry to ask so many dumb questions, but know that once I get these answers my Ubuntu understanding will leap up about 300% or so, so thank you!!!!!!


Ron
This is iffy with Ubuntu since it launches Compiz from behind the scenes. There's likely a smart way of solving this by editing gconf stuff, but you could try this. This won't break Compiz upon updating, but you'll lose these changes (so need to do them again).
```
$ cd /usr/bin
$ sudo mv compiz compiz.launcher

Gnome (Ubuntu):	$ gksudo gedit compiz
KDE (Kubuntu):	$ kdesu "kate compiz"
Xfce (Xubuntu)	$ gksudo mousepad compiz
Terminal:	$ sudo nano compiz
```
Paste the following:
```
#!/bin/bash

compiz.launcher --loose-bindings $@ &
```
This script will call compiz.launcher with provided arguments **plus** --loose-bindings. I've done this with lots of apps, like Kate (with which I added an argument to make it open in already open sessions, if such exist). The ampersand lets you keep terminal control.


> **Zarin Denatrose said:**
> My card is a GeForce 7950 GT.

This problem seems to persist trough the fixes provided here. If I run the loose-bindings fix, it works as long as I keep the terminal window that ran it open. 
As soon as I close it, the window frames go away again.
Furthermore, no matter what method I use, Nautilus refuses to get its frames back.

As mentioned earlier, whenever you call compiz, add an ampersand (&) to the end of the line.
```
$ compiz --loose-bindings &
```



edit: Lastly, **make sure** you have the Window Decorations plugin enabled, and Emerald installed. Even if you don't want to use Emerald (but rather gtk-window-decorator or kde-window-decorator), install it for now, just to see if things work. If you don't have a window decorator (emerald/gtk-window-decorator etc), you won't get any borders no matter how much you configure stuff right.

---

