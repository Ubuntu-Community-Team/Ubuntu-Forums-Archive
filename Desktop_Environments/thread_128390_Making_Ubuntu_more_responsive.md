---
title: "Making Ubuntu more responsive?"
date: 2006-02-11
forum: Desktop Environments
---

### Post by alvinblank on 2006-02-11
I'd love to stick to linux, but I have this little problem. It don't feel as responsive as 'the other OS'. Like in Firefox, I could scroll this particular forum and it would freeze here and there, not the OS but just the particular screen.

I read up a thread bout making Ubuntu more responsive when high disk usage, I tried that but it doesn't change anything. So I'm wondering what others have done.

Is this a problem with Xorg itself? I've had my nvidia drivers installed and my system is a not too shabby P4 2.0GHz with 512mb RAM on a Intel motherboard.

---

### Post by Horndog on 2006-02-11
To me, it sounds more like a video card problem. What model Nvidia card do you have and which forum are you having problems with?

---

### Post by alvinblank on 2006-02-11
I'm sure it isn't the video card problem. I'm saying in general, Linux/X feel sluggish when compared to Windows. I could be browsing the same forum (this forum), and I'd scroll and Firefox would feel sluggish while it doesn't happen when on Windows.

---

### Post by Lord Illidan on 2006-02-11
You are using firefox 1.07?

Upgrade it to firefox 1.5, either with Automatix or search in the wiki.

Enable dma.

Install nvidia drivers.

---

### Post by dannotdan on 2006-02-11
alvinblank, this really does sound like a video card driver problem. All these pauses are happening while waiting for your video card to process what has already been sent to it. So even though it doesn't seem like video related functions that are slowing down, that is still most likely the root cause. Do a search on this forum for the nvidia howto or the equivelant for whatever chipset your card uses, and chances are your problem will be fixed in ten minutes (including the time it takes to read the howto).

---

### Post by Curlydave on 2006-02-11
This is an easy one to fix, if it's what I think it is. Linux is not really slower than windows, it's the apps. Eg, Firefox and Open Office.

To fix the issue with Firefox, remove the package. Download firefox from the mozilla website, and unzip it a directory.

