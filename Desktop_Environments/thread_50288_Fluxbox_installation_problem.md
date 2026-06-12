---
title: "Fluxbox installation problem"
date: 2005-07-19
forum: Desktop Environments
---

### Post by ShaneR on 2005-07-19
I recently download fluxbox from synaptic.  The installation went fine.  However, when I log into a fluxbox session, I'm only presented with the taskbar and nothing else.  No slit, nothing in the menus(right-click). 

Is there something stupid that I'm missing??

Not sure what info you would need.  Fairly clean install of Ubuntu with KDE added on for choice.  Everything working fine...

Thanks :)

---

### Post by t2kburl on 2005-07-20
try a reinstall and add in fluxconf, too. I got the menu ok, but no slit here either

---

### Post by rutty on 2005-07-27
I tried this last night too. All I get on the right-click menu is the option to start an xterm term or logout. I'll try that fluxconf later...

---

### Post by swamytk on 2005-08-09
I too get the same screen of "JUST EMPTY BROWN SCREEN WITH MOSTLY HIDDEN TASK BAR". Nothing working. No Response for Mouse Click. I have installed fluxconf and menu also. Any clue? I was using fluxbox in Mandrake 10.0 nicely. It is a heaven.

---

### Post by egon spengler on 2005-08-10
It sounds as if there isn't a menu defined. Firstly run the command ```
fluxbox-generate_menu
``` to generate a menu file in your ~/.fluxbox directory


Next, check your ~/.fluxbox/init file to make sure that

a) the init file itself exists
b) it contains some reference to a menufile

```
cat ~/.fluxbox/init |grep menuFile
```

If the menufile doesn't point to the menu file you just created then you need to edit it (with gedit or nano or whatever you prefer) so that it does. This should fix the no menu problem.

The brown desktop is because no desktop has been set with flux and so the default brown desk of ubuntu is showing. You can use fbsetbg -f /path/to/image.jpeg to set the background. Personally i use [feh](http://linuxbrit.co.uk/feh/wiki/FehFeatures). Adding          ```
   [exec] (wallpaper) {/usr/bin/feh "/pathtowallpaperfolder"}
``` to my menu adds an entry that starts feh and allows me to choose an wallpaper. Of course you need to install feh, I'm pretty sure that it's in universe

---

### Post by swamytk on 2005-09-06
[QUOTE=swamytk]I too get the same screen of "JUST EMPTY BROWN SCREEN WITH MOSTLY HIDDEN TASK BAR". Nothing working. No Response for Mouse Click. I have installed fluxconf and menu also. Any clue? I was using fluxbox in Mandrake 10.0 nicely. It is a heaven.[/QUOTE]

I got my problem solved. I had selected en_IN as my locale setting (Indian English). Fluxbox did not supported it. I changed it in to en_US (US English). It is going smooth.

---

### Post by chadk on 2006-06-15
I just wanted to try Fluxbox for cedega performance so I installed fluxbox from synaptic but it doesn't seem to have installed fluxbox-generate_menu and I'm a little lost without it since fluxbox loads up basically blank.

---

### Post by zikki on 2006-06-15
Hey,

fluxbox-generate_menu is a  script, which is installed successfully after (sudo apt-get install fluxbox) in usr/share/doc/fluxbox/ directory.

The problem that it doesn't have executable rights initially.

So navigate nautilus (gksudo nautilus /usr/share/doc/fluxbox/) to that directory rightclick on this file and make it executable, then leave nautilus and 

sudo /usr/share/doc/fluxbox/fluxbox-generate_menu

That's it.

UPDATE: also look here [https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox)

---

