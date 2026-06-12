---
title: "Help me switch!"
date: 2010-04-11
forum: Desktop Environments
---

### Post by vek on 2010-04-11
Its about that time of year again when I feel like its about time I gave it another try to switch to Ubuntu, since I desperately want to get away from both the mac and vista/seven, and my XP is aging rapidly...

However, it seems that I just can't get all the way there.  Perhaps its a configuration error, or some of you have advice for me to nail down the final few problems I'm having.  Or perhaps you can point me to the appropriate fixes or projects to work with.  At the very least, I figure sharing my experiences with this all can have some sort of constructive purpose.  For the record, I'm on a standard core 2 duo intel desktop, with about 2gb of ram, and a perfect record under XP.  (No crashes, halts, BSODs, etc, ANYTHING, for over 2 years).  It has a nVidia 9800 GTX, if that helps.

The current problems I have with Ubuntu are basically just general stability problems, and general uncertainty.  For example, my desktop gui will at some point in the day just randomly lock up, and I have to switch to a terminal and do a GDM stop / restart.  This happens in a number of circumstances (eg, windows opening/closing, etc) and is obviously unacceptable as it loses any work in the apps I'm running, disconnects IM sessions, kills any persistent connections, destroys downloads in progress, etc.  I'm not sure what would prompt this as I'm running stock ubuntu, with the standard nVidia drivers it suggests I install.  One time the screen started going haywire, flashing dots all over the place, and getting all progressively more corrupted until again X froze.  There seems to be no rhyme or reason to it.  I'll be typing away in a terminal and it will lock mid-sentence.  I'll have an IM pop up and it will die while I'm typing a response.  This happens rarely, but even once is more than I've seen in XP in two years.

Now I know I could turn desktop effects off, but I use the magnifier as well as the placement / scale effects to increase productivity, and its what gives it the edge over XP.  In addition, the same video card is known to perform flawlessly with similar flashy effects under windows Seven and Vista.  It's not a problem with the card.  What am I doing wrong?  Is there anything I can do?  This is a blocker level problem - I can't switch with such an issue present, and I'm not going to turn effects off, (I may as well stick with XP, its far more usable than gnome without effects) or switch to Seven where the effects stay on AND it doesn't crash either.

That's the one issue.  The other issue is far more mysterious.  Its like the package manager went haywire and just started randomly uninstalling stuff.  Except I never told it to.  The most recent case was with Jungle Disk, which isn't even installed via the the synaptic package manager.  (But I suppose since its a DEB it is kept like that).  I had it installed, it was ticking away perfectly, I rebooted, it was not there anymore.  Its configuration directory was there, but the entire package was gone, its icons, its binaries, everything.  This was on normal shutdown, not even a fsck-enducing crash or anything.  Its like the disk went back in time.

This also happened when I ran the computer Janitor and it ate Adobe Air but that at least is a known issue, not quite the same as Jungle Disk.  The idea that every time I switch the machine off, it could come back with missing functionality or new stuff wrong with it... no, that doesn't seem like a good idea.  I need certainty.

Now, this is not nitpicking - I honestly need the stability and certainty that so far, only XP has provided me with.  I'm serious about switching, but I have some minimum requirements, one of which is that my desktop doesn't randomly delete files / uninstall things / freeze up without warning.  I'm serious about switching, enough so that I've already ported my 'scratch-an-itch' roll-my-own Qt custom micro video library application over to linux, (the one I use on windows), and added LIRC support (had to learn how to do that!), just so I could keep using my windows MCE remote to watch my shows.  I'm not afraid to recompile / hack away at code to get things just right, but that doesn't help me in this situation as its just general flakiness in general, and 'X randomly locks up' is not something I can nail down to a particular source code line...

Also, what's a good way for me to publish all this code I've written?  Its probably a useless video library in comparison to stuff like boxee and so forth, but hey, at least it contains cool examples of how to thumbnail videos, keep histories, interface Qt with many database threads, etc... I'm thinking launchpad?

Anyways.  If someone can help me tie down these last few loose ends, it'd help a lot.  For the time being, I'm posting from the safety of a stable XP session until I can trust the footing I'm on.  If nothing else, at least its feedback on the experiences of someone like me trying to switch.  Trying hard.  I've sunk weeks into this.  I can only imagine the stumbling blocks in place of average users trying to get their IR remotes to work who don't know how to download source, identify usb ID numbers, alter the kernel module, and recompile/load...

---

### Post by stoush on 2010-04-11
I can perhaps help you on the X front...
Since you have an Nvidia card, make sure you got the most up to date driver installed for it. Start up Synaptic Package Manager and search for NVidia.

I am using driver version 185.18.36. You can check what version you are on by System-> Administration -> NVIDIA X Server Settings

