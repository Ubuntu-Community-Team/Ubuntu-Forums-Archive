---
title: "ubuntu will not work after restarting the computer"
date: 2010-07-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nin3break3r on 2010-07-08
ive taken a recent interest in trying linux ubuntu out and have to say its a good os exept for one thing everytime i restart the computer ubuntu starts up fine but when i shutdown my computer the beginning ubuntu symbol shows up and after it loads it goes to a black screen and thats about it any ideas on fixing this issue? and if you ask  the computer im using is a dell 2350 with 512 ram and a 256 video card

---

### Post by mörgæs on 2010-07-08
Which screen card do you have? Please post the output of 

```
hwinfo --gfx
```

---

### Post by Nin3break3r on 2010-07-08
idk its a intergrated card

---

### Post by mörgæs on 2010-07-09
Yes, but please run the command and post the output. It will tell a lot more of the card.

Which version of Ubuntu are you using?

---

### Post by Nin3break3r on 2010-09-07
the version is 9.10 and as for the video card all its telling me is that its a intel i also have a nvidea series 6 video card but for some reason it wont work when i enable it and start ubuntu it gives me this long stream of error messages

---

### Post by garvinrick4 on 2010-09-07
If you did not have hwinfo installed run this command copy and paste video card to your thread so morgaes has something to work with, he is trying to help you out.

```
sudo lspci -v | less
```

---

### Post by Nin3break3r on 2010-09-07
> **garvinrick4 said:**
> If you did not have hwinfo installed run this command copy and paste video card to your thread so morgaes has something to work with, he is trying to help you out.

```
sudo lspci -v | less
```

0:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
        Subsystem: Dell Device 0147
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 1
        Kernel driver in use: i915
        Kernel modules: i915
i think this is it

---

### Post by mörgæs on 2010-09-07
This screen card works well on Ubuntu 9.10, but not 10.04. The easy solution would be a clean install of 9.10, which can be downloaded here:

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

9.10 is supported until april 2011, at which time you will have 10.10 and 11.04 to choose from.

---

### Post by Nin3break3r on 2010-09-07
> **mörgæs said:**
> This screen card works well on Ubuntu 9.10, but not 10.04. The easy solution would be a clean install of 9.10, which can be downloaded here:

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

9.10 is supported until april 2011, at which time you will have 10.10 and 11.04 to choose from.

hmm this is wierd i install 10.04 and the graphics card decides to work

---

