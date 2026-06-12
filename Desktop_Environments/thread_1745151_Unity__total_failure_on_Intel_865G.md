---
title: "Unity  total failure on Intel 865G"
date: 2011-04-30
forum: Desktop Environments
---

### Post by leecrocker on 2011-04-30
My system (A Shuttle XPC with Intel 865G integrated graphics) has been running beautifully on Meerkat, Compiz and all.  Narwhal upgrade totally fails; I can just manage to log out by feeling my way around, select "Ubuntu Classic with no effects", and it's almost usable, but still has lots of screen problems.  Running from livecd totally fails as well.  Not sure the best place to report this or how to investigate further.  Just had to re-install Meerkat and move on.

---

### Post by aaronwa on 2011-05-01
I am on a Dell desktop with the integrated Intel 82865g video chipset and I'm having the same issue.  Must log in as 'Ubuntu Classic with no effects' to see any of the taskbars.  
```
aaronw@aaronDesktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

```

any ideas to try?

Aaron Wagner

---

### Post by ds_shellback on 2011-05-02
I tried the live CD before attempting to upgrade from 10.10 - it did get to the gnome desktop, but the menus appear blacked out and if I click on an area of the desktop a large area of the screen from the top left corner to the cursor click point disappears and takes a long time to come back!

```
VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```

I know this is 'old' hardware but it's ok with 10.10 - guess I won't be upgrading.

---

### Post by danielgm on 2011-05-02
Same problem here. My machine is a Compaq with integrated 82865G graphics card.
Unity tries to start and fails (frozen screen).
Gnome (sorry, Ubuntu Classic) starts with garbled screen, then freezes.
Ubuntu classic without effects starts with some screen corruption, freezes ocasionally (sometimes it just runs very slow, CPU is not loaded but the screen only updated once every 3-4 seconds. I can log in simultaneously via a virtual terminal and everything works just fine).

Lucid worked wonderfully with the same hardware (Compiz and all).

---

