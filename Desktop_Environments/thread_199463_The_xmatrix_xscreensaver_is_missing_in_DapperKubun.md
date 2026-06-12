---
title: "The xmatrix xscreensaver is missing in Dapper/Kubuntu."
date: 2006-06-18
forum: Desktop Environments
---

### Post by HippoMan on 2006-06-18
I recently did a fresh install of Dapper/Kubuntu, and I can't seem to get the xmatrix screensaver working.  I've seen a number of messages here concerning conflicts between gnome-screensaver and xscreensaver, but nothing for dealing with what seems to be a similar situation under KDE.

I have installed (and re-installed, and re-installed, and ...) the following packages, but xmatrix still doesn't appear among the list of screensavers under **Appearance & Themes -> Screen Saver** in the KDE Control Center:[INDENT]apt-get install xscreensaver
apt-get install xscreensaver-data
apt-get install xscreensaver-gl
apt-get install xscreensaver-data-extra
apt-get install xscreensaver-gl-extra
apt-get install kscreensaver
apt-get install kscreensaver-xsavers
[/INDENT]I'm not sure if any of the other xscreensaver hacks appear there, either.  They all used to appear just fine under Breezy/Kubuntu.

Any ideas about how I can get xmatrix to appear in the list of screen savers under KDE?

Thanks in advance.

---

### Post by darkpark on 2006-06-18
It's possible that they took it out completey.  check the /usr/share/xreensaves/config/ directory.  see if it listed there.

---

### Post by HippoMan on 2006-06-18
Thank you.  I checked, and it's indeed listed there, and the config file is world readable.

Here are the contents of /usr/share/xscreensaver/config/xmatrix.xml:
```
<screensaver name="xmatrix" _label="Xmatrix">
    <command arg="-root"/>
    <select id="size">
        <option id="font1" _label="Small Font" arg-set="-small"/>
        <option id="font2" _label="Large Font"/>
    </select>
    <select id="mode">
        <option id="matrix" _label="Matrix Encoding"/>
        <option id="binary" _label="Binary Encoding" arg-set="-binary"/>
        <option id="hex" _label="Hexadecimal Encoding" arg-set="-hexadecimal"/>
        <option id="dna" _label="Genetic Encoding" arg-set="-dna"/>
        </select>
    <select id="fill">
        <option id="both" _label="Synergistic Algorithm"/>
        <option id="top" _label="Slider Algorithm" arg-set="-top"/>
        <option id="bottom" _label="Expansion Algorithm" arg-set="-bottom"/>
    </select>
    <number id="delay" type="slider" arg="-delay %" _label="Speed" _low-label="Slow" _high-label="Fast" low="0" high="20000" default="10000" convert="invert"/>
    <number id="density" type="slider" arg="-density %" _label="Density" _low-label="Sparse" _high-label="Full" low="1" high="100" default="75"/>
    <hgroup>
        <boolean id="trace" _label="Run Trace Program" arg-set="-trace"/>
        <boolean id="knock" _label="Knock Knock" arg-set="-knock-knock"/>
    </hgroup>
    <string id="phone" _label="Phone Number" arg="-phone %"/>
    <_description>

Draws dropping characters similar to what is seen on the computer 
monitors in "The Matrix".

See also "glmatrix" for a 3D rendering of the similar effect that
appeared in the title sequence of the movie.

Written by Jamie Zawinski.
  
    </_description>
</screensaver>
```

---

### Post by HippoMan on 2006-06-19
I may not have made it clear that although the xmatrix.xml file exists, that screensaver still does not appear among the ones that are listed in the KDE control panel.

Any ideas as to why I'm not seeing it?

Thanks.

---

### Post by asimon on 2006-06-22
See [Bug #48056](https://launchpad.net/distros/ubuntu/+source/kdeartwork/+bug/48056). The problem is that kscreensaver-xsavers is missing the hooks from all the extras screensavers and xmatrix is in xscreensaver-data-extra, thus is won't appear under KDE.

A workaround: Use GLMatrix ;-)

