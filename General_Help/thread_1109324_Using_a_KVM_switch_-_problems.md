---
title: "Using a KVM switch - problems"
date: 2009-03-28
forum: General Help
---

### Post by Thrasonic on 2009-03-28
Hello all.  I have a PC that dual boots Windows and Kubuntu 8.10.  I find myself needing to work on other computers at my desk on occasion so I purchased a Belkin KVM switch.  It's working fine, but it's kind of screwing with my Kubuntu experience/settings, specifically video.  The problem is that I don't know for sure if it's the KVM switch or having to switch from a DVI interface to a VGA interface that's messing up things.

When I installed Kubuntu a few weeks ago I was using the DVI interface on my video card.  The KVM switch supports VGA, so I switched cables.  When I booted into Kubuntu the "Auto" feature on my monitor didn't really fix the problem with the image on the screen being to far left so I changed my screen resolution from 1650x1050 (or something like that) to 1440x900 or something similar.  That worked okay, but when I went into the display settings to change it back to the recommended resolution there was no longer an option for 1650x1050 or whatever it's supposed to be.  I rebooted but the problem continues.

Is this a known issue with Linux and KVM switches or is there something I can do to fix this?  Even if reinstalling Linux is the only way to fix it I'll do that.

---

### Post by Thrasonic on 2009-03-28
bump

---

### Post by Thrasonic on 2009-03-28
bump

---

### Post by Thrasonic on 2009-03-30
bump

---

### Post by BoogeyOfTheMan on 2009-03-30
I just read another thread that said something about KVM switches not sending EDID info properly. It may be that with the KVM, the display manager thinks your monitor cant handle the higher res.

Sorry that I cant give more info, and I dont remember what thread it was, but a search for EDID, KVM, resolution, etc might help ya.

---

### Post by Thrasonic on 2009-03-31
Thanks for the reply.  Anyone else have any ideas?

---

### Post by Thrasonic on 2009-04-01
bump

---

### Post by dandnsmith on 2009-04-01
It has to be something like that - when I switched monitors (involuntary, forced by failure of my AOC monitor), I suddenly had this problem.

I resolved it by continuing to switch the keyboard and mouse through the switch, but coupled that with using VGA for one PC, and DVI for the other. This works, but makes for a longer switching sequence (which I get wrong sometimes).

---

### Post by Thrasonic on 2009-04-01
It appears that if I boot Kubuntu with the KVM switch on the Kubuntu machine, so I can see it boot up, it works fine.  When I log in I have the correct display resolution.  The problem comes up when I'm in my other computer, computer B, and I turn on my Kubuntu computer, which we'll call computer A.  If I do that then the resolution is all screwed up.

I did a search for EDID, KVM, resolution as BoogeyOfTheMan suggested and it turned up a lot of good information.  But it's truly A LOT of information so it's going to take a bit of time to sift through, testing things here and there until I figure out what exactly will work for me.  I'll keep you all posted and give you my solution once I find it.

---

### Post by BoneslikesLinux on 2009-04-22
Similar problem with 8.04 but I found a way around it. For some reason the box will fire up with normal res (1280x1024) with monitor connected directly but through the KVM it won't go above 800x600. I have an Nvidia card and I found that if I use nvidia-settings and set the resolution while connected directly to the monitor, I can then reconnect the KVM switch and the res stays at 1280x1024. No idea how to do this with an ATI card but I have done this on 3 machines on 2 different KVM switches and it works for me. For the unititiated, nvidia-settings can be installed  from a terminal with the following line
sudo apt-get install nvidia-settings
It then can be run from a terminal or from System/Administration/NVIDIA X Server Settings, the resoltion selected and saved to configuration. I couldn't do this as a user so logged in as root and changed it then logged back in as user and all is fine.
Hope this helps someone.

---