### Post by HappySmack on 2011-05-02
Same issue with video for Dell Optiplex GX2700 with Intel 82865G onboard. Has anyone tried just removing Unity? (I'm feeling kinda scared)

---

### Post by amiliv on 2011-05-03
Another "mee too".  In my case on old(er) Dell Dimension 3000 system with Intel 82865G integrated graphics controller (according to lspci).  Windows, toolbar, menus, etc mostly do not render properly.

There was an warning dialog the first time I logged in saying something along the lines that Unity might not be supported on my hardware, and suggesting using "ubuntu classic".

BTW, what is the minimum requirement for running Unity?  I've an PCI slot free, so if any of the (older and cheap) ATI or nVidia cards works (such as ATI Rage 128/Pro/XL, etc), I might consider getting one from Amazon.  This system just before PCI-E become widespread, and unfortunately it was made by Dell (meaning no AGP either).

---

### Post by amiliv on 2011-05-03
Forgot to mention.  While "ubuntu classic" proved unusable, "ubuntu classic (no effects)" worked for me just fine.  Now, on to figuring out some if there's such thing as ultra-cheap PCI graphics card that's supported by Unity...

---

### Post by vanquishedangel on 2011-05-03
I know that you all might want unity but on older machines I would recommend a lighter desktop, Unity is beautiful but requires a lot of system resources to run, That beauty comes at a price of resources.

I work on a Compaq presario 1500 with an ATI mobility radeon 7500 with 64 mb video ram, so that is a no go for unity for sure, however the LXDE desktop (lubuntu) is really fast on it and it is also beautiful and has all the functionality that you would find in a normal Ubuntu, It is in the repo's for those of you who have Ubuntu installed just open synaptic and search lubuntu-desktop or just lubuntu, extra's are also in the list when you look for lubuntu with synaptic to. A few things are different but it has about 1/5 the resource weight of the normal ubuntu and that was with gnome2 or "classic".

Here is the link for lubuntu 11.04 (natty)

[http://people.ubuntu.com/~gilir/lubuntu-11.04.iso](http://people.ubuntu.com/~gilir/lubuntu-11.04.iso)

and here is a link to other info and other downloads from distro watch ( including a LTS version)

[http://distrowatch.com/table.php?distribution=lubuntu](http://distrowatch.com/table.php?distribution=lubuntu)

good luck and i hope all works out for ya :)

---

### Post by danielgm on 2011-05-03
An update that fixes Gnome without Compiz (Ubuntu Classic) is on the queue. The update effects xorg-video-intel, and fixes screen corruption artifacts.

Compiz is still broken, though, and Unity will not start with the 865G (Unity requires OpenGL 1.4, the 865G is compatible with up to 1.3).

---

### Post by danielgm on 2011-05-03
Sorry, the update will fix Ubuntu Classic without effectcs, and only for the intel 865G and previous cards.

---

### Post by amiliv on 2011-05-04
Either the update was already rolled out yesterday, or classic without effects works on my system (which uses 865G).

Anyhow, with classic working, and considering how old is the system I'm using, I'm happy camper even without unity :-)

---

### Post by Ni-el on 2011-05-04
Similar situation with integrated graphics Intel 4 Series. Oddly enough, the same thing happened when installing Kubuntu 10.10. 
No answer yet, but it will likely be something that an xorg.conf could compensate for?

---

### Post by maxmaster1990 on 2011-05-05
Just installed, got the same problem, i'm appliying the updates to see if there's any solution on the problem, the "ubuntu classic" has a lot of glitches and black spaces and crazy stuff on the screen, the "just classic" is UNUSABLE.
Crossing my fingers for the fix to work, i saw the xorg-intel update in the list.

---

### Post by maxmaster1990 on 2011-05-05
Problem solved after update, going to try unity2d

---

### Post by bustamelon on 2011-05-06
Anyone getting 3d effects/compiz w Intel chip yet?
None here.  Classic/No effects only.
I tried screwing around, with no luck, with other PPAs, so I'm not sure if my sources.lst is back to the way it was.

---

### Post by jmore9 on 2011-05-06
I have a couple of laptops with that same chipset.  They will be using another linux distro on upgrades.  If i am not mistaken i think we need to have the intel 900 series or better to use Ubuntu 11.04 or better.  Not going to spend the money to buy new laptops will use what ever distro will work with them, no Ubuntu ,then no Ubuntu .

---

### Post by Blasphemist on 2011-05-06
FYI, [https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

and from that, 
> /usr/lib/nux/unity_support_test -p

---

### Post by OldBoy44 on 2011-05-09
Hi all,

I too have Intel 865G - Other posts in this thread seem to indicate problems with Ubuntu Classic. I gather there may be a fix on the way.

1. Is this correct?

2. What is Unity 2D?  Classic (With no effects)?

3. If so, can I expect Unity 2D will be around for version L.T.S. 12.04?

A not very happy little camper.

Cheers.

---

### Post by Blasphemist on 2011-05-09
> **aussiebean said:**
> Hi all,

I too have Intel 865G - Other posts in this thread seem to indicate problems with Ubuntu Classic. I gather there may be a fix on the way.

1. Is this correct?

2. What is Unity 2D?  Classic (With no effects)?

3. If so, can I expect Unity 2D will be around for version L.T.S. 12.04?

A not very happy little camper.

Cheers.

The 856G won't support Unity 3D if it precedes the 950. Unity 2D should work, as should classic. Those two are not the same session type. Unity 2D is just what it sounds like, unity without 3D effects. Many people are very happy with it. 

I'm sure Ubuntu will continue to offer desktop environment options that don't require 3D support. LXDE and Lubuntu 11.04 is a good option but Ubuntu with a session type that doesn't require 3D should work very well for you.

---

### Post by OldBoy44 on 2011-05-09
Thanks for your quick and kind response Jim!

:popcorn:

---

### Post by CyborgAlpha on 2011-05-10
> **Ni-el said:**
> Similar situation with integrated graphics Intel 4 Series. Oddly enough, the same thing happened when installing Kubuntu 10.10. 
No answer yet, but it will likely be something that an xorg.conf could compensate for?

I had no issue with 10.10, but as practice I now wait 2 months after the release date to update.

---

### Post by oliveryty on 2011-05-10
[SIZE=3]Have you guys tried unity-2d?

sudo apt-get install unity-2d[/SIZE]

---

### Post by CyborgAlpha on 2011-05-10
> **jmore9 said:**
> I have a couple of laptops with that same chipset.  They will be using another linux distro on upgrades.  If i am not mistaken i think we need to have the intel 900 series or better to use Ubuntu 11.04 or better.  Not going to spend the money to buy new laptops will use what ever distro will work with them, no Ubuntu ,then no Ubuntu .

I like kubuntu 10.10 , but if kubuntu 11.04 isn't fixed for Intel 865G - I'll be leaving too (and so will a lot of people from what I've seen).:(

The beauty of linux/unix is it's ability to bring older machines back to life. Kubuntu 10.10 runs fine on an Intel 865G machine with only 512MB of RAM.

---

### Post by amiliv on 2011-05-10
Well, looks like good old 865G is a bit too old these day for many other things, not just Unity.

I've an old Dell 3000 desktop: 2.4GHz Celeron, 865G chipset, only PCI slots, no AGP (insert an angry look at Dell here).  It worked great for many day to day things, but anything needing any kind of remotely fancy graphics was unusable.

So, hit the bullet, and ordered an PCI version of GeForce 9500GT last week.  Arrived today, plugged it in, installed nvidia driver (simply using "additional drivers" from system settings).  Unity fully works, as well as all that other eye candy like GL based screen savers that was unusable before.  All feels fast as well.  Normally, I don't play games, but just to test the things a bit more, I installed few, and they all worked fine and smooth (at least on default settings), even on this old system.  Boxee application now works nicely as well (was a bit slow on 865G), and even streaming videos is now an option on this old box again.

I guess anything that needs to transfer large amount of data to the card still isn't going to work (due to slow PCI), but many things for which 865G was simply too slow will work.

Summary, if you want Unity, or to simply prolong the lifetime of your old system for a few more years, an graphics card upgrade might be good way to go.  If you are lucky to have AGP or PCI-e slot in your system, go for that.  If you only have PCI slots (like in my Dell), even PCI based card will make a big difference (as long as your applications don't hit the limits of the old and slow PCI bus).

---

### Post by HappySmack on 2011-05-12
Dell Optiplex GX270
 Intel Corporation 82865G Integrated Graphics Controller (rev 02)

 I had to uninstall Unity just to get Classic/no effects to work. I am really irked by the inability to enable effects (Compiz). Brought to my attention in this thread, [http://ubuntuforums.org/showthread.php?t=1746497](http://ubuntuforums.org/showthread.php?t=1746497)
was the issue of the i915 driver being used in 11.04 as opposed to the i810 driver that was used in 10.10.

 My question would be, has anyone tried reverting to the i810 driver? If so, can Compiz be enabled? Unity? 2D or 3D (doubtful)

---

### Post by danielgm on 2011-05-16
Unity 2D should work (it does in my machine, similar specs). It even shows composition (transparent windows, windows shadows), but I'm not sure if it's because I had them already enabled in Metacity (in gconf-editor set /apps/metacity/general/compositing_manager to "true").

---

### Post by elinap on 2011-05-17
Unity-2d works on Intel 865G (on old IBM Think Centre) after doing
sudo apt-get install unity-2d.

Before installing unity-2d, the screen "went crazy", and windows did not draw properly.

Why doesnt it work on this system? It is not that old...

Old applications after upgrade are "hidden" in applications tab, together with all the rest that were installed...

---

### Post by OldBoy44 on 2011-05-26
Hi all,

I note that my Intel MOB D865GLC has an AGP 8X/4X graphics interface with the flexibility to upgrade via a high end AGP graphics card supporting universal 1.5V 3.0 up to AGP 8X. 

Will such an upgrade fix the problems outlined in the previous posts?

If so, can anyone one suggest a suitable card as I am a complete newbie in this area?

If so, where is the best place to obtain one? 

I do not need for gaming.

Cheers,  :)

---

### Post by jasonofx on 2011-05-26
Just chiming in with another "Me too". I have a little Gateway box I got for $50. It has a 2.8 Ghz processor with 2 gb ram. Was hoping to dual-boot Unity and XP on  this, it's a work computer. Guess not. Re-installing 10.04 LTS, guess I'll wait to see if this gets fixed to try it again. May not get fixed being an older chipset and all.

---

### Post by galacticaboy on 2011-05-26
I got the same Graphics and I could not do Unity, I had to install Unity 2D and that worked great!

---

### Post by amiliv on 2011-05-26
> **aussiebean said:**
> Hi all,

I note that my Intel MOB D865GLC has an AGP 8X/4X graphics interface with the flexibility to upgrade via a high end AGP graphics card supporting universal 1.5V 3.0 up to AGP 8X. 

Will such an upgrade fix the problems outlined in the previous posts?

If so, can anyone one suggest a suitable card as I am a complete newbie in this area?

If so, where is the best place to obtain one? 

I do not need for gaming.

Cheers,  :)

I think any current (not previous generation) GPU made by nVidia should work just fine: [http://www.nvidia.com/object/geforce_family.html](http://www.nvidia.com/object/geforce_family.html)

Note that after installing the card, you have to manually enable nvidia driver (trivial, go to additional drivers in settings, enable proprietary nvidia driver, it will download it from the net and install it, reboot, and that's it).

It's likely older and cheaper (previous generation) nVidia cards should work just fine as well (while Unity requires only OpenGL 1.5 with few extensions on top of it, I'd likely pick something still recent enough to support at least OpenGL 2.0).

I decided to go with nVidia card, after seeing some negative articles on the web about stability of Linux drivers for ATI (AMD) cards.

I put an PCI GeForce 9500 GT card in my old Dell PC (with 2.4GHz Intel Celeron).  Card supports up to OpenGL 2.1, and both Unity and few 3D games and flight sims I tried worked fine (after enabling nvidia driver through "additional drivers" setting).  Flight Gear was a bit on the slow side though, and I X-Plane had to be tuned down just slightly from defaults (both probably not related to GPU, more likely due to either an slow(er) CPU or slow PCI bus).  I ended up with 9500 GT only because 9500 GT and 8400 GS are the only two current nVidia chips available on PCI cards these days.

My new PC (2nd gen. Intel Core i7 3.4GHz) came with PCI-e GeForce GT 440 card in it (supports up to OpenGL 4.0).  While there are much faster and bigger (and way more expensive) video cards around, GT 440 worked out good for me so far.

If it's an old PC you have, probably not worth spending too much money on video card anyhow (hack, high-end video cards these days cost almost as much as my new PC -- you end up better of just buying faster PC with not so bleeding edge card).  I think all curent nVidia chips support at least OpenGL 2.0.   If you can find nVidia based card that supports OpenGL 3.0 or 4.0 for not too much more then an OpenGL 2.0 card would cost, I'd go with that.

---

### Post by amiliv on 2011-05-26
BTW, there's probably not much point in buying new video card just to run Unity.  The old UI is just as good, IMO.  Simply select classic (without effects) when logging in, and you'll be good.  If there's some other stuff needing 3D acceleration you use, then it may make sense to try out upgrading video card.

---

### Post by OldBoy44 on 2011-05-26
Thanks for your input amiliv, it is very much appreciated. I may opt for the classic mode (no effects) as my computing needs are really rather simple.

Cheers, :)

---

### Post by joe96 on 2011-06-25
Hi, I am very new to Ubuntu and just installed 11.04 to my Dell Optiplex SX270  to use as a low-spec PC attached to my TV for watching videos, etc.  It has onboard Intel 82865G graphics.

The TV res is 1360x768 and all I could get to display which was even vaguely useable was 640x480. The problems I had included the picture being cut off at the top and bottom, windows disappearing (so having to guess where to click), and just black 'dead spaces' where nothing was displayed. I was tearing my hair out trying to get it to display properly, looking for drivers, messing around with GRUB options, not really knowing what I was doing. Then I tried something someone suggested here - changing to 'no effects' on the login screen and everything's fine so far. Can't believe how easy it was to fix!

---

### Post by John Morris on 2011-07-31
I'm writing this note just to confirm for anyone searching, the situation.  If you have for example IBM off-lease ThinkCenters (for example an M50), which were delivered in 2005, this family of machines has the Intel 865G video chipset.  And upgrade to 11.04, a.k.a. Natty Narwal, produces an unusable desktop.  Symptoms include disappear pull-down menus and windows that won't display, and various blinking artifacts.  It is a little tricky to make a menu selection if you get stuck.  And if you are not presenting a login screen, you will have difficulty selecting the display system that works.  If you do get stuck, what you want to be able to do is to "logout", or login where you are presented, in a ribbon at the bottom of your screen during login, the choice for display system.
 
Gnome Classic DOES NOT WORK.  It has to be, as per the great folks who have contributed to this thread earlier, Gnome Classic WITHOUT EFFECTS.  Then (so far) it seems you'll be fine.
 
I think given that there are likely (and seem to be) quite a few folks in this position, a "test my system for compatibility" button or dialogue during upgrade or install, would be helpful -- there is the "graphics not compatible with Unity" message at one point -- but one is not informed as to the implications, or given the opportunity to downgrade the display system -- or even a default to Gnome Classic Without Effects.  So it seems the system knows there is a problem but nothing is done about it.
 
John

---

### Post by feed5000 on 2011-08-11
Logging in with Ubuntu Classic (no effects) did not fully take care of the problem for me. Many of the same problems described in this thread persist.

---

### Post by feed5000 on 2011-08-11
I have a lab of 24 computers, and I put 11.04 on them all. But the 5 with the 865G were experiencing the problems described in this thread. This process worked with all 5:

1. From login screen open the command line with Ctrl+Alt+F1.

2. Login with admin account.

3. Run command "sudo apt-get update".

4. When finished updating, run command "sudo shutdown now".

5. Boot computer to login screen.

6. Click username, select "Ubuntu Classic (No Effects)" at bottom of screen, and enter password.

7. At this point I had a working desktop environment (where I could actually do thing), but still had the weird artifacts in various places.

8. System > Administration > Update Manager. Install updates.

9. Restart computer. Now artifacts were gone.

---

### Post by Dragonbite on 2011-08-11
Sounds like the issues that cropped up with i855 in 10.04 have reached the 865s.  It sucks, no doubt about it, and even after 15 months the i855 issue isn't looking like it is going to be fixed so I wouldn't hold your breath for the 865.

The 855 issue was also not just Ubuntu, but all of the Linux distros (related to the kernel).  Fedora provided the best patch out of Ubuntu, openSUSE and Fedora. Unfortunately with their latest release (15), while it does work it doesn't handle desktop effects anymore.

---

### Post by FormatSeize on 2011-08-11
> **HappySmack said:**
> Dell Optiplex GX270
Intel Corporation 82865G Integrated Graphics Controller (rev 02)
One of my computers is the exact same thing. 
 
I have never gotten Ubuntu 11.04, Kubuntu 11.04, or Fedora 15 to work on any of my Dell machines that used Intel integrated graphics. This is one of my newer 'old' machines from Dell. The first time I actually got Unity or any other graphic intensive distribution to work correctly is when I went and got a really cheap eMachine computer, which had nVidia integrated graphics. I bought that computer to give me an idea of what I would need to get the newer generation of GNU/Linux distributions to work (I returned it to the store). 
 
Right now, I have a Gateway GM5442. I'm not sure what the graphics controller is, but it will do Ubuntu 11.04 and anything else without a graphics card. While this is still considered 'old' it works where the Dell machines don't. But, of course, this is from my own personal experience.

---

### Post by dgrover on 2011-12-06
Dell GX270, 2.4 GHz P4, 512 MB RAM, with Intel 82865G graphics controller.  Installed Ubuntu 11.04.  The default login (Unity?) is unusable--windows flicker and go away, etc., as reported in prior posts on this thread.  Logging in with Gnome No Effects is useable, but there were video artifacts at the top and bottom of the screen.  Ran system update, and once rebooted, the video looks fine.  (1600x900 screen)  Seems to be resolved for this particular system/configuration.

---

### Post by bustamelon on 2011-12-06
> **dgrover said:**
> Dell GX270, 2.4 GHz P4, 512 MB RAM, with Intel 82865G graphics controller.  Installed Ubuntu 11.04.  The default login (Unity?) is unusable--windows flicker and go away, etc., as reported in prior posts on this thread.  Logging in with Gnome No Effects is useable, but there were video artifacts at the top and bottom of the screen.  Ran system update, and once rebooted, the video looks fine.  (1600x900 screen)  Seems to be resolved for this particular system/configuration.

Really?
Both Gnome and Unity 100% now? 
Great news.  Thanks.

---

### Post by kio_http on 2011-12-06
> **bustamelon said:**
> Really?
Both Gnome and Unity 100% now? 
Great news.  Thanks.

When was this update? I'm on an Intel GMA 950 that is significantly better but Unity feet slow to me. While I'm a KDE user I wanted to give unity a shot

---

