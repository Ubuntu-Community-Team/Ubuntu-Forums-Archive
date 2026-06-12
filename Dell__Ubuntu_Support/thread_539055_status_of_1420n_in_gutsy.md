---
title: "status of 1420n in gutsy?"
date: 2007-08-30
forum: Dell  Ubuntu Support
---

### Post by kuja on 2007-08-30
I'm interested in hearing how things are working on gutsy tribe 5 in an ootb install on a 1420n. 
I'd test things out myself but I simply don't have the bandwidth to do it (or the time really, but if I had the bandwidth I'd make the time ;))

A simple though not really "conclusive" checklist of things I'm interested in hearing about:

- x3100 graphics adaptor support (should be fine, but I'm curious)
- broadcom 10/100 ethernet network adaptor
- Intel Corporation PRO/Wireless 3945ABG Network Connection
- Intel Corporation 82801H (ICH8 Family) HD Audio Controller (ie: does sound still work)
- Suspend/resume
- Hibernate/resume
- Synaptics touchpad features
- Multimedia buttons?
- Bluetooth?
- Knetworkmanager ability to behave/function?

And anything else that might seem pertinent :)

---

### Post by rs3 on 2007-08-31
my assessment-in-progress of the 1420n in gutsy tribe 5:

- x3100 graphics adaptor support is fantastic.  compiz, enabled by default in tribe 5, works like a dream.
- broadcom 10/100 ethernet network adaptor--have not yet tried.  it is listed as an available connection in network manager, for what that's worth...
- Intel Corporation PRO/Wireless 3945ABG Network Connection works fine; sometimes i find network manager to be a bit slow to connect to my wifi router, but it works out of the box.
- Intel Corporation 82801H (ICH8 Family) HD Audio Controller is dead.  no sound yet. :(  i haven't been able to get any results so far.
- Suspend/resume--tried suspending, had trouble coming back up.
- Hibernate/resume--haven't yet tried.
- Synaptics touchpad features--feels very sensitive on the tap-to-click, but the scrolling edges work.
- Multimedia buttons--though sound is dead, the volume controls work.  haven't had any impetus to try the other media buttons without audio, as you might imagine. :D
- Bluetooth--ordered mine without bluetooth, can't test
- Knetworkmanager ability to behave/function--haven't tried it.

hope this helps!  and if anybody has a clue how to get sound back up and running, let us know!

---

### Post by kuja on 2007-08-31
Thanks for the positive feedback :) That was just the kind of information I was looking for.
Here are the results I'm seeing in Gutsy - My dist-upgrade from Feisty finished today.

**Bear in mind anybody that reads this post that this is my results from a dist-upgraded Dell install, not a fresh install of tribe 5**
- x3100 graphics adaptor support -Works well 
- broadcom 10/100 ethernet network adaptor- Haven't gotten to it yet, I hope so.
- Intel Corporation PRO/Wireless 3945ABG Network Connection- Works well
- Intel Corporation 82801H (ICH8 Family) HD Audio Controller - Works Well
- Suspend/resume - Haven't gotten to that yet
- Hibernate/resume - or that either
- Synaptics touchpad features - Works, scrolling works too. My old syndaemon and qsynaptics scripts are still in place also)......
- Multimedia buttons? - Works well
- Bluetooth? - I don't have anything bluetooth (at least not yet .... I put it on there for insurance)
- Knetworkmanager ability to behave/function? Besides it needing a few kicks to the balls, yes.(this statement *is* related to a bug report)
SD Card reader + Automount - Works well
USB + Automount - Works Well

rs3, try the following and it might be a foothold on getting your sound working:
```

sudo -s;
echo "options snd-hda-intel model=3stack" > /etc/modprobe.d/1420n-sound;
exit;

```

and afterwards reboot. if it does work, it likely won't work after suspending/hibernating and then resuming, there are more files to edit to take care of that if this works.

if it doens't work, pull up a shell and run "lsmod | grep snd_hda_intel"
If it's not loaded, run "sudo modprobe snd_hda_intel"

-- 

On a very disturbing sidenote, when the 2.6.22-10-generic kernel installed, and the automagic script ran, it failed to add the whole entry to the menu.lst - it left out the initrd line.

---

### Post by rs3 on 2007-09-04
i switched from amd64 gutsy to x86 gutsy, enabled proposed updates and backports, and found that sound works--but esound itself is broken.  strange.

i might try amd64 again with the tribe 6 desktop cd when it hits.

---

### Post by Az7 on 2007-09-05
What was the fix to get sound working?  I did a fresh gutsy install, then did a apt-get upgrade.

---

### Post by Az7 on 2007-09-05
Looks like there is a bug report located here for "[Dell 1420n audio not supported under Gutsy]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/131368")"

---

### Post by rs3 on 2007-09-05
i performed a dist-upgrade after adding the proposed updates and backports repositories; then, i disabled esound and performed a video fix for good measure (under gstreamer-properties), changing default output to X Window System (No Xv).

that seemed to do it for me.  however, i can't use esound, so my laptop doesn't make any system sounds (logout/login, et cetera).  everything else works.

