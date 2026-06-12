---
title: "[SOLVED] dual disply - visual effects not possible?"
date: 2008-04-17
forum: Desktop Effects &amp; Customization
---

### Post by abh83 on 2008-04-17
Dual display - visual effects not possible? :confused:

Last night I decided to hook up my LG Flatron L203WT monitor to my acer aspire 5633 notebook/laptop.

Set up was easy and flawless and I managed to run both displays at their original resolution:

notebook: 1280x800
Monitor: 1680x1050 

Until last night I was always using advanced desktop affect, so things like shadows, animations, desktop cube, widget layer screenlets and emerald themes.

However, after enabling dual display the visual effects switched off. Now when I try to enable visual effects in System > Preferences > Appearance > Visual Effects tab I get the following message: "Desktop effects could not be enabled".

Any idea as to why this is happening?

thx in advance!

---

### Post by estanton on 2008-04-17
I have the same problem with my dual displays. I just live with it, preferring the extra monitor space over the desktop effects.  I suspect that the dual monitor support in Ubuntu isn't advanced enough. Or it could be that your video card can't cope? Hardy is supposed to have advanced dual monitor support so maybe that will fix the problem?
Does anyone know for sure?

---

### Post by lintoolman on 2008-04-17
I use dual monitors and I'm running Hardy.  I only get the advanced effects after enabling the restricted ATI drivers.  You may need the same for your video card.

---

### Post by loudnlownoma on 2008-04-17
Not really sure why it would do this exactly - but I can say I have GGutsy on both my Desktop and laptop and haven't noticed this problem.  The desktop has an Nvidia card - restricted driver enabled - and Compiz works fine with the Twinview option, allowing the extended desktop across both monitors.  All the effects work exactly the same, just like they did on the one monitor.

The laptop - ATI card, also with the restricted driver enabled - has Gutsy as well, connecting one of the monitors in a clone view works just the same.  Didn't have to mess with settings at all, it just picked everything up and cloned it on the second monitor.  No trouble with the desktop effects there either, didn't have to change any settings.

Sorry - still fairly new to some of this stuff, so I can't offer much advice on why it may not be or what's causing the trouble, but I can say that it will work, at least in some cases.  What kind of video card are you using?

---

### Post by abh83 on 2008-04-17
I have restricted drivers enabled since I first installed GGutsy and they still are enabled.

I also have the latest drivers installed for my graphics card.

My card: Nvidia GeForce Go 7300 TurboCache 256 MB.

(see my signature for more system info.)

could it be memory related?

---

### Post by loudnlownoma on 2008-04-17
> **abh83 said:**
> I have restricted drivers enabled since I first installed GGutsy and they still are enabled.

I also have the latest drivers installed for my graphics card.

My card: Nvidia GeForce Go 7300 TurboCache 256 MB.

(see my signature for more system info.)

could it be memory related?

Sorry - noticed that after I posted...  Do you have the nvidia-settings program installed?  If you do, which configuration is selected for the outputs under the X Server Display Configuration?  Should be TwinView or Separate X session or something similar.

---

### Post by abh83 on 2008-04-17
no problem mate!

yes i have nvidia-settings installed. i use separate X screen.

I don't want to use twin view or anything else really because i have 2 different resolutions. Laptop being 1280x800 and ext. monitor being 1680x1050.

I also don't wish to have my desktop spread out onto 2 screens. I'd rather have 2 separate desktops.

btw. in nvidia-settings i have Xinerama enabled (if it helps)?

---

### Post by loudnlownoma on 2008-04-17
Gotcha.  I am using TwinView with separate resolutions, but that shouldn't matter.  When I first set it up I had them as separate X sessions, and things still seemed to work normally for the effects.  Although I do remember having trouble with the menu bars on the second monitor tho.  I'd say your best help would probably be in the compiz forums, there seemed to be a lot of threads dealing with dual monitors and various issues.  I think I have just been getting lucky with most of my stuff working fairly easily...  :)

Have you tried re-installing or disabling/restarting/enabling the restricted driver?  May be something messed up in there and the re-install of the driver may reset it.

---

### Post by LausArndon on 2008-04-17
I've got two CRT monitors at 1280x1024, two X screens, and restricted drivers disabled. Visual effects work fine. I'm using Gutsy and the only problem I've ever had is that one screen lags and the other is missing the title bar. I've had to settle for using emerald there, but I don't know why your visual effects wouldn't work.

I did have some trouble getting monitors configured properly, and it turned out that my sync and refresh rate were wrong in my xorg.conf. You should check to make sure everything matches up with what you have.

---

### Post by abh83 on 2008-04-17
Thx to all for your time and effort!

problem solved:
[http://forum.compiz-fusion.org/showthread.php?p=55220#post55220](http://forum.compiz-fusion.org/showthread.php?p=55220#post55220)

The solution was to disable Xinerama and enable twin view like what some of you mentioned.
:)

cheers once again!

---

### Post by loudnlownoma on 2008-04-18
> **abh83 said:**
> Thx to all for your time and effort!

problem solved:
[http://forum.compiz-fusion.org/showthread.php?p=55220#post55220](http://forum.compiz-fusion.org/showthread.php?p=55220#post55220)

The solution was to disable Xinerama and enable twin view like what some of you mentioned.
:)

cheers once again!

Glad you got it straightened out!

---

