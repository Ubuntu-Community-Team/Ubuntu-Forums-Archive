---
title: "Firefox crashing randomly"
date: 2005-09-04
forum: Desktop Environments
---

### Post by blueturtl on 2005-09-04
Firefox will randomly crash on my system with a segfault. There is no pattern (I cannot recreate the situation for a bug report). I've tried to narrow the field, but to my best knowledge the crashing is just random. Occationally it will occur with a plug-in, occationally just clicking a link on any site. Going to the same site again after restarting the browser everything will work just fine, as if nothing was wrong. Crashing may occur multiple times within a browsing session, or not a single time during a whole day. I have the latest Firefox 1.0.6 from the official Ubuntu repository. I even switched a recently purchased RAM stick with a new one because I suspected it may have been faulty. As far as I know, this only affects Firefox - otherwise the system is stable as a rock. Firefox is the best free browser out there in terms of simplicity. Maybe I should go back to Mozilla? What other options are there? Opera blazes, but is not free and is not as easy to configure for plugins.

---

### Post by arnieboy on 2005-09-04
[QUOTE=blueturtl]Firefox will randomly crash on my system with a segfault. There is no pattern (I cannot recreate the situation for a bug report). I've tried to narrow the field, but to my best knowledge the crashing is just random. Occationally it will occur with a plug-in, occationally just clicking a link on any site. Going to the same site again after restarting the browser everything will work just fine, as if nothing was wrong. Crashing may occur multiple times within a browsing session, or not a single time during a whole day. I have the latest Firefox 1.0.6 from the official Ubuntu repository. I even switched a recently purchased RAM stick with a new one because I suspected it may have been faulty. As far as I know, this only affects Firefox - otherwise the system is stable as a rock. Firefox is the best free browser out there in terms of simplicity. Maybe I should go back to Mozilla? What other options are there? Opera blazes, but is not free and is not as easy to configure for plugins.[/QUOTE]
run firefox from terminal, that way u will have a debugging trace when it crashes. copy and paste it here.

---

### Post by invisage01 on 2005-09-04
my firefox is starting to crash as well.. im working today so i havn't had any chance to check out any reasons for it.. but i have only started to notice after i installed the flash plugin.. but i wasn't really paying too much attention to it as i had only been running ubuntu for a few days before this.. I do definately know that my browser will crash when going to [http://www.weather.com ](http://www.weather.com ) - sometimes on the first page.. other times when i do a search.. 

i'll keep you posted on what is happening with mine.. i'll run from the terminal next time and see if it comes back with anything... 


Iain.

---

### Post by Weav on 2005-09-04
Firefox sometimes crashes for me randomly as well. Anywhere from once daily to maybe 5 times a day, i will try running from the terminal and see what it says

---

### Post by rastilin on 2005-09-04
There are several other browsers that use the same core as firefox, you could try using Knoqueror for KDE or Epiphany for Gnome and they're both open source to my knowledge.

My firefox install works perfectly at 1.0.6 but does crash if I try to save a picture and the connection lags too badly.

---

### Post by jassyjohn on 2005-09-05
I had problems with FireFox crashing while printing, so I installed the development version "Deer Park Alpha 2".   After copying over my plugins, all works fine.

John

---

### Post by blueturtl on 2005-09-05
> run firefox from terminal, that way u will have a debugging trace when it crashes. copy and paste it here. 

Warning: too many lines!
Segfault

This is all that is ever outputted. The number of warnings might differ, but in the end it's always a segfault. To fix the problem I'm currently using Mozilla 1.7.10 (would never even have switched, but since Firefox was the Ubuntu default, I didn't bother installing it until now). We shall have to see.. since ultimately they are the same browser, if Mozilla works I will stick with it instead.

---

### Post by blueturtl on 2005-09-13
> Poorly designed or incompatible Extensions can cause problems with your browser, including make it crash, slow down page display, etc. If you encounter strange problems relating to parts of the browser no longer working, the browser not starting, windows with strange or distorted appearance, degraded performance, etc, you may be suffering from Extension or Theme trouble. Restart the browser in Safe Mode. On Windows, start using the "Safe Mode" shortcut created in your Start menu or by running firefox.exe -safe-mode. On Linux, start with ./firefox -safe-mode and on Mac OS X, run:

    cd /Applications/Firefox.app/Contents/MacOS/
    ./firefox-bin -safe-mode

When started in Safe Mode all extensions are disabled and the Default theme is used. Disable the Extension/Theme that is causing trouble and then start normally.

This is from the Firefox FAQ.
So far I've experienced far less crashes with Mozilla (has crashed two times on me, once today just a while ago which lead me to investigate further). Mozilla is also faster than Firefox (what's this.. wasn't Firefox supposed to be the lightweight version!). The problem is that I don't think it'll be that easy to find out which of my plug-ins is causing the crashing, because of it's random nature.

I currently have the following plug-ins installed:

Shockwave Flash 7.0 r25
mplayerplug-in 2.85
Java(TM) Plug-in 1.5.0_02-b09

With these the web is a much nicer experience and I'd hate give any of them up.  :-|  Of course if there was an update or a patch I could try that.. but why are the Linux versions of Mozilla/Firefox so much more prone to crashing than their Windows counterparts? I think since the OS is much more stable, so should the applications be that run on top of it. /end idealism

---

### Post by agm642 on 2005-09-13
I have all those plugins installed and it has never crashed for me...

---

### Post by blueturtl on 2005-09-13
Ok, one hint for everyone is to make sure your plugins are *properly* installed.
I've just installed new versions of these plugins:

mplayerplug-in 3.10
Java(TM) Plug-in 1.5.0_04-b05

and reinstalled this:
Shockwave Flash 7.0 r25

Turns out there are some inconsistencies in some parts of plugin installation:

I noticed when installing the newer mplayerplug-in, that globally the files ending ".so" go into the mozilla/plugins folder whereas the ".xpt" files fo into mozilla/components. The automated Flash Player installer by default installs both types of files under /plugins. I'm not sure what the implications are, but I unzipped the installer and copied the files by hand this time doing it the same way that mplayerplug-in is supposed to be installed and guess what: Flash still works. In the case of Java I simply updated the symbolic link to point to the new file.

I'm curious about this and we shall see if the updates and fiddling pay off.
I no longer use Firefox, but my girlfriend does and I'm sure I'll hear her opinion about things if it continues to crash on her.  :razz:

---

