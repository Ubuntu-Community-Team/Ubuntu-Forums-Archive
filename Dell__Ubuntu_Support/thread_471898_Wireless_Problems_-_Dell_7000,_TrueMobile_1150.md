---
title: "Wireless Problems - Dell 7000, TrueMobile 1150"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by rjmarshall on 2007-06-12
Hi,

I am new to Ubuntu...which may become more apparent as time goes on :)

I am trying to install from the ubuntu 7.04 livecd and having a lot of problems with the Dell TrueMobile 1150 wireless card.  I did an install the other day and got the network up and running, installed all the updates, and when I rebooted the card disappeared.  The network manager no longer saw it.

I did an lspci but didn't see it.  However when I do an lshw I do see the card on the pcmcia where it should be, but I don't know how to force the system to recognize it.

I am in the process of doing my third install from the CD (which with a Dell 7000 takes a very, very, long time :), and hoping that it will work this time.  I have tested a different (Linksys) card on the laptop and it seemed to work.  I also tested the 1150 on another laptop (running XP) and it worked.  So I know that the card works - after all, it was working fine until I rebooted after the update.

Is there something else that I can check?  How do I find out why the card shows up with lshw and NOT with lspci?

Thanks,

Rob

---

### Post by rjmarshall on 2007-06-12
Additional note:  When I unplug and re-plug the card I see:

hermes @ 00010100: Card removed while waiting for command 0x0021 completion.

In the /var/log/messages file.  Anyone know what that means?

Also, the access point that I'm using is a wireless G from Linksys.  The card itself is an 802.11b (at least I assume that it is - it's fairly old).  I don't know if that's important, but I thought I'd mention it.

Thanks,

Rob

---

### Post by rjmarshall on 2007-06-12
I did find a comment in another forum about the firmware for the TrueMobile 1150, so I upgraded from 6.10 to 8.72 (I think).  Anyway, that didn't help...

---

### Post by rjmarshall on 2007-06-13
I opened a new thread in the networking wireless forum since I don't think that this is "Dell" specific.  Just looking at the survey results on people having wireless problems under 7.04, I see that I am not alone.

Rob

---