Most of the Windows Manager/X crashes come down to a bad version of device driver used (in my case anyway).

---

### Post by stinkeye on 2010-04-11
Wait a few weeks for the release of lucid and try that.
or
Try using the latest nvidia driver from the nvidia repository.
[_**[COLOR="DarkRed"]How To Install Nvidia 185.xx, 190.xx and 195.xx Drivers In Ubuntu, From A Launchpad Repository[/COLOR]**_]("http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html")
I am currently using 195.36.15 with no problems on a 9400GT card.

---

### Post by jflaker on 2010-04-11
I dual booted for about a month, then just dove in head first....

Moving mail from outlook was the biggest pain....solved by using imap to google and moving mail to it. then moved it back once over on Linux.  

Otherwise, I never looked back...it's been 4 years now...

---

### Post by vek on 2010-04-12
Thanks for the advice so far.  I'm giving the 195 drivers a try, since I'd rather switch sooner than later.  

As for applications mysteriously disappearing, I'll keep my eye on it, but I THINK it could be the 'computer janitor' to blame.  It seems to see all manually installed debs that I have installed as not having been manually installed, and instead being dead dependencies, so it kills them...

This might be a known bug.

Here's hoping for no more X.org freezes.  For the record, I was using whatever the latest 'ubuntu official' ones were, 185.xxx, so perhaps I'll have more luck with this.

(To be honest, it seemed more like a bug in X or compiz than it did a bug in the driver, at least, when it all froze up.  When it started spewing random dots and scanlines all over, that looked more like a driver bug)

---

### Post by richardkwong on 2010-04-12
This is the 1st time I  boot the CD (with Ubuntu 9.10 ISO image) on my HP Notebook (Model CD4510s) (Dual Core T4400 2.2Ghz , 2GB RAM, 320G HardDisc, 16.3 inch 1360x760 display)
running Windows7 Home Premium.
 
I have not installed the Ubuntu 9.10 yet but it can boot up and run using the Notebook's internal RAM memory.
 
I can use the Ubuntu Firefox to surf the internet under this condition.
 
I can also view the HardDisk 's Windows7 files and file folder.
 
However, I just accidentially DRAG the HardDisk C: drive <Program files> foler onto another directory <C:\temp\). 
 
After I remove the Ubuntu CD and reboot my Notebook.
 
Windows7 boot up normally, but I cannot run any windows program (eg. Internet Explorer8) installed under this folder.
 
I recognised the <Program Files> folder is not under C:\.
 
I boot up the Ubuntu 9.10 from the CD again without install Ubuntu 9.10.
 
I use the admin->computer to DRAG the <Program Files> folder from Hard Drive C:\temp back to HardDrive C:\      again.
 
Then I shutdown and remove the CD and boot up Windows7 again.
 
Now Windows7 just keep on saying <c:\Program Files  folder is corrupted , please run utility CHKDSK>
 
I think Ubuntu 9.10 has modified the Folder's ownership when I DRAG it back and forth . Windows7 cannot read this folder any more since the ownership is changed from Windows7 administrator to Ubuntu.
 
Can anyone provide a solution to me such that I do not require to re-install all my Windows7 programs again ?/
 
thanks and regards !
 
:(
-ricky-

---

### Post by agnes on 2010-04-12
> Its like the package manager went haywire and just started randomly uninstalling stuff. Except I never told it to. The most recent case was with Jungle Disk, which isn't even installed via the the synaptic package manager. (But I suppose since its a DEB it is kept like that).
Computer Janitor deletes all .debs you did not install through Synaptic if you let it do its default way (clicking "clean up" or something). It is a really bad program.
Maybe you checked something in Computer Janitor to "clean up" stuff regularly automatically? (Or something along those lines... I don't even know if that's possible because I uninstalled it after one first try and recommend everyone to do so.)

You could give a try to Debian stable? It's what its name says.
Mandriva is fine for beginners too, it uses rpm packages, so your package problems may disappear (or will at least be very different).
PCLinuxOS is specifically aimed at switchers from Windows and people say it's quite stable.
Slackware is stable too in my experience but installing is less simple.

---

### Post by vek on 2010-04-16
After installing the new video drivers I have not had trouble for a couple days.

Most recently I had jungle disk lock up the entirety of compiz, which is really strange, considering all it was doing was opening the file menu.  It does this repeatably.  However, I simply switch to a terminal and kill it, and when I switch back, all is good.  If I didn't already know my way around linux to some degree, and I was a naive user, that'd be a 'crash reboot' though, so still a poor performance.

Other than that, it's been pretty good.  Now to get a PPA set up so I can start working on some FOSS stuff :)

---

