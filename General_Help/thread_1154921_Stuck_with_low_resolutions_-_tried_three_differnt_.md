---
title: "Stuck with low resolutions - tried three differnt cards"
date: 2009-05-10
forum: General Help
---

### Post by Bartender on 2009-05-10
This is with 9.04, on a PIII ASUS motherboard...
I need some help with xorg, video output, etc.
I have a couple old (2000 or thereabouts) CRT monitors.  Both of them have one pin missing - not broken, just not there - in the middle row of their VGA input cables.  Both of them have dedicated cables so I can't just jack a different cable in.
Also have a Dell 1905FP LCD monitor.  All the pins are there and it also has a digital in.
I've tried two ATI cards (a 9200SE and an old Rage card) all I get is 800x600.
Tried a newer ASUS Nvidia v9400 card, same thing - 800X600.
In Preferences>Display the monitor is always unidentified.  The "Detect Displays" button doesn't do anything.
Went into xorg, and there are NO entries of any sort.  It's just the basic template.
With the Nvidia card in, I ran that command to ask xorg to reconfigure itself...no diff.  Still just the basic template.

I've read a couple of posts that indicated that xorg does not play the same role it did in earlier versions.  Is that true?

Anyways, sure would appreciate some ideas!

P.S.  I woulda tried installing the Nvidia 177 drivers but I'm on dial-up.  Is there any relation between the Nvidia drivers and xorg?

---

### Post by danwood76 on 2009-05-10
The xorg.conf file is no longer needed with the latest xserver.
The two ati cards are supported by the ati-xorg driver and should work fine with jaunty.

The first thing I would check is that the correct driver is loading for those two.
so run the following commands with either installed:
```

lsmod | grep 'ati'
lsmod | grep 'radeon'

```
That will list if either of those drivers are loaded, if neither show any results then you should specify the ati driver in the xorg.conf file as it will take notice of it.

---

### Post by CatKiller on 2009-05-10
Hey, bartender. Didn't we go through this before?

> **Bartender said:**
> I've read a couple of posts that indicated that xorg does not play the same role it did in earlier versions.  Is that true?

Yep. More-or-less. The X.org server is still used, but the assumptions that it uses were made quite some time ago, and the basic way that it works isn't really appropriate for the way that people want to use their computers these days. It's all in the process of some major changes. The idea is that X will still do what X does - defining boxes on the screen - but all of the configuration, hotplugging, and so on will be handled by other systems that pass appropriate information to X which on its own has no real idea of what the actual hardware is. It's an abstraction thing. xorg.conf just has a skeleton layout that points to the automatically-configured stuff. It's still possible to over-ride that in xorg.conf, though.

The reason those monitors aren't detected correctly is either because they aren't giving out EDID information, or the information they are giving is incorrect, or the grahics driver isn't passing the information along. You can still specify the information yourself though as I detailed in [my other post]("http://ubuntuforums.org/showthread.php?p=7244593#post7244593"). The refresh rates are the most critical part for getting the resolution you want, but you might also want to specify the screen size (for DPI calculations) or tell the driver to ignore the EDID information altogether if the information is incorrect (as the data from my monitor is).

---

### Post by cmost on 2009-05-10
The new xserver does not require an xorg.conf, however, if one is present, it overrides defaults.  Instead of swapping out video cards, boot up Knoppix or the latest Sidux.  If your resolution is detected properly (which I bet it will be) then you can copy that xorg.conf to a USB key.  Then, replace the xorg.conf in Ubuntu with the new one.  Make sure you install yoru proprietary drivers (i.e., ATI or Nvidia) BEFORE you replace your xorg.conf file in Ubuntu because doing so will overwrite the xorg.conf with an updated generic one.  You will need to edit the new xorg.conf to enable the ATI / Nvidia driver.  Good luck!

---

### Post by Bartender on 2009-05-11
Yeah, Cat, we did.
I apologize.  I'm on dial-up, so there's that.  But sometimes I just get lazy and want you guys to spoon-feed me instead of doing some homework.
Took the PC, with the V9400 Nvidia card, to a friend's house with broadband.  Hooked it up to their Gateway 20" CRT, and suddenly Ubuntu was displaying at a higher resolution.  The Gateway has a fully-pinned D-sub cable, but so does the Dell 1905 LCD that I tried at home.
Didn't understand what was happening, but at least things seemed to be going in the right direction.
The 9.04 installation had never been updated (dial-up) so I asked Synaptic to do that, then went into Hardware Drivers and activated the identified Nvidia drivers.
When I got home, I connected the PC to a funky old IBM P200 20" CRT and went into Nvidia X Server.  Impressive.  This was the first time I'd ever seen ANY operating system correctly identify the IBM monitor.

---

### Post by CatKiller on 2009-05-11
No worries. Personally, I'd rather monitor manufacturers had got EDID working right on the products they'd made. Then we wouldn't have to do this at all.

So you've got the resolution that you want on one of your monitors? That's good. If you want the others to get the resolution that they can do then you're probably going to have to put the refresh rates in yourself. It's not too bad.

---

