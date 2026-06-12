---
title: "Finally! A fix for our Azureus Problems!"
date: 2006-05-25
forum: Desktop Environments
---

### Post by QuacoreZX on 2006-05-25
Of most primary concern that I am addressing this post is to anyone and everyone out there annoyed by Azureus' refusal to allow those error messages on the bottom right of the desktop to close and the lack of a tray icon next to their clocks.  I have a fix for all of you, and its name is....CVS.  Yup, you saw that comin, I know it.

Anyways, here's how to do it.  First and foremost, I must admit this plugin for Azureus is indispensable:

[http://azureus.aelitis.com/wiki/index.php/Azureus_CVS](http://azureus.aelitis.com/wiki/index.php/Azureus_CVS)

In order to install it, you must follow these instructions

1) download the .jar file of the plugin
2) go into /home/<username>/.azureus/plugins
3) create folder of the EXACT SAME NAME as the .jar file, minus the ".jar" part of course
4) copy the plugin file you downloaded into there
5) restart Azureus.

The plugin should now be installed.  Open it up inside Azureus, and click the refresh button and hopefully a torrent will automatically be started grabbing the latest CVS build.  In order to get this thing installed, up, and running immediately, simply do this:

1) Open the AZCVSUpdater plugin
2) click the settings tab
3)check "Auto download latest", "...Insert", and "and restart immediately"

As soon as your download finishes for the latest CVS, Azureus will immediately restart and...Ta Da!  There now appears an icon in your top right corner, and if any error windows come up, just click and they're gone!

---

### Post by it.henrik on 2006-05-25
the cvs version .. on auto download ... expect to get some unstable versions. I was running the same a while back when I was writing plugins for azureus. Not recommended for avarage joe :)... at least by me.

Have you tried the version from [www.getazureus.com](www.getazureus.com) ?

---

### Post by QuacoreZX on 2006-05-25
2.4.0.2 is the old one I had before, yes.  Worked awful.  Sure, CVS is unstable, but instability here and there with bug fixes is something I can live with.  If anyone fears the CVS so, be it his or her prerogative not to touch it I suppose.

---

### Post by BitTorrentBuddha on 2006-05-25
didn't work for me = \

---

### Post by mlind on 2006-05-25
I've never had any stability problems with Azureus unstable versions from CVS.
Newest beta really fixes dialog hiding issues.

---

### Post by BitTorrentBuddha on 2006-05-25
selecting the plugin from the plugin menu just brings up a blank tab, and there's no way to check for updates under options -> plugins

---

### Post by mlind on 2006-05-25
[QUOTE=BitTorrentBuddha]selecting the plugin from the plugin menu just brings up a blank tab, and there's no way to check for updates under options -> plugins[/QUOTE]

I dunno, I'm using locally installed Azureus and I don't 
have problems like that

You can always get latest Azureus2.jar that's CVS from
[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

Just download it and replace your current Azureus2.jar.

---

### Post by souled on 2006-05-31
After I download the newest jar file, I get this error: ```
[05/30 10:43:01 PM]  Major Error Inserting/Restarting please report to omschaub@users.sourceforge.net
``` Any ideas?

---

### Post by mlind on 2006-05-31
[QUOTE=souled]After I download the newest jar file, I get this error: ```
[05/30 10:43:01 PM]  Major Error Inserting/Restarting please report to omschaub@users.sourceforge.net
``` Any ideas?[/QUOTE]

That's probably error from AZCVSUpdater. 
Have you tried to replace the .jar file manually?

---

### Post by souled on 2006-05-31
Where does the jar file get downloaded to, and where to I put it?

---

### Post by mlind on 2006-05-31
[QUOTE=souled]Where does the jar file get downloaded to, and where to I put it?[/QUOTE]


Development version of Azureus2.jar can be downloaded from
[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php) (current is Azureus2403-B35).

I have installed Azureus locally, so I don't know where Ubuntu packages actually
install the file, but you can search for it, for example

```

slocate Azureus2.jar

```

if you don't get any hits, execute *sudo updatedb* and try again. Or just search
for 'Azureus'.

---

### Post by whatrucrazy on 2006-08-20
in my dapper install the Azureus2.jar file lives in /usr/share/java. i just moved the old file (after shutting down azureus), downloaded the new one, renamed it "Azureus2.jar", restarted the programme and bingo, new version. now no popup problems if you go into tools- options- interface- display, and change the "automatically hide non error popups..." to "0".
at least that did it for me; some people seem to have rid themselves by using a new build, but i did this and its all good.

anyway read this thread for more info on where to get the file etc...
[http://www.ubuntuforums.org/showthread.php?t=179033&highlight=azureus+bug+popup](http://www.ubuntuforums.org/showthread.php?t=179033&highlight=azureus+bug+popup)

---

### Post by PreachersPoker on 2007-03-02
This did not work for me.  Here is a solution that did.

Download lastest Azureus build from
[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php) to /usr/share/java

Start terminal

cd /usr/share/java
sudo mv Azureus2.jar Azureus2.old
sudo mv Azureus3xxxxx.jar Azureus2.jar #replace Azureus3xxxxx.jar with actual file name that you downloaded
exit

Start Azureus

---

