---
title: "Really Slick Screensaver Package &amp; Hard Locking!!!"
date: 2005-04-22
forum: Desktop Environments
---

### Post by raid517 on 2005-04-22
Hi, before I report it as a bug, can anyone else here confirm that the really slick screensaver package does not function correctly under KDE? What are other users experience of this?

GJ

---

### Post by brent on 2005-04-22
Works fine for me. Maybe it's a problem with you GL setup? Do the other GL screensaver work?

---

### Post by raid517 on 2005-04-22
Which video card do you have? I have a radeon X800. Yes all other GL screensavers work. Although the really slick screensaver package was omitted from the official Kubuntu release. I wonder if this was for a reason?

I just booted into Linspire 5.0 which has them installed by default - and I encountered no lockups whatsoever. So it doesn't seem to be a hardware issue.

Moreover I can run them individually by simply double clicking them on the desktop. It is only when I try to run them from within KDE control that I hit any snags.

GJ

---

### Post by brent on 2005-04-22
I've got a Nvidia 6200 TC. Do the Flux and Euphoria screensavers that come with KDE work, but the ones that came with Really Slick Screensavers not?

---

### Post by raid517 on 2005-04-22
No those specific screensavers don't work at all. also OpenGL performance in games really sucks. Which has kind of got me thinking. The last time something like this happend it had something to do with an entry on my /etc/fstab file. But I'm stuffed if I can remember what it was.

Any hints would be appreciated.

It still doesn't explain why I can run them without a glitch outside of KDE Kontrol (or at least outside of the desktop settings applet).

As soon as I try to access them from within KDE control, my system hard locks. (And I mean genuinely hard locks. All keypresses, ctrl, alt backspace/delete/F1/F2/F3 and so on are non functional).

GJ

---

### Post by brent on 2005-04-22
fstab shouldn't affect the graphics.

Some questions:
What's you processor speed?
When you run the screensaver outside of KControl do you get a good frame rate?
Are the ati drivers working properly?
What's your frame rate in glxgears?
Do you have kscreensaver, kscreensaver-xsavers, xscreensaver, and xscreensaver-gl packages installed?
Do you have all the mesa and glut packages installed?

---

### Post by raid517 on 2005-04-23
**fstab shouldn't affect the graphics.**

It does with the ATI drivers as they depend on tmpfs being mounted at the correct location. Unfortunately Kubuntu has tmpfs automatically mounted at a very non standard location (in /dev) and I have no clue how to change this, or even if it is advisable to do so. I could specify it in fstab, but I assume that the selected location is there for a reason.

[B]Some questions:
What's you processor speed[/B]?

Althlon 3800+ 2400MHZ

**When you run the screensaver outside of KControl do you get a good frame rate?**

They look great if that's what you mean. But I don't know what the switch is outside of Kcontrol to turn on the osd framerate counter.

**Are the ati drivers working properly?**

They seem to be. In every other respect.

**What's your frame rate in glxgears?**


```
raid516@linux1:~$ glxgrears
bash: glxgrears: command not found
raid516@linux1:~$ glxgears
27716 frames in 5.0 seconds = 5543.200 FPS
35981 frames in 5.0 seconds = 7196.200 FPS
35967 frames in 5.0 seconds = 7193.400 FPS
35978 frames in 5.0 seconds = 7195.600 FPS
35923 frames in 5.0 seconds = 7184.600 FPS
35975 frames in 5.0 seconds = 7195.000 FPS
```

No problems there.
[B]
Do you have kscreensaver, kscreensaver-xsavers, xscreensaver, and xscreensaver-gl packages installed?[/B]

Yes. I just double checked and I do.

**Do you have all the mesa and glut packages installed?**

Which of these do you think I need? I do know that some parts of the messa opengl implimentation play holy havock with ATI's own opengl implimentation, if you don't know what you are doing.

But as I said I have had at least three other distros installed on this machine - and have never encoutered a similar issue.

It might not rule out hardware, but it makes it less likely.

GJ

---

### Post by raid517 on 2005-04-23
On another note, it doesn't happen at all in XFCE. I like XFCE a lot, but I have been a KDE user for several years, so it would be hard to make the adjustment. Perhaps I will simply have to try to use it until some kind of resolution emerges. Possibly I should have just stuck with a pure debian distro. The chances are with pure debian that with the sheer volume of updates, if you wait a couple of days, most problems solve themselves.

It feels weird opening up synaptic after two or three days and still seeing no updates avialable.

GJ

---

### Post by raid517 on 2005-04-23
One way round it of course would be if I could find a way to use the xscreensaver interface instead of the Kcontol to set my screensavers. But of course I have no clue how to go about doing this.

Anyway I take back what I said about OpenGL performance sucking. I just installed the latest version of Cedega - and finally I was able to have a quick go on Half Life 2 - and it performed pretty much flawlessly. Some of the inintial videos are slightly garbled, but game play is certainly on a par with windows.

Now I feel very encouraged to see what else works.

Although, not wanting to stray from the point, if anyone can help with my initial problem, please feel free to let me know.

GJ

---

### Post by brent on 2005-04-23
To set up a screensaver I think you just run xscreensaver and set it up, then you have to start the daemon at start up.

