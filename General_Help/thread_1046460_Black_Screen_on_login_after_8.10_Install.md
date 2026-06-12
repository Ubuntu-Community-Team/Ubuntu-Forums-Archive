---
title: "Black Screen on login after 8.10 Install"
date: 2009-01-21
forum: General Help
---

### Post by fragility14 on 2009-01-21
I recently tried to reinstall Kubuntu 8.10 64 bit, I had got new internet service and previously had to heavily modify settings for bug with wireless (was on a static connection without knetworkmanager and the ethernet was shut off, all of which I couldnt fix without internet...on the bright side I wanted a clean install anyway but didnt because of what a pain the wireless had been). 

I initially installed 8.04 32bit (because that's the cd I had) then downloaded and installed 8.10 64 bit...it goes to a black screen where I can see a cursor but nothing else...and the livecd doesn't load either. I checked the integrity, it is fine.

I'm on a GeForce 6600 PCI Express 16 video card, and am having way more driver issues than I remember.

please help me!

---

### Post by fragility14 on 2009-01-21
Can someone please help me with this problem? The only computer access I have is on a liveCD and I can't find a solution

---

### Post by abn91c on 2009-01-21
try removing compiz, ctrl+alt+f1 at the prompt do ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
``` then reboot

---

