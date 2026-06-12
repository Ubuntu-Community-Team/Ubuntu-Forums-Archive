---
title: "Sub-woofer dead with Ubuntu 13.10 on Dell 17R"
date: 2013-10-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mikesmithv on 2013-10-18
The sound is shallow without the sub-woofer since only the tiny left & right speakers are working.  There was a fix for 13.04 which made the sub-woofer work but that doesn't work with 13.10.  That fix was to append the following line to the end of /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=ref

If I add that line under 13.10 the sound goes dead and I get no sound from any speaker.  Is there some other fix for this latest version?

---

### Post by mikesmithv on 2013-10-18
UPDATE:  The steps below do nothing for the problem.  See my last post in this thread for the real solution.

After googling around I see that it appears to be a common problem.  [Here is a web page]("http://linuxsagas.digitaleagle.net/2012/11/23/sound-for-inspiron-17r") about just that.  I tried every combination of things mentioned there but nothing makes the sub-woofer work in Ubuntu 13.10.  Interestingly, I do now have a sub-woofer control in the sound panel, but it is dimmed (disabled).  Below I describe the modifications that got me that far, but like I said, still no sound from the sub-woofer

In Terminal type the following:
> sudo gedit /etc/pulse/daemon.conf

Uncomment and modify the following lines:
> enable-lfe-remixing = yes
default-sample-channels = 3
default-channel-map = front-left,front-right,lfe

Next type the following:
> sudo gedit /etc/pulse/default.pa

Append the following line to the end of that file and restart:
> load-module module-combine channels=3 channel_map=front-left,front-right,lfe

The Intel codec is IDT 92HD91BXX and it seems to be a popular one used in many other computers beside Dells.  Hopefully there will be some movement to make this work someday.

---

### Post by solid.danil on 2013-10-20
I've downgraded my Ubuntu to 13.04 as there were a lot of bugs. But [here]("http://askubuntu.com/questions/361441/subwoofer-doesnt-work-on-dell-inspiron-17r-after-upgrade-to-13-10") was given an answer. Could you try it?

---

### Post by mikesmithv on 2013-10-20
I tried it and it works!  Here are my version of those steps (with a little more detail):

In "Ubuntu Software Center" search for "alsa-tools-gui" and install it.

Open Terminal and type hdajackretask and press Enter.

In the window the comes up check "Show unconnected pins" checkbox in upper right-hand side.

Scroll down and find "Pin ID: 0x10" and under that do the following:
Check the "Override" checkbox.
Select "Internal speaker (LFE)" in pop-down menu.

Click "Install boot override" button in lower right-hand side.

Restart computer - sub-woofer works!

Maybe it's my imagination but the sub-woofer sounds better than ever doing this patch.  Even better, when I plug in the headphones the speakers go completely silent now.  With Ubuntu 13.04 using the "options snd-hda-intel model=ref" patch I mentioned above the sub-woofer still had sound when headphones were plugged in.  Now the sound functions are all working as they should.  Thankyou so much for that post.

---

### Post by prangfamily on 2013-10-22
Had try this for my Asus G73JH -A1 and even if the subwofer button did not appear the bass started working :)

---

### Post by muel2 on 2013-12-17
works like a charm on a Dell Studio 1557 (STAC92HD73)
but would be nice to know, what hdajackretask actually changed, and if it could be done with pulse/alsa config (which still fails under 13.10)

---

