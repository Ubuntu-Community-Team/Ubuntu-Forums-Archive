---
title: "Failed to load module fglrx with gnome shell"
date: 2011-11-12
forum: Desktop Environments
---

### Post by neopium on 2011-11-12
Hi everyone,

I really like Gnome Shell and was using it since its release on Fedora 15. Now that Oneiric is out, I plan to switch back to Ubuntu, that is much easier to use and configure IMHO.

So I just installed Oneiric on my MacBook Pro 8,2 (early 2011) equipped with an ATI HD 6750M.

Everything went very well during installation. I ran the software update tool and then I installed Gnome Shell (keeping LightDM).

I logged out and in again, and everything was super smooth and clean. Great!

But when I restarted my machine, it refused to start the X server, displaying a frustrating error message: "(EE) Failed to load module "fglrx" (module does not exist, 0)"

Sure you can't find it: I didn't install it! And I don't want to, as it is not compatible with Gnome Shell.

What can I do.

I search the web and found plenty of users having this problem (not with Gnome Shell however). And most of the time, the solution they found was to install fglrx, which is not what I want.

I also followed instructions here: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch)

To fully remove fglrx and reinstall -ati from scratch, but I still have the error message.

Any other clue is welcome.

Kind regards

---

### Post by neopium on 2011-11-14
I have re-installed Oneiric and the problem persists.

When installing, I chose to download updates during installation and to install the additional components (mp3, flash, etc.).

After installing, I restarted the computer. Everything worked perfectly.

Then I updated all packages (192 updates where waiting).

I restarted and everything worked well.

Then I installed Gnome shell from the link provided on gnome.org. I restarted and everything went well. 

I thought the problem was gone, did not do anything more (no extra installation nor package update). And the day after, when I rebooted my machine, I had the problem again: X refuses to start.

:confused:

---

### Post by typhoon_tip on 2011-11-14
Please post the output of this command on that machine:
```
update-alternatives --get-selections | grep gl_conf
```

---

### Post by neopium on 2011-11-14
> **typhoon_tip said:**
> Please post the output of this command on that machine:
```
update-alternatives --get-selections | grep gl_conf
```

I restarted my machine... and it worked (this time)

This is what I get when I run the command.

```

update-alternatives --get-selections|grep gl_conf
x86_64-linux-gnu_gl_conf       auto     /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf

```I will try to reboot a few times to check if I have the problem again...

---

### Post by neopium on 2011-11-14
I found a pattern and.. it's weird.

As I already said, I try to run Ubuntu on a Macbook Pro. This means that I have rEFIt ([http://refit.sourceforge.net/](http://refit.sourceforge.net/)) bootloader to switch between Mac OS X and Ubuntu at startup.

Here is the thing: if I boot on Mac OS X and then reboot on Ubuntu, it works like a charm. But if from Ubuntu, I reboot back to Ubuntu, then the error message appears again and X refuses to start (I tried the command line you gave me and obtained the same result as in my previous post).

Any idea why?

---

### Post by typhoon_tip on 2011-11-14
> **neopium said:**
> Any idea why?

Yes, you may have a dual card configuration: INTEL + ATI (onboard card during battery operation). I don't think MacBook has a BIOS option to disable the autodetection of the video card to use based on OS... Happens almost the same thing in my T400 if I enable that function.

EDIT: you may try to boot with and without battery, and shutdown instead of restart might lead also to different behaviour. After correct boot, please do this command and tell me what you get:
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
```

---

### Post by neopium on 2011-11-14
> **typhoon_tip said:**
> Yes, you may have a dual card configuration: INTEL + ATI (onboard card during battery operation).

I indeed have two cards Intel + ATI. The switch is a bit more subtle: it uses the ATI card only when hardware acceleration is required.

> I don't think MacBook has a BIOS option to disable the autodetection of the video card to use based on OS... Happens almost the same thing in my T400 if I enable that function.

There is no BIOS on Mac, it's EFI. And I don't think this is possible... I think the switch is managed by the OS, not the EFI, as it is dynamic and based on the API used... but thats a wild guess.

> you may try to boot with and without battery
:D
Not an option: I can't remove the battery, its integrated. Yeah, I know, I shouldn't have bought a Mac...

> After correct boot, please do this command and tell me what you get:
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
```

I will try that and let you know

---

### Post by typhoon_tip on 2011-11-14
> **neopium said:**
> :D
Not an option: I can't remove the battery, its integrated. Yeah, I know, I shouldn't have bought a Mac...

Roflll I wanted to say without power cord ! :D:D

---

### Post by typhoon_tip on 2011-11-14
> **neopium said:**
> I think the switch is managed by the OS, not the EFI, as it is dynamic and based on the API used... but thats a wild guess.

No this doesn't happen. Switching card is very intensive process for the system, so it happens usually when the power is switched (using integrated card saves a lot of power).

The problem may be like for me, that sometimes at start it randomly activated INTEL instead of ATI (I used FGLRX driver), and thus the system started with a similar error from XOrg.

If you have switcheroo enabled and detected, there are some script to force one video card at startup. :)

---

### Post by neopium on 2011-11-14
> **typhoon_tip said:**
> No this doesn't happen. Switching card is very intensive process for the system, so it happens usually when the power is switched (using integrated card saves a lot of power).

The problem may be like for me, that sometimes at start it randomly activated INTEL instead of ATI (I used FGLRX driver), and thus the system started with a similar error from XOrg.

If you have switcheroo enabled and detected, there are some script to force one video card at startup. :)

I rebooted from MacOS X... and X crashed... So the pattern I described earlier is not systematic.
I shutdown completely the machine and started it again and then X started normally.

I strange thing though, each time I try to login, the first attempt leads to a black screen and LightDM again. The second attempt succeeds.

Regarding the command line, I have no directory called vgaswitcheroo in /sys/kernel/debug, so it didn't work. How do I install and configure switcheroo?

---

### Post by typhoon_tip on 2011-11-14
> **neopium said:**
> How do I install and configure switcheroo?

Forget it, it is built into the Kernel, that's exactly what I needed to know. If there is no folder, then there is no vga_switcheroo enabled because it cannot detect the switcher.

I think you are stuck in that mode: if you want to use Ubuntu, you should start from a shutdown rather than restart, it should be fine all the times... I don't either want to suggest you to touch boot settings because it may break your OSX install.

---

