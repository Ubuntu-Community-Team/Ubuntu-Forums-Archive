---
title: "azureus wont start"
date: 2006-08-08
forum: Desktop Environments
---

### Post by finite9 on 2006-08-08
Ok, so I've read several thread here and on linuxquestions about azureus not starting and all seem to imply that its Java thats the problem, but I installed 6.06 and the got azureus from universe and it worked fine...without blackdown java or official sun java.  This is because it uses the open source java runtime.  I have never had any other Java on my system.  Lately, azureus wont start (having being working fine for several months), so I suspect that an offical update killed it in some way, as I very rarely install new software.

Does anyone else have same problem?  I start azureus and get splash screen and a popup box, but no gui.  If I start from command line, I get loads of java messages but no gui.  My LAN traffic goes to 100% when I start azureus!???

If I start azureus from icon then start another instance from command line, it complains about another instance already running but it actually pops up the gui, but no torrent window, just the menu bar, so all I can do is shutdown the gui again.

Is this something that the package maintainer needs to look into?  Seems like the package has been broken by official update.

--finite9

---

### Post by em3raldxiii on 2006-08-08
This is a semi-known problem, though I don't know if there are any universal fixes.  I have seen it reported elsewhere, and I actually have a similar problem:  start azureus fine, get GUI fine.  Minimize or change workspaces = azureus vanishes but stays running.  Can't open GUI.
 
Solution for me:  Open your system monitor, find Java, KILL process.  Now you can start Azureus again.  (or you can killall java in terminal).
 
Is there any time where you *do* get to see the Azureus GUI?

---

### Post by finite9 on 2006-08-09
Well, killing java doesn't help...the only process started when  I start Azureus is CIJ...GJI...CJI (sorry if the acronym is wrong - i mean open source java but can *never* remember the acronym).

If I kill it, it kills azureus.  I start azureus again and get a new java process - why is there no separate "azureus" process?

--finite9

---

### Post by em3raldxiii on 2006-08-09
Azureus requires the Java runtime environment in order to function.

I am not familiar with the open-source-java that you are using, so I cannot speak for it directly, but I can't help but to be suspicious that perhaps it is the cause of your problem.  Not sure though.

As an interim fix, there are a number of other bittorrent client programs that might suit you.  I'll see if I can dig one up for you.  (I use Azureus too, it's unfortunate it's causing you problems).

---

### Post by em3raldxiii on 2006-08-09
Look up ABC and Bitornado ... I haven't used them though.

---

### Post by finite9 on 2006-08-09
Hi!

Well, If I do a new install of 6.06, without updating it immediately, and install Azureus from the universe repo, it loads a load of other open source Java modules at the same time as dependencies.  You never need to install Sun Java or Blackdown Java to make Azureus work (strong statement there..hope my memory serves me well otherwise i'll have to eat my hat).

I have *never* installed Sun Java or Blackdown but Azureus *used* to work for me until recently!  As I mentioned before, I rarely install new software, so I suspect an official update has broken the package in universe.

I actually use the bt client in the main repository with the gnome nautilus plugin, as this fulfills most of my needs.  There are more options in azureus but i've never used most of them even when I used it in windows.  I haven't figured out how to change the port in the official bt client or how to start my own local tracker and host torrents, but I saw that the man pages explained how to do this.  Considering the memory usage of Azureus and the current fact that it doesn't work, I think i'll stick to the less pretty but more efficient official bt client.

--finite9

---

### Post by em3raldxiii on 2006-08-09
Hmm, did you file any official bug reports about it?

---

### Post by finite9 on 2006-08-10
turns out I was wrong about an official update killing Azureus...I re-installed i386 version of Ubuntu 6.06 and didn't update anything.  Instead I installed all my software from the repositories including azureus.  This was a mistake, as I should have only installed Azureus, but I don't have time to re-install again today.  Anyway, after installing the following software (see below), Azureus would not start and has the same behaviour (this is with the 2.6.15-23 kernel), so I guess I can rule out any official update as being the problem.  Maybe I'm completely wrong about Azureus working in the past without Java, but the thing is, that if I now install sun-java5-jre from the repositories, Azureus still doesn't work!

sudo apt-get install libdvdread3 gparted inkscape kino ssh xchat-gnome build-essential vorbis-tools gaim fakeroot linux-kernel-headers automake1.4 libstdc++5 totem-xine totem-xine-firefox-plugin f-spot kinoplus tor privoxy scite audacity vlc vlc-plugin-alsa wxvlc videolan-doc gnomebaker revelation module-assistant azureus gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

---

### Post by maniacmusician on 2006-08-10
save yourself a lot of trouble, install azureus, and java, with automatix. worked perfectly when I did it.

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

you can also install a lot of other handy apps with it.

---

### Post by finite9 on 2006-08-10
I've steered clear of automatix because it is mostly useful for getting flash and java and win32codecs but i have an amd64 laptop at home and neither flash nor win32codecs work on amd64 so there wasn't really any point.

Maybe I have to get back to installing Blackdown Java or getting the binary from Suns website instead of getting sun-java5-jre from the repos.

UPDATE.  Actually, I scrolled down a bit to the bottom of this thread to the 'similar links' section and there is a post there by clarke.rainey that has the exact same problem as well as several suggestions for fixes.  Seems like Azureus is not working properly at all.  As I have used Dapper since flight 5, this could explain why I remember it working ok with open source Java.  Seems like the current solution is to install Sun java from repos then (the part I didnt do) update prefs so that the system uses the new Java (see other post).

UPDATE-2:  I installed sun-java5-jre and then did the following:

sudo update-alternatives --config-java

and chose Sun Java, and now Azureus works fine.

---

### Post by mwshook on 2006-08-16
Thanks! This works perfectly. Although I think you meant to type 

sudo update-alternatives --config java

(without the hyphen)

> **finite9 said:**
> 

UPDATE-2:  I installed sun-java5-jre and then did the following:

sudo update-alternatives --config-java

and chose Sun Java, and now Azureus works fine.

---