---

### Post by kuja on 2007-10-11
Well, I just dist-upgrade yesterday to check how things look now, a week from release, and it doesn't look good. It looks like both sound and wireless are broken :( I didn't bother to investigate farther than that. 

(On a side note, modprobe snd_hda_intel returns an error module not found ???)

---

### Post by rs3 on 2007-10-11
Apparently the Intel X3100 has been blacklisted from Compiz Fusion...not rightly sure why, but since that's the graphics processor the 1420n ships with, we're without desktop effects for the time being.

I reverted back to the Dell 7.04 until the 7.10 RC becomes available.  But when I last had Gutsy running, sound was working fine for me--as long as I didn't try to suspend or hibernate.  Maybe things were different for me because I upgraded from Tribe 5 to Beta rather than starting from a Beta CD...?

In any event, I'm hopeful that the RC will run well.  I don't like running x86 when I have the option of running amd64, and unfortunately Dell only provided a patched x86 installation.

---

### Post by notwen on 2007-10-11
Not what I was wanting to see.  Looks as if I'll be waiting a while before upgrading my 1420n to Gutsy.  Hopefully a month post-release will be enough time to make a sound judgment on whether upgrading will be beneficial to us 1420n users.

---

### Post by kuja on 2007-10-11
As of the latest kernel adjustment (2.6.22-14.43) (released this morning, I think) The sound and wireless are back in a working state! Hurray!

(I've not tried a usable kernel since 2.6.22-10, though I've only tried a few)

Oh, and rs3, the RC is available now, so test away :)

---

### Post by rs3 on 2007-10-11
> **kuja said:**
> Oh, and rs3, the RC is available now, so test away :)

Excellent.  Grabbing it now!

---

### Post by mutenewt on 2007-10-11
Are you using a secure wireless network?  I'm very interested to know if Gutsy on a 1420n will support WPA.  Having lots of trouble getting it to work on other systems.

---

### Post by kuja on 2007-10-11
Yeah, I've got my router setup with WPA2.

---

### Post by mutenewt on 2007-10-12
Thx kuja - that's all i needed to know.  Now I can get a 1420n.  :)

---

### Post by tpischke on 2007-10-14
Another Datapoint here:

I've been on gutsy with my 1420n for about a month now.  For the most part it's been working very well with a few minor hiccups:

Issues I'm aware of:

3D is MUCH worse under gutsy using the new 'intel' drivers.  I haven't investigated why, but I suspect that the 3D is being handled by the CPU and not the graphics card.  Probably I could revert to the i810 driver, but since the 'intel' driver is the future, prefer to use that.

Another issue with the new intel driver, already noted here, is that Compiz is a wash.  Forget it.  I tried to get it working using a hack somewhere and that didn't work.

Can't play video of any sort using any player.  May be related to my attempt to get Compiz to work, interested to hear what other people report.

The Dual-Monitor configuration utility is useless.  Doesn't work and crashes the X server.  They may have fixed the crash, but I'm pretty sure it still doesn't work effectively as of RC.

All in all, I don't recommend upgrading to Gutsy unless you don't care about any of the above or are really hot for some of the other new features that gutsy offers.  Otherwise, better to wait a month or two until all the hollering by upgraders results in all this stuff getting fixed.

---

### Post by rs3 on 2007-10-14
I tried the RC on both my 1420n and my desktop box, and on both counts I was unable to justify the upgrade.  I'm sticking to Feisty for the time being.

That "Screens and Graphics" configuration applet seems to invoke my ire like nothing else.  And I can't seem to find any documentation regarding the Compiz Fusion blacklist on the Intel x3100 accelerator--I was able to use Compiz Fusion right out of the box with Tribe 5, and after adjusting my gstreamer-properties I could get video to play uninhibited...so what's up with that?

I really like some of what Gutsy has to offer, but I'm hoping that Hardy will come with a bit more polish, even at the expense of daring new features.

---

### Post by notwen on 2007-10-15
Looks like I'll be one of the few waiting for a month or three for the 1420n to become more compatible. =[

---

### Post by kuja on 2007-10-15
> **tpischke said:**
> Another Datapoint here:

I've been on gutsy with my 1420n for about a month now.  For the most part it's been working very well with a few minor hiccups:

Issues I'm aware of:

3D is MUCH worse under gutsy using the new 'intel' drivers.  I haven't investigated why, but I suspect that the 3D is being handled by the CPU and not the graphics card.  Probably I could revert to the i810 driver, but since the 'intel' driver is the future, prefer to use that.

Another issue with the new intel driver, already noted here, is that Compiz is a wash.  Forget it.  I tried to get it working using a hack somewhere and that didn't work.

Can't play video of any sort using any player.  May be related to my attempt to get Compiz to work, interested to hear what other people report.

The Dual-Monitor configuration utility is useless.  Doesn't work and crashes the X server.  They may have fixed the crash, but I'm pretty sure it still doesn't work effectively as of RC.

