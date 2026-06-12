---
title: "[SOLVED] Fedora 10 and Nvidia - text splash"
date: 2009-01-03
forum: Fedora/RedHat and derivatives
---

### Post by BigSilly on 2009-01-03
Installed Fedora 10 yesterday from a DVD that came with Linux Format mag, and mostly I've been very impressed. I'm less impressed though, with their handling of proprietary drivers. Obviously I'm aware of the Fedora mantra with regards proprietary drivers, but nevertheless I'm still surprised at their "head in the sand" approach. Other distros seem to handle this better.

Anyhoo, I managed to enable the Nvidia driver OK via extra repos, and can now get desktop effects, OpenGL settings etc, but I still only get the Commodore 64 bootsplash, rather than a proper graphical boot as many in the modern age would hope to see. Also, on shut down I just get garbled text instead of the splash again.

I have been on the Fedora forums, and found a reference to adding the option vga=318 to the grub conf, but this hasn't worked and I still get the circa 1980's progress bar etc.

Now I know the Ubuntu forums is the friendliest place on the net, so I'm sure someone here will be able to help! Thanks in advance.

EDIT: I'm now reading that Nvidia support could be dropped altogether in future Fedora's due to it's closed nature. That's really disappointing, and I only hope this doesn't have an effect on the Linux world overall, as I would really have to draw the line there I'm afraid.

:(

---

### Post by BigSilly on 2009-01-03
OK I've fixed it for now. It looks like the option I needed was vga=792, which makes more sense anyway. I now get the lovely new splash at boot. Great.

However, I still have some concerns about the future of Nvidia and Linux. Sure, it's easy enough to say "go buy ATI", and sure I may do that, but that's really not a long term solution for Linux on the whole. Everyone is much better off if Nvidia and other such hardware vendors are on board and positive.

As things stand, how is the state of play with Nvidia and Linux at the moment? Anyone here have any real insight into it? Thanks.

---

### Post by pelle.k on 2009-02-04
> but I still only get the Commodore 64 bootsplash, rather than a proper graphical boot as many in the modern age would hope to see.
If you ask me, i think this looks just as pretty, but way more professional than any "glitz" bootsplash. Although i agree that plymouth is a cool technology. But if and when they go too far with the "cool effects" i will turn them off.

> I'm now reading that Nvidia support could be dropped altogether in future Fedora's due to it's closed nature.
I don't understand? Nvidia propreitary drivers were never in the fedora repos, so how could they drop something non existant?
If rpmfusion would drop the packaging of the nvidia drivers however, i would be very surprised.
Xorg's nv and nouveau are completely free so i don't think those are what you meant?

The Fedora folks never aimed for the windows converts or newbie crowd. So the nvidia driver issue is, in fact, an non issue for the intended user base. At least i'm very comfortable with the "fedora way".

---

### Post by igknighted on 2009-02-04
> **BigSilly said:**
> OK I've fixed it for now. It looks like the option I needed was vga=792, which makes more sense anyway. I now get the lovely new splash at boot. Great.

However, I still have some concerns about the future of Nvidia and Linux. Sure, it's easy enough to say "go buy ATI", and sure I may do that, but that's really not a long term solution for Linux on the whole. Everyone is much better off if Nvidia and other such hardware vendors are on board and positive.

As things stand, how is the state of play with Nvidia and Linux at the moment? Anyone here have any real insight into it? Thanks.

If we all just roll over and take it, nvidia won't be motivated at all to change status quo.  In that sense, I applaud Fedora for taking this step.  However, there's nothing about Fedora that will ever not let you use Nvidia's binary graphics driver, and it will always be packaged in RPM Fusion for easy install.  All Fedora is going to do is switch to Nouveau as the default driver, replacing the currently awful nv.

---

### Post by Noblacktie on 2009-02-06
And even if RPMFusion for some reason decides to no longer host nVidia drivers, there is still the option of compiling it yourself.

I wish these hardware companies would just make their drivers open source once and for all if they don't plan to support Linux. The Linux community is so proactive and progressive it's amazing that not more companies take advantage of these traits.

Hopefully, ATI's move to release their drivers as open source will encourage nVidia to follow suit.

---

