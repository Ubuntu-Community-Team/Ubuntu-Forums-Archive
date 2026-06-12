---
title: "left and top menus and desktop not displaying"
date: 2010-11-18
forum: Desktop Environments
---

### Post by AndyGaskell on 2010-11-18
Hi Everyone

I've been using Ubuntu for several years, and wanted to try the netbook remix on my old Acer Aspire 5050 laptop.  

I tried to install and switch from desktop 10.10 to netbook 10.10, and the home page and menus didn't display properly.  I took this as being due to some conflict with an exiting bit of software (I use it as a LAMP server and dev machine, so it had a lot of stuff one it).  Keen to try the netbook edition, and clean down my laptop, I installed in from scratch, formatting the HDD etc.

Anyway, the issue is still the same.

It is quite hard to describe what is displayed.  The left menu is just empty, with no icons.  The top bar is also empty.  When you mouse over the left menu, blank pop-outs appear.  Also, some icons are blank or mangled.  Occasionally, when I close a dialogue, or do an alt-tab, the left menu icons appear, but only for a split second.

Anyway, screen dumps (reduced to half size) will explain this better, so here are a couple...

Top and left menus showing as empty semi transparent bars.
[IMG]http://ssofb.co.uk/uploads/photos/Screenshot-1-small.png[/IMG]

Same with an app running
[IMG]http://ssofb.co.uk/uploads/photos/Screenshot-2-small.png[/IMG]


with mouse over a left menu item, and a blank pop-out with black surround.
[IMG]http://ssofb.co.uk/uploads/photos/Screenshot-3-small.png[/IMG]




Some hardware info...
AMD Turion 64 Mobile Technology MK-36 (2.0 GHz, 512 KB L2 cache)
ATI Radeon® Xpress 1100
14.1" WXGA Acer CrystalBrite™ TFT LCD, 1280 x 800 pixels

Any ideas?  Is this an ok place to post this query?
Cheers

---