---

### Post by HippoMan on 2006-06-24
Ah ... thank you very much for the bug reference, and the GLMatrix suggestion.

Yeah, I know about GLMatrix, but it just doesn't have that traditional Matrix effect that I have come to love. :)

I ended up using another workaround: I disabled kscreensaver and now am using xscreesaver, directly.

Once the bug gets fixed, I'll just go back to kscreensaver.

---

### Post by HippoMan on 2006-06-24
P.S. -- is there a kscreensaver or kdeartwork config file somewhere into which I can put the missing hooks for xscreensaver-data-extra and xscreensaver-gl-extra while I'm waiting for the bug fix to work its way through the system? ... or is the list of hooks instantiated at compile time in kscreesaver-xsavers?

---

### Post by erik-the-red on 2006-06-30
What about for Xubuntu? Which packages do I need to install for Xmatrix to show up? GLMatrix is kind of slow on my aging ca. 2000 system.

---

### Post by Peacepunk on 2006-07-01
Xmatrix is missing as well in Gnome-Ubuntu, and I am very sad about it. Furthermore, they simplified the Screenaver application so much that there is no way one can twist anything anymore.

Sad. It looks Ubuntu want's to simplify things to the point the user feels there isn't much freedom left in the system - especially as it is a downgrade from Breezy who allowed for twiting some parameters inside screensavers.

And the new MatrixScrensaver sucks, sorry for the language. Give us back the old 2D / Tunable Matrix please.

@ Hippoman; how do you use "directly" xscreensaver ?

thanks


Peacepunk.

---

### Post by tuxolan on 2006-07-01
This is a workaround for run xmatrix screensaver, until the developers don't fix it.

I describe the steps that i've do under kde (for gnome do the equivalent steps).
[LIST]
[*]Go to kde screensaver settings and _uncheck_ the "Enable Screensaver'" checkbox.
[*]Go into the kde "Autostart" directory (/home/yourUserName/.kde/Autostart), create a file called "xscreensaver.desktop" and with a text editor write this lines:
```

[Desktop Entry]
Exec=xscreensaver -no-splash
Name=XScreensaver
Type=Application
X-KDE-StartupNotify=false
```
[*]make a backup copy of the file "/usr/bin/kdesktop_lock" (**sudo mv /usr/bin/kdesktop_lock /usr/bin/kdesktop_lock.orig**)
[*]Create (with root privileges) another file called "kdesktop_lock" under /usr/bin/ and add this lines:
```
#!/bin/sh
xscreensaver-command -lock
``` make the new file executable with: "**sudo chmod a+x /usr/bin/kdesktop_lock**"
[*]Run this command: "**xscreensaver-demo**" for configure the xscreensaver
[/LIST]

That's all ;)

---

### Post by HippoMan on 2006-07-03
[quote=Peacepunk]@ Hippoman; how do you use "directly" xscreensaver ?[/quote] Here's how I did it under KDE:

- In **aptitude**, I installed the **xscreensaver** package and all other packages whose names are of the form **xscreensaver-***

- In the **KDE Control Center**, I went to **Appearance & Themes -> Screen Saver**, and I unchecked **Start Automatically**.

- I used the **Menu Editor** to create an entry in **Settings** called **X Screensaver**.  In this entry, I set the command to be this:  **/usr/bin/xscreensaver-demo**

- In the **.kde/Autostart** subdirectory under my HOME directory, I created a file called **00-xscreensaver** which contains the following line:[INDENT]**/usr/bin/xscreensaver -no-splash 1>/dev/null 2>&1 &**
[/INDENT]- I then did this:  **chmod +x ~/.kde/Autostart/00-xscreensaver**

- Then, I went to **Settings -> X Screensaver** on the main KDE menu, and I selected and configured the **XMatrix** screensaver.

