---
title: "Firefox 1.5.05 Keeps crashing Kubuntu 6.6.01"
date: 2006-09-13
forum: Desktop Environments
---

### Post by comfortablynumb on 2006-09-13
I put Kubuntu 6.6.01 on my IBM T23 laptop, Pentium III M 1.13 Ghz with 512MB of Crucial ram, KDE (stock theme) 1024x764

Everything is installed and recognized as it should be. Ever since I installed Firefox 1.5.0.5 and been using it, it just randomly locks up, and I have to terminate the process, I haven't been able to duplicate the problem to any one particular website or anyone script as of yet. 

Has anyone come across this, or know how I can track the crash to trouble shoot this problem?

Thanks in advance

---

### Post by llamakc on 2006-09-13
Any large number of extensions installed?

---

### Post by comfortablynumb on 2006-09-13
No extensions at all at this time, just the clean install from apt-get

---

### Post by llamakc on 2006-09-13
Try running it from a Terminal like:

firefox

and leave that terminal up or minimized. Next time it crashes see what is logged to the terminal & cut-n-paste it for us.

---

### Post by comfortablynumb on 2006-09-13
Thanks llamakc I'll do that

---

### Post by comfortablynumb on 2006-09-13
Well it just happened again, I ran Firefox from Konsole as suggested, I was going through a few websites, with about 3 tabs open, then the browser just froze, I waited several minutes and it didn't generate anything in Konsole, it was just frozen, I finally just clicked the x to close the application and it says it's not responding terminate process? So I choose terminate and it closed, nothing came up in Konsole.

---

### Post by someguyouknow on 2006-09-13
is flash being used on these sites?
I had a similar problem

---

### Post by orb9220 on 2006-09-13
Sounds like a plugin or java issue.
type in address bar
about:plugins
Post java type and version also any plugins that may be using like flash.

---

### Post by comfortablynumb on 2006-09-13
Shockwave Flash

    File name: libflash-mozplugin.so
    Flash Movie player Version 0.4.12 compatible with Shockwave Flash 4.0

    Shockwave is a trademark of Macromedia®

    GPLFLash homepage : gplflash.sf.net

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Flash Plugin 	swf 	Yes
application/futuresplash 	Future Splash 	spl 	Yes
Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_08 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_08 	Java 		Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r63

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by comfortablynumb on 2006-09-13
After I posted that, it looked like I had 2 different versions of Flash some how, I uninstalled the plugin one, restarted firefox and tested flash is still working. I'm hoping maybe it was just because there was 2 different flash versions.

---

