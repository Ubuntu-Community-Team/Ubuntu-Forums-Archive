---
title: "USB mounting problems flash drives &amp; music player &#61664; Ubuntu vs xubuntu vs mint :"
date: 2020-03-20
forum: Desktop Environments
---

### Post by dokbrown2 on 2020-03-20
[CENTER]



USBmounting problems flash drives & music player &#61664;Ubuntu vs xubuntu vs mint : [/CENTER]


Fordaily use, I use Ubuntu 64-bit [my main desktop] & linux mintMATE 32-BIT [my travel laptop b/c I hate tablets]
Iwas thinking about switching mintcinnamon or xubuntu 64-bit. Will this fix the problem ?
Ido NOT want to fiddle with package or terminal commands but I need tobe able to move docs/music/pics files smoothly between windowsdesktop & linux desktop & android phone.






Iam an appraiser by day
DJby night
    Thuswindows 7 is necessary b/c MS office / APEX SKETCH / ABLETONLIVE/PUSH.
[https://www.ableton.com/en/shop/live/]("https://www.ableton.com/en/shop/live/")
[https://www.apexwin.com/registration/store.php?cat=5]("https://www.apexwin.com/registration/store.php?cat=5")



Fordaily use, I use Ubuntu 64-bit [my main desktop] & linux mintMATE 32-BIT [my travel laptop b/c I hate tablets]
Irip to FLAC via rhythmbox/sound juicer.
Icarry a FIIO player everywhere with me.  [https://www.fiio.com/x1ii]("https://www.fiio.com/x1ii")
Butwhen I mount/copy the FLAC files to my FIIO media player, the FIIOsees but cannot read/play the music files.



Ialso noticed that my main USB flash drive which moves back &forth between Ubuntu & Windows is always showing error messages 
Ubuntu/mintalso have problems mounting the SD card on my old galaxy phone so Ican take pics/videos of my phone.






Ihave upgraded to windows 10.
Inow have the 2[SUP]nd[/SUP]generation X1 & this problem persists.
        Iam convinced the problem is with the USB mounting in linux.
        Doesanyone have any suggestions ?  this is killing my linux experience &pushing me back to windows 10 for daily purposes.
    
AmI the only one having issues with USB mounting flash drives &music player?
Iwas thinking about switching mint cinnamon or xubuntu 64-bit.  Willthis fix the problem ?
Lorenzo
310-708-0104

---

### Post by Autodave on 2020-03-21
What are the USBs formatted to?  Are you properly dismounting them from Win10 *before* you remove them from or shut down the Win10 machine?

---

### Post by dokbrown2 on 2020-03-27
the drives are inthe original format they came in.
I have had no needto reformat them.


The FIIO player doesits own SD card formatting when you first pop in a sd card.  I assumethey aimed for compatibility with windows 10/macbook.

---

### Post by TheFu on 2020-03-27
> **dokbrown2 said:**
> the drives are inthe original format they came in.
I have had no needto reformat them.


The FIIO player doesits own SD card formatting when you first pop in a sd card.  I assumethey aimed for compatibility with windows 10/macbook.

Won't install any packages to provide the necessary drivers and won't answer the relevant questions asked.
Flash devices can have different file systems when they come from the vendor.  Not all of those are usually installed on any Linux system by default.  So, if you'd like for the flash drive to work as is, then the file system on it needs to be known.  Plus, not all flash drives are compatible with all USB ports (and USB controllers).  if that's the situation, trying a different port on the system, not near the port that isn't working would be the next step.

Not sure anyone can help.  Sorry.

---

### Post by dokbrown2 on 2020-04-15
Please tell me that there is ubuntu desktop OS that comes withdrivers to support mounting a sd card in an android phone: gnome,mate, cinnamon, xfce.  In regards to ease of use, that would bepriority for many users.  



I use Samsunggalaxy phones b/c their &#8220;Samsung switch&#8221; software supportsgalaxy/android/iphone/blackberry.



---Interoperability is key ---

---

### Post by TheFu on 2020-04-15
All the drivers needed to access almost any file systems are in the standard repos just like any other software.  exFAT should be included in 20.04 now that Microsoft has stopped being nasty with their patent licenses for it.  But really, devices using SD storage really should use a better, patent-free file system like Samsung's f2fs.

On exFAT: [https://arstechnica.com/information-technology/2020/03/the-exfat-filesystem-is-coming-to-linux-paragon-softwares-not-happy-about-it/](https://arstechnica.com/information-technology/2020/03/the-exfat-filesystem-is-coming-to-linux-paragon-softwares-not-happy-about-it/)

---

### Post by dokbrown2 on 2020-04-16
Interesting article.  Does that mean that the next version of Ubuntu with the new linux kernel 5.7 will solve my problem & that the desktop environment is not the issue ?  
I&#8217;ve been using Ubuntu for 5+ years & I am still confused as the lines between kernel/desktop/gui.
 
I meant to say I use LIBREoffice b/c it works on linux/mac/windows.
 
--- Interoperability is key ---

---

### Post by CelticWarrior on 2020-04-16
> **dokbrown2 said:**
> Interesting article.  Does that mean that the next version of Ubuntu with the new linux kernel 5.7 will solve my problem & that the desktop environment is not the issue ?  
I’ve been using Ubuntu for 5+ years & I am still confused as the lines between kernel/desktop/gui.
 
I meant to say I use LIBREoffice b/c it works on linux/mac/windows.
 
--- Interoperability is key ---

No, it won't.
Now that you have Windows 10 and if still using typical Windows file systems like NTFS (you still are) it's imperative to disable the Fast Startup feature in Windows.

---

### Post by TheFu on 2020-04-16
> **dokbrown2 said:**
> Interesting article.  Does that mean that the next version of Ubuntu with the new linux kernel 5.7 will solve my problem & that the desktop environment is not the issue ?  
I’ve been using Ubuntu for 5+ years & I am still confused as the lines between kernel/desktop/gui.
 
I meant to say I use LIBREoffice b/c it works on linux/mac/windows.
 
--- Interoperability is key ---
Whether there is a GUI program that can interface with any storage, or not, is separate from whether the storage can be accessed.  

The only problem I see is a refusal to load a driver that is, and has been, available for years.

[https://itsfoss.com/mount-exfat/](https://itsfoss.com/mount-exfat/) has directions.
 3 steps if you have a kernel 5.3 or lower. Check that with
```
$ uname -r
4.15.0-96-generic

```

Those 3 steps, two of which might be optional, so just do all three.
```
sudo add-apt-repository universe
sudo apt update
sudo apt install exfat-fuse exfat-utils
```

Anyway, after you load the exfat drivers, any file manager should make access possible, assuming the storage uses exFAT. It won't help if a different file system is used or there's a compatibility issue with the SDCard and USB port.

[https://www.dedoimedo.com/computers/gnome-gsconnect.html](https://www.dedoimedo.com/computers/gnome-gsconnect.html) talks about GSConnect and KDE-Connect. These are full-access tools for Android devices, assuming you don't care about security. GSConnect requires Gnome3 as the DE.  KDE-Connect prefers KDE as the DE.  There are other tools trying to accomplish similar connectivity. I've looked at a few, but they all fail my "smells bad" security review.

---

### Post by Holger_Gehrke on 2020-04-17
A rather safer way to copy or move data between an Android device and a Linux machine is to set up ssh with sftp on Linux and then use a file manager that can use that on Android. Reduces wear and tear on the SD-Card slot. I'm using Cx Explorer on Android for that, but I'm sure there are others.

Holger

---

### Post by TheFu on 2020-04-17
> **Holger_Gehrke said:**
> A rather safer way to copy or move data between an Android device and a Linux machine is to set up ssh with sftp on Linux and then use a file manager that can use that on Android. Reduces wear and tear on the SD-Card slot. I'm using Cx Explorer on Android for that, but I'm sure there are others.

Holger

I use ES-File Explorer for the sftp. I'm not convinced that most Android software hasn't been compromised due to all the advertising bloat embedded in every, freakin', app.  That's why I prefer the USB connection and drag-n-drop file xfers controlled by the Linux side.

I try to avoid using anything from google, so the F-Droid app store is usually where F/LOSS, non-advertising-bound, software for Android comes.
[https://search.f-droid.org/?q=sftp&lang=en](https://search.f-droid.org/?q=sftp&lang=en)   shows 2 sftp apps.
[LIST]
[*]Ghost Commander - SFTP plugin
[*]Spider
[/LIST]
I've used neither.

---

### Post by dokbrown2 on 2020-04-17
I actually tried kubuntu/netrunner 5+years ago for KDE-connect alone. It worked well but kubuntu had 2 many other problems relative to ubuntu gnome/mint.  Make use of has a great KDE/kubuntu guide & I keep telling myself to try netrunner again . . . . .
 
[https://www.makeuseof.com/tag/guide-to-kde-the-other-linux-desktop/](https://www.makeuseof.com/tag/guide-to-kde-the-other-linux-desktop/)
thank u FU for the simple terminal commands.  I’m a newbie but that seems simple enough.

---

### Post by TheFu on 2020-04-17
> **dokbrown2 said:**
> I actually tried kubuntu/netrunner 5+years ago for KDE-connect alone. It worked well but kubuntu had 2 many other problems relative to ubuntu gnome/mint.  Make use of has a great KDE/kubuntu guide & I keep telling myself to try netrunner again . . . . .
 
[https://www.makeuseof.com/tag/guide-to-kde-the-other-linux-desktop/](https://www.makeuseof.com/tag/guide-to-kde-the-other-linux-desktop/)
thank u FU for the simple terminal commands.  I&#8217;m a newbie but that seems simple enough.

The shell/terminal is more concise and exact, plus it saves having to draw lines on 10 screen shots trying to explain the same stuff due to a GUI. Don't fear the terminal. It is your friend.  

Plus, once you learn how to do things in the terminal, that's usually it for 20+ yrs.  The GUI changes every few years, but most terminal commands do not.  Keep notes in a directory that can be searched quickly for stuff you've already solved. The next time, instead of 5 minutes, it will be 15 seconds.  A great aid to productivity.  Something I do twice will get a script that automates it.  There are a few hundred of those at this point.  Each one saves time and most last decades.  Some scripts I wrote in 1993 are still working fine because they were written for Unix, not just Linux.  About 90% of Unix/Linux are the same, just the sysAdmin stuff is different.

But lots of people do fine only using the mouse with the point-n-click or so they claim. That's fine too.

DId you run those commands?  Is the storage mounting?  Is the music player working?

---

### Post by dokbrown2 on 2020-04-21
I haven&#8217;t had a chance yet b/c my windows desktop just crashed & burned.  My tech friend is trying to recover my files as we speak.  I suspect it was a virus.  Just another reminder of why Ubuntu is my primary desktop . . . . . . I&#8217;m trying to convert him b/c he knows more than me. 
 
I actually learned to use commands 5 years ago but Ubuntu/MINT is so overall smooth that I really haven&#8217;t had much need.  The book was full of commands & was based on Ubuntu 10 LTS.  It&#8217;s collecting dust in my garage somewhere.

---

### Post by dokbrown2 on 2020-05-05
Igot this answer from linux mint MATE & still no ability to see mysd card


exfat-fuse is already the newest version (1.2.8-1).

---

### Post by dokbrown2 on 2020-05-09
thiscode worked on my ubuntu install but not linux mint MATE.


Iforget how simple/efficient the terminal can be.

---

### Post by wildmanne39 on 2020-05-09
It would be helpful if you posted the code you used, will you please edit your post to include the code?

Thanks

---

### Post by dokbrown2 on 2020-05-22
can any KDE / kubuntu users comment on dolphins ability to access android phones with sd cards ?

[https://kubuntu.org/feature-tour/](https://kubuntu.org/feature-tour/)

"[CENTER][COLOR=#777777][FONT=Ubuntu]Dolphin makes connecting your USB flash drives, SD cards, and your phone super easy! "[/FONT][/COLOR][COLOR=#777777][FONT=OpenSansRegular]


[/FONT][/COLOR][/CENTER]

---

### Post by dokbrown2 on 2020-05-22
> **TheFu said:**
> Whether there is a GUI program that can interface with any storage, or not, is separate from whether the storage can be accessed.  

The only problem I see is a refusal to load a driver that is, and has been, available for years.

[https://itsfoss.com/mount-exfat/](https://itsfoss.com/mount-exfat/) has directions.
 3 steps if you have a kernel 5.3 or lower. Check that with
```
$ uname -r
4.15.0-96-generic

```

Those 3 steps, two of which might be optional, so just do all three.
```
sudo add-apt-repository universe
sudo apt update
sudo apt install exfat-fuse exfat-utils
```



i used this code

---

### Post by dokbrown2 on 2020-11-15
Fornew users who do not want to fiddle with the terminal or packages . .. . . . 




10/2020update


Itried MINT CINMAN 19.3 to no avail.


Idid a clean install of 18LTS 18.04.5 & it seems to have fixed alot of problems [but not all of them].

---