I was having a look at xscreensaver and guess what, I've got the same problem as you, sort of. Most of the screensavers run fine (Flux and Biof are the only ones I really use) but Atlantis and some others are really slow in KControl, but fine in xscreensaver. Also, I can't change the preset in Biof with KControl.

Seems the KDE area of Kubuntu is a bit broken. I'm thinking of going back to Slackware or giving Kanotix a try :-?

---

### Post by raid517 on 2005-04-23
How do you start the daemon at start up? If I knew how to do that I would be more than half way there.

Kanotix is a good bet. I freaked a tad too prematurely with it as it turned on a bunch of services by default that really slowed my hard disk down. But I then read a few days later how easy it would have been to disable these services. 

I wish I had stuck with it. The other advantage is that it is almost 100% Debian Sid compatable, which means that you probably will never learn what a big mistake it is to mix packages from other distros - simply because you will never need to. (For those who don't know, it isn't just different distributions of Linux that are incompatable, even most big name derivitives of Debian are fundamentally incompatable too. Try mixing packages and you will quickly find how fast you can break your system). 

At least when you open up Synaptic in Kanotix you will always find updates - even if you only leave it for a few hours. (20MB+ a day in updates isn't unusual for Sid). They don't call it the mighty apt-get for nothing.

These guys seem happy to live with broken packages almost all the way between releases. (Or at least their update cycle is minimal to say the best). For someone used to a pure Debian world, this is very disconcerting.

Unfortunately I'm kind of stuck with it for now. I have invested a huge amount of work in getting everything up and running as best as I can, so it is a daunting prospect to consider switching right at this exact point in time. Mind you, if Kanotix include Xorg in their next release, I doubt I will be able to resist it.

But you are right, I don't think KDE is something these people are very familiar with. It is possibly the poorest KDE implimentation on any distro I have ever encountered. I think they are Gnome people, who just included KDE at the last moment as an afterthought in an attempt to attract more patrons.

I certainly hope that they get more competant KDE developers on board very soon.

GJ

---

### Post by brent on 2005-04-23
[QUOTE=raid517]How do you start the daemon at start up?[/QUOTE] In the [man page](http://www.linuxmanpages.com/man1/xscreensaver.1.php) it says to run it in KDEs autostart:> USING KDE (K DESKTOP ENVIRONMENT)
 I understand that KDE has invented their own wrapper around xscreensaver, that is inferior to xscreensaver-demo(1) in any number of ways. I've never actually seen it, but I'm told that this is the way you disable it: 
1: Switch off KDE's screen saver.
 Open the ``Control Center'' and select the ``Look and Feel / Screensaver'' page. Turn off the ``Enable Screensaver'' checkbox. 
2: Find your Autostart directory.
 Open the ``Look and Feel / Desktop / Paths'' page, and see what your ``Autostart'' directory is set to: it will probably be ~/.kde3/Autostart/ or something similar. 
3: Make xscreensaver be an Autostart program.
 Create a file in your autostart directory called xscreensaver.desktop that contains the following five lines: 
[Desktop Entry]
Exec=xscreensaver
Name=XScreensaver
Type=Application
X-KDE-StartupNotify=false


 Now use xscreensaver normally, controlling it via the usual xscreensaver-demo(1) and xscreensaver-command(1) mechanisms.[QUOTE=raid517]But you are right, I don't think KDE is something these people are very familiar with. It is possibly the poorest KDE implimentation on any distro I have ever encountered. I think they are Gnome people, who just included KDE at the last moment as an afterthought in an attempt to attract more patrons.

I certainly hope that they get more competant KDE developers on board very soon.[/QUOTE]They're KDE guys, but there's only two of them and they haven't had much time to sort it out yet

---

### Post by raid517 on 2005-04-24
Well he is right, that is a much better solution anyway.

Actually there are quite a few graphical and other gltiches with this version of Kubuntu/KDE. Like the way sometimes my user preferences are saved and sometimes they are not. (Such as show hidden files and folders - I had to edit a text file to finally get this to go away after I was finished with it, because it wasn't saved in KDE preferences) or like my route for my router not sticking, no matter how many times (as su) I entered it and hit apply, or preferences telling Opera to use java not being saved, or graphical tears on menu bars after a screensaver stops running, or the Konqueror download dialog jumping to 100% and sticking there as soon as I click on a download, no matter how big that download is - or the way I can't accurately copy a large number of small files from a CD drive (particularly game CD's) on to my harddrive without it skipping files or corrupting them - and maybe one of 100 or more other bugs I have reported already.

And when are we going to see some updates? How about a new kernel? How soon will it be after kernel 2.6.12 is released before we can have it?

I don't want to seem impatient, but I have encountered so many bugs and inconsistancies that I am finding them really quite hard to live with.

None of this would have been a problem if these guys had at least made an attempt to maintain binary compatability with the Debian unstable source tree. Because at least then you have thousands of developers and really quite well tested applications and lots of new updates every day - so that if you have a problem on one particular day, it probably won't (with updates) persist for very long.

It would at least have taken the heat off of the developers and would have lessend the pressure on them where right now it seems they have to do it all by themselves.

I think that is the main bug here. Broken binary compatability. IMHO that is the real issue that needs to be addressed.

GJ

---