All in all, I don't recommend upgrading to Gutsy unless you don't care about any of the above or are really hot for some of the other new features that gutsy offers.  Otherwise, better to wait a month or two until all the hollering by upgraders results in all this stuff getting fixed.

Personally I couldn't get anything 3d (for example, anything that uses opengl) to work without the new drivers, it just crashed. That problem is gone.

Video playing of all sorts works for me. Perhaps you botched that during your attempt to make compiz work.

---

### Post by LMP900 on 2007-10-16
Good news, guys. Looks like Dell will be active in supporting the transition from Ubuntu 7.04 to Ubuntu 7.10. I don't know if this means that they will be providing a "remastered" version of 7.10 (à la 7.04), or simply provide fixes for known issues, but it's looking good regardless.

Relevant links:
[LIST]
[*][Dell's Linux Blog: Ubuntu 7.10 Update]("http://direct2dell.com/one2one/archive/2007/10/16/31817.aspx")
[*][Dell's Linux Wiki - Ubuntu 7.10]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10") (Check regularly for updates)
[/LIST]

---

### Post by notwen on 2007-10-16
Very cool, I hope they resolve the issues Compiz-Fusion has w/ the X3100 chipset.  Good to see Dell not forgetting about their new, but small Dellbuntu market. =]

---

### Post by mrc.gran on 2007-10-17
@notwen:

Gutsy's compatibility with Dell latest hardware (1420,1720 etc) has evolved a lot in the last few days since RC. I have hda sound and wireless without problems. 

Compiz is disabled but the X3100 intel driver supports it. Just create a file ~/.config/compiz/compiz-manager containing the line SKIP_CHECKS=yes . It will activate compiz in gutsy for your hardware. 

In [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) it's explained why the intel 965/x3100 is disabled by default: it won't play XV videos if compiz is enabled. The solutions:

1) Leave compiz enabled, but run gstreamer-properties and change the video default output to 'X windows system (no XV)'. Any gstreamer-based player, like totem-gstreamer (the default player), will play videos with no problem. Xine (and maybe mplayer) won't. Don't forget to activate desktop effects and do a sudo apt-get install compizconfig-settings-manager to get the complete control panel for compiz fusion.

2) Disable compiz, and activate EXA in your /etc/X11/xorg.conf, by putting the line Option "AccelMethod" "exa" inside your Device section. e.g.

Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Boardname       "intel"
        Busid           "PCI:0:2:0"
        Driver          "intel"
        Screen  0
        Option "AccelMethod" "exa"
EndSection

This is the correct way to enable XV videos, and everything (gstreamer,xine, mplayer etc) works perfectly. Currently, EXA and compiz do not work together (it crashes the X server), but they should, it's a current known bug in the intel driver and it will probably be solved in the next weeks. 


Regardless if you are using compiz or not, other 3D programs and 3D games work with X3100 on Gutsy.

---

### Post by cabbarosman on 2007-10-28
hey,

I created a filed named 'compiz-manager' in the folder /.config/compiz/ with the line SKIP_CHECKS=yes in it, but I still can't enable the visual effects in appearance preferences.

I have 1420n. Do you have any suggestions?

p.s. I also did the other steps you wrote about.

---

### Post by rs3 on 2007-10-28
I was able to get it to work by just installing xserver-xgl and rebooting.  (shrug)  However, Flash stopped working after that, which may or may not be related.

---

### Post by cabbarosman on 2007-11-04
Great!:frown: I installed the last compiz upgrade and now my resolution got out of control. I have the 1440x900 monitor but no resolution option for that is available...

Do you know how to restore video settings or just how to reinstall the necessary stuff?
 (I certainly wouldn't like to reinstall the whole ubuntu although my /home partition is separate.)

---

### Post by rs3 on 2007-11-04
Bizarre.  Are you using xserver-xgl or one of the more roundabout fixes for getting Compiz up?  Additionally, are you using the "intel" xorg driver, or the "i810" xorg driver?

On an aside, I reverted to the x86 arch and found Flash and XGL to coexist with Compiz just fine in Gutsy.  But I'm still unable to do anything OpenGL reliably, otherwise.

---

### Post by cabbarosman on 2007-11-04
I just did what mrc.gran's suggestions above. Namely, I added SKIP_CHECKS=yes,  set 'X windows system (no XV)' and activate EXA in /etc/X11/xorg.conf. But these didn't change anything. I still couldn't enable the desktop effects but the resolution was fine. Then I installed the compiz upgrade that popped up two days ago and after I rebooted my resolution settings were gone crazy.

I deleted the SKIP_CHECKS=yes file and set the gstreamer video default output back to automatic. The xorg file was already changed with no exa. Still I am using my lovely 1440x900 monitor with just a 1024x768 res.   

I am using the intel graphics card driver.

Do you know anyway to reset everything? (Maybe replacing my xorg.conf with a default one?)

---

### Post by cabbarosman on 2007-11-04
okay, I entered "sudo dpkg-reconfigure xserver-xorg" and everything came back to normal
I really hope they release an official upgrade to enable compiz on x3100 and make every video component run smoothly at the same time.

---