### Post by AndyGaskell on 2010-11-18
I guess this may be a Unity and AMD/ATI graphics issue, after reading some of the Unity mega thread at [http://ubuntuforums.org/showthread.php?t=1610637](http://ubuntuforums.org/showthread.php?t=1610637)

---

### Post by BoomShiqua on 2010-12-01
I've got the exact same issue that you're having. My laptop is a Compaq Presario V2312US using an ATI Radeon Xpress 200M.

I noticed that if I log in to the desktop edition rather than the netbook edition the menus display properly.

---

### Post by AndyGaskell on 2010-12-02
Hi BoomShiqua

I noticed if I tried the Ubuntu Netbook Edition 2D, it all worked fine on my Acer Aspire 5050.  The downside is that the 2D version is not such a cool interface in some ways, though still pretty cool.

I guess the netbook edition, being intended for netbooks, is aimed at Intel Atom hardware, which has no AMD/ATI goodness in it. Perhaps the 2D version was aimed at more general hardware, that 3D stuff is always trickier, hardware-wise.

I went back to the normal Ubuntu desktop, it is pretty nice anyway.  Were you thinking of using the netbook remix to speed up your Presario? I guess xubuntu might be a better bet for that.

hope that's helpful.


[]("http://ubuntuforums.org/member.php?u=239236")

---

### Post by BoomShiqua on 2010-12-02
I'll have to try out Ubuntu Netbook Edition 2D and see how that works sometime. I think you're probably right about the reason why the 3D stuff doesn't work being due to the graphics cards in our laptops when the system is expecting to find Intel Atom hardware.

I would really like to get the netbook edition working on my laptop just because of the speed improvements. My laptop is about 5 years old now and has a single core processor so I'd like something lightweight. I have thought about using Xubuntu in the past but I never have really gotten around to trying it out. Maybe I'll give that a try and see how it runs on my system.

I'll keep working on getting everything working and I'll let you know if I make any progress. Good luck getting your system working as you'd like for it to!

---

### Post by Konzales on 2010-12-20
Hi,

On my ThinkPad Edge with AMD/ATI (Athlon II Neo K325/Radeon HD4225) I've similar problems:
 - Icons show up very late if they do, 
 - All windows show up upside down if I hoover over them
 - Info boxes are distorted

I wanted to use Netbook version because of the small 11" screen.
But it looks like I have to change to standard version...

---

### Post by MargaretA on 2011-01-02
Wow, finally - I asked this very same question a couple of days ago in the beginners section here and got no real answers. So today I put it on Yahoo Answers, and within an hour had two good ideas - both that it was an issue with the netbook version of Ubuntu and the ATI card - which is what my laptop has. So I did a search for "ubuntu netbook problems with ati radeon display" and found this thread.

For the record, my computer is a Dell Latitude D631 with an ATI Radeon X1200 series card. My desktop looks, and behaves, exactly the same as described in the original post here.

The Yahoo answers had to do with the fact that Ubuntu netbook uses Unity, and suggested that I switch to the regular version, which uses Gnome. As a rank beginner I really don't know the difference between the two, and actually couldn't even tell you what each of these does. But it gives me a place to start - basically, find another version of Ubuntu to install.

I don't know if this will help anyone else here; I hope it does. I did want to reply here so that if anyone has the same problems installing Ubuntu netbook on a Dell Latitude they'll find this on a search.

Now I'm off to do more downloading...

Meg

---

### Post by dryphi on 2011-01-09
I have this exact same problem on my Lenovo T60 with Ubuntu 10.10 Netbook fresh install.
So it sounds like I have to reinstall from scratch, using the non-netbook edition?  Yes?  Or did anyone figure out a fix?

---

### Post by Krytarik on 2011-01-09
The thing with the Netbook Edition is: It depends on hardware-accelerated video support! If you don't have the correct driver installed, you can't barely see anything. The same is true for the effects in the Desktop Edition. The driver support is the same for both editions, you just have to find the driver which fits your video card/chip the best.

Starting with the build-in so-called driver jockey is generally a good idea:
since I don't know where it is in Unity (Netbook Edition), if at all, log into the Desktop Edition and go to "System -> Administration -> Additional Drivers". With that tool you can search for compatible drivers and install/activate them.

If you have an older ATI card/chip, which isn't supported by the proprietary drivers anymore, the Open Source Edge Drivers are currently the best solution:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)
(look below that section to get to a list of now unsupported video cards/chips)

Good luck!

---

### Post by dryphi on 2011-01-09
Thanks! Your response was somewhat helpful.

> **Krytarik said:**
> 
If you have an older ATI card/chip, which isn't supported by the proprietary drivers anymore, the Open Source Edge Drivers are currently the best solution:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)
(look below that section to get to a list of now unsupported video cards/chips)

I went here and determined that my video card - ATI Mobility Radeon X1400 - is among those no longer supported.

> **Krytarik said:**
> 
log into the Desktop Edition and go to "System -> Administration -> Additional Drivers". With that tool you can search for compatible drivers and install/activate them.

How do I do this? I have the Netbook edition on a USB drive and installed. When I bootup Ubuntu I can see nothing.

---

### Post by dryphi on 2011-01-09
So I booted up in recovery mode with the failsafe graphics option. That worked. Then I updated everything and am now, apparently, running 11.04.
We'll that seemed to fix it as I can now see the menu on top and actually do stuff. Lol

Anyway I still don't see any menu (the netbook menu) on the left.
Also I didn't install any ATI drivers. I don't have "hardware" under administration.

---

### Post by Krytarik on 2011-01-09
Hi dryphi,

in the boot menu choose "recovery mode", then "root shell prompt", then enter those commands:
```
add-apt-repository ppa:xorg-edgers/ppa
apt-get update
apt-get upgrade
reboot
```

---

### Post by dryphi on 2011-01-09
Thanks. I added the repository and updated, rebooted.

Still no launcher or global menu bar. Also nothing under Additional Drivers.
Am I supposed to see this stuff?

Basically I can see everything, as before, but it doesn't look like the netbook edition. It looks just like regular Ubuntu.

---

### Post by Krytarik on 2011-01-09
Oh, I overlooked your second post, due to the display style of the threads, sorry.

So, you're now officially a Natty Narwal beta tester. *grin*

If you have the "normal" (Gnome) menus, you are definetely running the "Desktop Edition".
Logout and look if there is the option to login to the "Netbook Edition", should be.

---

### Post by dryphi on 2011-01-09
Ah yes. There's Unity.
I did not notice the little login selection menu at the bottom until now.
Thanks

---

### Post by Krytarik on 2011-01-09
> **dryphi said:**
> Ah yes. There's Unity.
I did not notice the little login selection menu at the bottom until now.
Thanks
Oh, at least now they name it like it is.
Great.

---

### Post by dryphi on 2011-02-16
So I reinstalled Ubuntu but kept it at 10.10 (no pre-releases).
Also I installed primarily the Desktop Ed and added-on the Netbook Ed packages.

Anyway, I still have the problem where I cannot see the Unity menus.

Also I followed this guide
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)
and added the Ubuntu-X PPA
I'm hesitant to go to the Xorg-edgers PPA because if I recall from last time when I added this repository I lost all video hardware acceleration (all Visual Effects options grayed out in Appearance menu)

