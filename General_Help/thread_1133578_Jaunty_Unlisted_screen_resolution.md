---
title: "Jaunty: Unlisted screen resolution"
date: 2009-04-23
forum: General Help
---

### Post by martin_legion on 2009-04-23
Hi. Yesterday I installed Ubuntu 9.04 RC and I see that the screen resolution I used to have in Intrepid is gone. I used 1152x864, but now it jumps from 1024x768 to 1280x1024.
I tried sudo dpkg-reconfigure xserver-xorg but nothing changed. I restarted gdm and rebooted after that, and 1152 is still missing.
Anyone?

Thanks

---

### Post by martin_legion on 2009-04-23
Wow, not a single reply to such a simple issue?
Usually I get a reply instantly! That's why this forum is so great.
C'mon!
Please?

---

### Post by DagMan on 2009-04-23
I had it bookmarked as I'm not really sure how to go about it since the xorg.conf file isn't as verbose as it used to be and things are handled within other files as well now, so I was going to wait even longer to see if you hadn't had a reply as not to needlessly run the thread off of the list of ones with zero replies... how I found it in the first place.  Since that's now been done, post your xorg.conf, and state your video card.  I'm really not as quaified as I was for your "simple problem", that you and google can't solve, as it isn't handled the same way it used to be when it comes to how the xserver gets configured.  If no one else gets to it though, rest assured that someone is here to at least have a look at it.. just not today, for me, as it's bedtime in my part of the world.

---

### Post by martin_legion on 2009-04-23
> **DagMan said:**
> I had it bookmarked as I'm not really sure how to go about it since the xorg.conf file isn't as verbose as it used to be and things are handled within other files as well now, so I was going to wait even longer to see if you hadn't had a reply as not to needlessly run the thread off of the list of ones with zero replies... how I found it in the first place.  Since that's now been done, post your xorg.conf, and state your video card.  I'm really not as quaified as I was for your "simple problem", that you and google can't solve, as it isn't handled the same way it used to be when it comes to how the xserver gets configured.  If no one else gets to it though, rest assured that someone is here to at least have a look at it.. just not today, for me, as it's bedtime in my part of the world.

Thanks for the replay DagMan.
Let me tell you that I changed to the 64bit version, just for fun :) and the problem keeps the same.

Video card info:
```
$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690 [Radeon X1200 Series] [1002:791e]
```

xorg.conf
OMG!!! I was about to paste the output of "cat /etc/X11/xorg.conf" and I see that THERE IS NO OUTPUT. The file is empty! :O

---

### Post by DagMan on 2009-04-23
Have you tried using the fglrx driver to see if it supports the resolution?
**apt-get install xorg-driver-fglrx**
If you already have it installed, then try the following before a reboot:
**sudo aticonfig --initial**

Uninstalling the driver might require a little help if it doesn't work out or makes your particular graphics card laggy in compiz, like it does mine, but it shouldn't be hard.  The fglrx driver also requires a little setup on the multimedia side on some cards, so be aware of that and that its fixable with a few settings edited if you run into it.

---

### Post by martin_legion on 2009-04-24
I installed that driver (it wasn't installed already) and after reloading gdm my PC freezed and there was no way of bringing it back to life. I rebooted, and as soon as gdm loaded, freezed again. I had to boot in failsafe and change the settings to the default.
What I did NOT do, because I didn't know the command existed, is aticonfig --initial.
I will try that today and tell you how it went.
Thanks!

---

### Post by martin_legion on 2009-04-27
> **DagMan said:**
> Have you tried using the fglrx driver to see if it supports the resolution?
**apt-get install xorg-driver-fglrx**
If you already have it installed, then try the following before a reboot:
**sudo aticonfig --initial**

Uninstalling the driver might require a little help if it doesn't work out or makes your particular graphics card laggy in compiz, like it does mine, but it shouldn't be hard.  The fglrx driver also requires a little setup on the multimedia side on some cards, so be aware of that and that its fixable with a few settings edited if you run into it.

I've installed fglrx driver and after running aticonfig --initial I get this:
aticonfig: No supported adapters detected

I don't dare rebooting right now, because I can see what's going to happen...

---

### Post by martin_legion on 2009-04-27
Rebooted.
At gdm startup system freezed.
Booted in recovery mode.
Executed:
apt-get remove --purge xorg-driver-fglrx
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
dpkg-reconfigure xserver-xorg
apt-get install --reinstall xserver-xorg-core

and now I'm again where I started: 1152x864 is still missing.

Where are all the configurations that used to be in xorg.conf?
Running dpkg-reconfigure xserver-xorg is rather useless. It just configures the keyboard and makes no changes to xorg.conf.
Could anyone give me a hand with the configuration file? 

Thanks

---

### Post by DagMan on 2009-04-27
I'm at a loss.  I was hoping the aticonfig utility would write one, but in the past, for me, its always needed something in xorg.conf to write to even if it was a really minimal file. Perhaps that's no longer the case.  One thing to try, is to pop the live cd in and see if you have an xorg.conf file, or to install the fglrx driver from the cd and see if one gets written, and then try copying it to your hard drive to see if it works.  It may give you a clue about wheather the driver is going to write an xorg.conf too, in the case that the live cd doesn't have one either when you boot into it.  Keep in mind that if you install fglrx from within the live cd, you can't simply restart X and start testing it out because the kernel module won't load until you reboot.  You can't just run depmod either.  I don't know why it does that.

 Apart from that, the only other thing that might work, and its sort of far fetched the way its sounding, is to use the force option which will make the aticonfig utility try to write the info about itself into xorg.conf despite it thinking it isn't a valid xorg.conf (or a non-existant one)
**aticonfig --initial -f**

If these things don't work then I think the best thing is to open a new thread stating something like "fglrx won't initialise and xorg.conf blank upon setup".  Or simply "xorg.conf blank upon install, can't adjust options" since I'm not able to help and there hasn't been any other attention in the thread.  Those would be more specific topics I think, as they sort of sound like they are closer to where the starting point is going to be, though looking at my /etc/X11 directory and the backed up files as fglrx initialised, I'm now not sure I had an xorg.conf to begin with either...

---

### Post by martin_legion on 2009-04-27
It does create the xorg.conf, but it doesn't set any driver or any screens or options of any kind. It just puts Identifier "Configured Monitor" and Identifier "Configured Video Device" and little else.
Some time ago, I think I remember that command at least selecting the vesa driver or some generic parameters, but not now, and I if Xorg configurations are not in xorg.conf I have no clue where they might be.
I'm a little tired to fight today.
I'll try that -f thing some other day.
And thanks a lot for your replies, DagMan.

---

### Post by DagMan on 2009-04-27
Dont give up on using the tiny xorg.conf then.  It may be all the fglrx installer needs to set things up properly, assuming you really meant entirely blank before, and not just empty entries within xorg.conf

---