- Then, I ended my KDE session and re-logged in,

Now, I have the good ol' 2D XMatrix screensaver.

You can also set it up in the way that **tuxolan** did it, and I assume that something similar will also work in Gnome.

---

### Post by djclue917 on 2006-07-15
> **HippoMan said:**
> I recently did a fresh install of Dapper/Kubuntu, and I can't seem to get the xmatrix screensaver working.  I've seen a number of messages here concerning conflicts between gnome-screensaver and xscreensaver, but nothing for dealing with what seems to be a similar situation under KDE.

I have installed (and re-installed, and re-installed, and ...) the following packages, but xmatrix still doesn't appear among the list of screensavers under **Appearance & Themes -> Screen Saver** in the KDE Control Center:[INDENT]apt-get install xscreensaver
apt-get install xscreensaver-data
apt-get install xscreensaver-gl
apt-get install xscreensaver-data-extra
apt-get install xscreensaver-gl-extra
apt-get install kscreensaver
apt-get install kscreensaver-xsavers
[/INDENT]I'm not sure if any of the other xscreensaver hacks appear there, either.  They all used to appear just fine under Breezy/Kubuntu.

Any ideas about how I can get xmatrix to appear in the list of screen savers under KDE?

Thanks in advance.

This should do the trick:

> sudo sed -i -e 's/TryExec=xscreensaver//' /usr/share/applnk/System/ScreenSavers/*

That command will remove the line **TryExec=xscreensaver** from every file in the /usr/share/applnk/System/ScreenSavers/ directory.

After a lot of experimenting, I found out that the line **TryExec=xscreensaver** in the *.desktop files renders the (x)screensaver undetectable by KScreensaver. Thus, any <screensaver>.desktop file that would contain this line would not appear in the list of available screensavers.

I hope that helps. ;)

---

### Post by HippoMan on 2006-07-15
Hmm ... for me, all of the screen savers in **/usr/share/applnk/System/ScreenSavers** do already appear in the **Screen Saver** applet of the **KDE Control Center**, in spite of the fact that **TryExec=xscreensaver** indeed appears in each of those **.desktop** files.

And the **xmatrix** screen saver that I'm looking for does not have a **.desktop** entry in that directory.  The only **xmatrix.desktop** file on my system is this: **/usr/share/gnome-screensaver/themes/xmatrix.desktop**.  But since I'm not using Gnome, this has no effect.

Although the Gnome **.desktop** files appear to be of a format that's different from that of the KDE **.desktop** files, just for the hell of it, I copied **/usr/share/gnome-screensaver/themes/xmatrix.desktop** into **/usr/share/applnk/System/ScreenSavers**.  However, the KDE **Screen Saver** applet still didn't see the **xmatrix** screen saver.  Oh well, I had to try, at least ...

Does anyone know of a way to cause a proper, KDE version of an **xmatrix.desktop** file to get put into **/usr/share/applnk/System/ScreenSavers**, short of my creating this file by hand?

Thanks.

---

### Post by bswilson on 2006-10-26
For gnome users, I found that you can install XMatrix by following this post on Gervase Markham's site:

[http://weblogs.mozillazine.org/gerv/archives/2006/06/knoppix_easter_egg_in_ubuntu.html](http://weblogs.mozillazine.org/gerv/archives/2006/06/knoppix_easter_egg_in_ubuntu.html)

In case the link goes away, here's the 'meat' of it:

```
Actually, you can get Xmatrix running in Ubuntu fairly easily (I use the BoxFit screensaver and you need to do the same thing to get it working).  
Install "xscreensaver-data-extra" and "xscreensaver-gl-extra" (they're in the universe repository; one of those has Xmatrix in it). 
Go back to Ubuntu's screensaver settings and you should see all of the Xscreensavers listed; Xmatrix should be third from the bottom :)
Posted by: Limulus at June 13, 2006 2:08 AM 
```

---