Is it possible to run a different video driver through the Desktop edition than through the Netbook edition?
I wouldn't mind if I had no hardware accel in Unity as long as the menus showed up but I'd prefer to keep my current driver in Gnome as everything is working well with the Netbook ed.

Everything is fully updated through Update Manager with a fresh reboot.
Thanks

---

### Post by Krytarik on 2011-02-16
No, you can't run different video drivers in different desktop environment, since it is all the same xserver.

I doubt that installing Ubuntu-X-Swat's PPA will make you happy, since your card isn't supported by the proprietary drivers, like described in the guide you visited.

I have the OSED running just fine at my mom's machine, she has a ATI Radeon 9600XT.

And as yourself experienced, you wont see really much in the Netbook Edition if you cannot enable hardware-acceleration.

---

### Post by dryphi on 2011-02-17
Yeah I have the ATI Radeon X1400.

Edit: Yeah I'm fine with using the open-source drivers, in fact I would prefer that. Works great in the Desktop edition.
It's only in the Netbook edition that I am unable to see any menus.

Do you have Netbook or Desktop on your mom's machine?

Thanks.

---

### Post by dryphi on 2011-02-17
So I added the edgers PPA and Unity is now visible in the Netbook edition and I still have hardware accel (visual effects) in the Desktop ed. All good...

I guess there's no visual effects options with Mutter

---

### Post by Krytarik on 2011-02-17
No, we only have the Desktop Edition installed at her machine. But as I said that makes no difference regarding hw-accel.

I installed Mutter most recently at my machine, just to check how it works, because it was recommended over Compiz in another thread ([http://ubuntuforums.org/showthread.php?t=1684667](http://ubuntuforums.org/showthread.php?t=1684667)). And it's not really great, worse than Compiz, at least at it's current state. And, like you said, I also didn't recognize any desktop effects, and no ability to change its settings whatsoever.

Why don't you switch to Compiz instead in your Netbook Edition?

To change the default window manager, which is run automatically at login, use gconf-editor:
- press Alt+F2
- enter gconf-editor
- browse down the path "/desktop/gnome/applications/window_manager"
- set "/usr/bin/compiz" in both "current" and "default"

---

### Post by dryphi on 2011-02-17
I didn't even know that was an option. I'll check it out. Thanks.

---

### Post by dryphi on 2011-02-17
Compiz is already set as the default in my Desktop Ed.

I guess I don't understand the push for Unity / Mutter in the Netbook ed (and going forward?) if Gnome / Compiz works fine and offers additional functionality. lol

Fyi - installing Compiz Advanced Effects is an option in Ubuntu Tweak. I would imagine it would have no effect in the Netbook ed, however, since all the conf editor options are schema based.

---

### Post by Krytarik on 2011-02-17
> **dryphi said:**
> Fyi - installing Compiz Advanced Effects is an option in Ubuntu Tweak. I would imagine it would have no effect in the Netbook ed, however, since all the conf editor options are schema based.
Eh, I don't get this one!? :-?

---

### Post by dryphi on 2011-02-17
Compiz is the default for Maverick. Ubuntu Tweak = awesome and allows you to install some additional visual effects for Compiz. (I'm sure there are other ways to get the advanced visual effects but Ubuntu Tweak provides a nice clean interface and has a lot of useful options in one neat package).

Sorry, I just meant that I don't see the option to set Compiz in the Netbook edition. You can open gconf-editor (from a Terminal since hotkeys don't work) but from there things are a little different.
A lot of the options are schema based, I guess meaning you set a theme and everything follows that. Which is nice.

Basically, I imagine there is a way to use Compiz in Unity but changing settings is not the same as in Gnome.

---

### Post by Krytarik on 2011-02-18
Ok, I understand, you don't use the same options like in Gnome. I didn't thought of that, sorry. And that may also be one reason why Compiz may not run currently in UNE 10.10.

But upon googling for both keywords I found some articles about the Compiz developers working on the adaption to Unity, and there are also some indications that Canonical may have chosen Compiz as the default window manager for UNE 11.04 Natty Narwal.

[http://www.webupd8.org/2010/11/first-compiz-based-unity-screenshots.html](http://www.webupd8.org/2010/11/first-compiz-based-unity-screenshots.html)

---

