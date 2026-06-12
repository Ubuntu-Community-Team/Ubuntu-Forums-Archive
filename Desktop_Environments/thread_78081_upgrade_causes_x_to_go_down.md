---
title: "upgrade causes x to go down"
date: 2005-10-17
forum: Desktop Environments
---

### Post by smergler on 2005-10-17
hi, i upgraded from hoary to breezy yesterday, and when i try to log into x... it just gives me a black screen... 
when i check the gdm logs,... it says 

Skipping "/usr/X11R6/lib.modules/extensions/libGLcore.a:m_debug_clip.o": no symbols found
Skipping "/usr/X11R6/lib.modules/extensions/libGLcore.a:m_debug_norm.o": no symbols found
Skipping "/usr/X11R6/lib.modules/extensions/libGLcore.a:m_debug_xform.o": no symbols found
Skipping "/usr/X11R6/lib.modules/extensions/libfb.a:fbmmx.o": no symbols found
Warning: font renderer for ".pcf" already registerd at priority 0
Warning: font renderer for ".pcf.Z" already registerd at priority 0
Warning: font renderer for ".pcf.gz" already registerd at priority 0
Warning: font renderer for ".snf" already registerd at priority 0
Warning: font renderer for ".snf .Z" already registerd at priority 0
Warning: font renderer for ".snf.gz" already registerd at priority 0
Warning: font renderer for ".bdf" already registerd at priority 0
Warning: font renderer for ".bdf.Z" already registerd at priority 0
Warning: font renderer for ".bdf.gz" already registerd at priority 0
Warning: font renderer for ".pmf" already registerd at priority 0

any suggestions?
thanks
-smergler

---

### Post by DJ_Max on 2005-10-17
Hi,
Were you watching as you ran the upgrade for errors? It may not have went through correctly, which is a common problem. 

Run
```
sudo apt-get -f install
```

Show me what you get.

---

### Post by smergler on 2005-10-18
$ apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
$

no i did not watch the upgrade... i started it late at night and i fell asleep before it was finished, and woke up several hours after it finished

---

### Post by Murgle on 2005-10-18
can you look further up in your Xorg log? somewhere there is mostlikely a line that has error or something close to it on it

---

### Post by smergler on 2005-10-18
all that is above the previous message is the position of the Xorg log file... which has some other warnings, the config file, and the markers, kernel v., the module loader is present, the build date, the current operating system, the build operating systm, X protocol version (11)
the release date, 
and the fact that its X window system vers. 6.8.2

the warnings in the Xorg log file
the directory "/usr/share/X11/fonts/cyrillic" does not exist and the entry was deleted from font path... same with /usr/share/X11/fonts/CID

fonts.dir was not found or not valid in /var/lib/defoma/xttcidfont-conf.d/dirs/CID: entry deleted from path

Open APM failed (/dev/apm_bios) (no such file or directory)

it ignored request to load module GLcore

the skipping of things mentioned in first post

I810(0): config file hsync range 30-96 khx not within DDC hsync ranges
""              "             vrefresh range 50-160Hx not within DDC vrefresh ranges

(640x350) mode clock 31.5MHz exceeds DDC maximum 0Mhz
and it continues with lots of different resolutions

and then theres also the fonts that were mentioned earlier that didnt work... does this help?

---

### Post by Murgle on 2005-10-18
[QUOTE=smergler]
I810(0): config file hsync range 30-96 khx not within DDC hsync ranges
""              "             vrefresh range 50-160Hx not within DDC vrefresh ranges

[/QUOTE]

this looks like you might have invalid vertical refresh reates and invalid horizontal sync rates.  you might want to try changing them in the Xorg.conf if you know what good ones are for your monitor, you can also try commenting out the lines that declare what the rates are, they should be in the monitor section.

---