[http://www.ubuntuforums.org/showthread.php?t=98530](http://www.ubuntuforums.org/showthread.php?t=98530)

---

### Post by alvinblank on 2006-02-11
Yes! Using Firefox 1.5.1 seems to improve alot! Thanks for the headsup.

---

### Post by Lord Illidan on 2006-02-11
What about dma?

Enabling dma is a must, especially if you are playing music, etc.

---

### Post by TheIdiotThatIsMe on 2006-02-11
[QUOTE=Lord Illidan]What about dma?

Enabling dma is a must, especially if you are playing music, etc.[/QUOTE]

How do you enable dma?

---

### Post by crypticreign on 2006-02-11
[QUOTE=TheIdiotThatIsMe]How do you enable dma?[/QUOTE]
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by handy on 2006-02-11
Or, if you want to do it & a few other things the easy way:

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

Allways your choice!  :KS

---

### Post by steve.horsley on 2006-02-11
He is right - Linux does feel unresponsive compared to windows. Sometimes when I switch desktop (something windows can't do), I hear a frenzy of disk activity which I assume is my app being swapped back in, and I can see the app repainting itself button by button and checkbox by checkbox. This is f***ing crazy to me. In my opinion, X should double-buffer so that if an app window is uncovered the "damage" can be repaired immediately, without paging in the entire app and asking it to rebuild the window from the ground up. This would make everything feel very much snappier, and quite possibly reduce how much of an app needs to be paged back in at all when switching windows. I really can't understand why X double buffering wasn't the norm a decade ago.

Enabling DMA probably only has an effect at all by allowing apps to be paged back in more quickly. That's not really fixing the problem.

---

### Post by Curlydave on 2006-02-11
I needa clarify something about my FF comment, and how you said installing 1.5.1 made it much faster. I don't know if it's Firefox 1.07 that makes it slow, or if it's the fact that the Ubuntu package for FF makes it slow. I guess an easy way to find out would be to manually install firefox 1.07 and see how it runs.

---

### Post by macewan on 2006-02-11
[quote=TheIdiotThatIsMe]How do you enable dma?[/quote]

sudo hdparm -d1 /dev/hdc

---

### Post by alvinblank on 2006-02-11
Well, all my hd* has dma (udma5) on by default. I'll do it on the cdrom but I suspose I doesn't help much as I've not been using the drive.

Actually I'm just saying in general, X feel sluggish.

EDIT: Anyone tried getting dapper's Xorg 7 to run on breezy?

---

### Post by TheIdiotThatIsMe on 2006-02-11
[QUOTE=steve.horsley]He is right - Linux does feel unresponsive compared to windows. Sometimes when I switch desktop (something windows can't do), I hear a frenzy of disk activity which I assume is my app being swapped back in, and I can see the app repainting itself button by button and checkbox by checkbox. This is f***ing crazy to me. In my opinion, X should double-buffer so that if an app window is uncovered the "damage" can be repaired immediately, without paging in the entire app and asking it to rebuild the window from the ground up. This would make everything feel very much snappier, and quite possibly reduce how much of an app needs to be paged back in at all when switching windows. I really can't understand why X double buffering wasn't the norm a decade ago.

Enabling DMA probably only has an effect at all by allowing apps to be paged back in more quickly. That's not really fixing the problem.[/QUOTE]

To me that's odd, since I use multiple desktops all the time and use 3DDesktop to switch between them, and I never notice a slowdown. Usually I'll run Firefox and Gaim on the 1st desktop, amaroK on the second, and Azureus on the 3rd, and I never experience a slow page in.

---

### Post by handy on 2006-02-11
My machine runs **faster** on Ubuntu 32bit Breezy 5.10, than it does under xp pro' Sp2 + all relevant patches.

Running Ubuntu, I find that I have multiple work areas open that I switch between.  It's normal for me now to have 5 tabs open in Firefox, (like at the moment) & sometimes FF running on another work area with multiple tabs?  I can switch between these instantly when I select a tab, scroll as fast as I want smoothly.

I would **NEVER** do that in windoze... windoze would behave like it was bogged in mud upto it's axles!

I have recently installed on a lower spec' machine than mine, no problems with speed!?

So, naturally, I have to think that there is a strong chance that something is not configured optimally, or broken in Ubuntu, or the cause of your unresponsive system is other than Ubuntu.

I wish that I could tell you how to fix it!

---

### Post by Horndog on 2006-02-11
Just think of all the overhead used by Windows just to call hame your unique ID. 
That's how they track down the machine that write all those nasty Windows diseases and who know what else.
I would never go back to Windows even if it was faster. In which case on my machine it's not.
...and very few could afford all this software that come free with ubuntu and Linux.

---

### Post by clov on 2006-02-11
Same problem here! 
I have a slow system with ubuntu when compared to Win XP. I used to think it was caused by firefox and I stopped using it, but I noticed no differences.
It's not slow when a start a progam (that works normaly), it's slow when I change windows, open menus, those kinds of things.

I don't think that's related with my computer, I'm using a Dothan 1.7GHz with 1.5Gb or RAM and ATI9700- 128MB.
When I'm configuring xeserver-xorg I can't use a kernel framebuffer, could it be the problem?

---

### Post by handy on 2006-02-12
So, if it is slow on the internet only?

Have you turned off **IPv6**?

Enter the following in the Firefox address field:

**about:config**

then enter in the new **Filter** field:

**ipv6**

Then double click on the entry to change it's boolean value to **True**

--------------------------------------------------------------------
**[EDIT:]**  The following can matter too:

**sudo gedit /etc/modprobe.d/aliases**

Change this line: **alias net-pf-10 ipv6**

To this: **#alias net-pf-10 ipv6**

(# = commented out), **Save & Exit**

Now you can forget about ipv6, possibly for years.
---------------------------------------------------------------------

*My machine won't even connect to the internet unless I do that!*

Another thing that can slow your internet connection down, is if you have **Static IP Address** selected instead of **DHCP**, to check this:-

Goto - *Menu:* **System/Administration/Networking** double left click on your ethenet device - usually eth0, this will bring up the **Interface Properties** dialogue.

Now check that the **Connection Settings - Configuration**: pull down says **DHCP**.

DHCP is much faster when changing connections from server to server.

If your setting is Static IP Address, it will take a long time to load a page from a New server. Once on that server the pages should load normally, until a page is called from a different server, then that page will be slow to arrive.

*Disregard the DHCP stuff just mentioned if you [I]**DO*** have a static ip address![/I]

I hope this helps...

---

### Post by Mr Self Destruct on 2006-02-12
Sure, there are some tweaks to be made but you can't honestly claim that the very same computer runs Ubuntu/Gnome as well as Windows XP. Never have I seen Ubuntu's GUI performance approach what you get with Windows and of course, this is on several machines. Everything graphical is slower, Firefox and 2D games very much so. But why?

GTK and X are problably what drags performance down but I'm not about to profile everything so it's just something that sounds reasonable to me. But of course GTK fans will defend GTK and X fans will defend X and so on and we are nowhere.

Windows have had GDI hardware acceleration since well, forever. Anyone know if X uses graphics cards like this?

---

### Post by handy on 2006-02-12
I like your name...

& no, sorry, I'm not biting!

**[EDIT:]  No one likes to be called a liar.**

---

### Post by alvinblank on 2006-02-12
[QUOTE=Mr Self Destruct]
Windows have had GDI hardware acceleration since well, forever. Anyone know if X uses graphics cards like this?[/QUOTE]

Xorg or XGL there will be hardware accelerated?

---

### Post by ritger on 2006-02-12
Actually, there's not a lot of difference (performance wise) between either Windows or Ubuntu on this pc i'm working on. One of the things i like to do on a fresh install is make sure the latest Nvidia drivers are installed, X is using the NvAGP instead of the via_agp driver (search my username on the forum, there's a thread that describes on how to configure this) and that Sideband Adressing and Fast Writes are disabled (no real performance gain, makes my system unstable though).

Next i kill any service i'm not likely to use, the major offender here being Postfix. If you're running a desktop and all you need is the stand alone ssh server for remote access, kill inetd as well. Also check DMA settings for harddrives, and especially CD/DVD drives. As for anything else, just look in the logs once in a while and see if your system is telling you whether something just failed.

One more thing, Nautilus get hungry, real hungry. As do firefox and gam_server (alteration monitor daemon). If you notice Nautilus really slowing down pull up a console and give it a `killall -9 nautilus'. That'll restart Nautilus and it'll be all better again. I have this one in a button on my taskbar (i keep my pc on all the time). 

There's a lot of other stuff you can tweak, but for me these are the major points. Messing with anything else will probably break more then help.

---

