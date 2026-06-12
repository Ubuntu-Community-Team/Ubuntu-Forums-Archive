---
title: "Terrible screen tearing - vsync not working"
date: 2009-04-27
forum: General Help
---

### Post by ZankerH on 2009-04-27
OK, I've searched the forums, and I'm aware of the fact that this is a known compiz bug, but this is downright annoying. I can not get vsync to work, I've enabled the sync to vblank option in both nvidia-settings and the compizconfig settings manager, and the tearing is still there. I should also note that I use two monitors in a twinview configuration, and the tearing is only present on the primary monitor, regardless of which one I set nvidia-settings to sync to. I use the nvidia geforce 8800GTS 512 graphics card, with the proprietary 180 drivers.

---

### Post by ZankerH on 2009-04-27
bump for rage-inducing bug

---

### Post by ZankerH on 2009-04-27
bump back to 1st page

(yay, helpful community! linux for human beings!)

---

### Post by ZankerH on 2009-04-27
one more bump

---

### Post by feffo on 2009-04-29
I've also this problem with my ati 9500pro and in my eeepc (intel gma945). I can set vsync in game with the driconf but the sync-to-vblank option in compiz doesn't work and the tearing is very annoying!!
I haven't found nothing that can repair this and people seems not to care about this. There must be a way to activate the vsync in compiz, the wobbling windows need that!!

---

### Post by amadeus266 on 2009-04-29
I used to have this problem when I had my ATI 9200. Solved it by simply turning off sync to vblank.

---

### Post by feffo on 2009-04-29
But I activated Sync-to-vblank because there was and there is screen tearing. The is tearing with and without the option active!!

---

### Post by Prometheus28 on 2009-06-17
I've also had this problem since forever. Ubuntu cannot vsync. Nobody on ubuntu has vsync. Some people think they do, but really they do not.

There is no way to enable vsync on ubuntu. This is a limitation of xorg-x11. Nothing can be done to correct the situation. Sorry for the bad news. Hoepfully one day it might work.

---

### Post by cariboo on 2009-06-17
I beg to differ, I'm running Jaunty on an atom powered media center pc, and using the drivers from [here]("https://launchpad.net/~intel-gfx-testing/+archive/ppa"), I have zero tearing problems. Running Karmic on my main computer that has an 8400GS with 512MB and the Nvidia 180.60 drivers, there are no tearing problems either.

---

### Post by robert114 on 2009-06-17
I too have enabled Vsync in Nvidia settings and compiz and the tearing went away.

I'm using the latest nvidia drivers of the nvidia website. But i guess the ubuntu nvidia drivers should work.

Here is what i did:
1. enable sync to vblank in CompizConfig settings Manager
2. enable sync to vblank in NVIDIA X Server Settings (2 instances)
3. add a startup program in startup applications with this command:
 'nvidia-settings -l' (without the quotes)

Good luck!

---

### Post by Prometheus28 on 2009-06-17
> **cariboo907 said:**
> I beg to differ, I'm running Jaunty on an atom powered media center pc, and using the drivers from [here]("https://launchpad.net/~intel-gfx-testing/+archive/ppa"), I have zero tearing problems. Running Karmic on my main computer that has an 8400GS with 512MB and the Nvidia 180.60 drivers, there are no tearing problems either.

Interesting, perhaps intel drivers are capable of vsync.

Because I assure you, that your nvidia drivers are tearing, but they are just barely notice able. You are running 8400gs, no doubt that makes tearing less noticable. I am running 7600 gs, which is noticable when I move windows or play games.

Just because you don't notice tearing, on a fast computer, doesn't mean tearing doesn't happen..

To test for yourself:: move a dark window against a light background rapidly, at the same time attempt a screenshot, you will see tearing

---

