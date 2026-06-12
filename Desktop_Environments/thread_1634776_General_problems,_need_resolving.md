---
title: "General problems, need resolving"
date: 2010-12-01
forum: Desktop Environments
---

### Post by fallofshadows on 2010-12-01
Hello,

I've managed to dual boot my computer without it dying, and I'm running ubuntu 10.10 64 bit, on a dell inspiron 1545. So far I have not been able to see any wireless networks, and I cannot install ANY packages from the synaptic package manager. Is this a problem with 64 bit ubuntu, or with my dell? In the terminal it informs me that my chip set is not supported, as far as wireless goes, but I'm still confused about the problem with packages. Can anyone help?

If you need further system info, just tell me what to plug into the terminal and I'll post what it tells me. Thanks in advance, I really want to get ubuntu working as my main operating system :)

---

### Post by killa.fr0gg on 2010-12-01
Generally speaking, you should use the 32-bit edition - it's better, to put it simply. Unless you're dead-set on running the 64-bit version, reinstall with 32-bit and I'll be surprised if a good majority of your issues aren't resolved automatically.

Cheers!

---

### Post by fallofshadows on 2010-12-01
Running a live cd of the 32 bit version would let me know if those problems would be fixed, right?

And do you have any advice on reinstalling with the 32 bit version? Partitioning my hard drive makes me nervous, I've gone through one already due to ubuntu installation...

---

### Post by killa.fr0gg on 2010-12-01
For the most part, yes. The thing is LiveCD's are always slow (at least when compared to running off of an actual hard disk installation, but just the same it should be able to give you an idea of whether or not your various hardware components are gonna be recognized. Let us know!

---

### Post by fallofshadows on 2010-12-01
I should know for sure tomorrow. I have 10.10 loaded up on my flash drive, so I'll be working with that tomorrow; it's 1:43 in the morning here, so now is not the best time to be playing with my computer, since my roommate is asleep...

The biggest hassle is that I have to manually install Java in order to have internet access because of the way my college does things, but once I get that worked out I should have a better idea as to how well ubuntu functions with my computer. Hopefully the two get along, I've grown attached to ubuntu, it's more fun than windows 7 :p

---

### Post by fallofshadows on 2010-12-01
EDIT!!! I finally got my wireless problem solved! On Synaptic there is a package, "firmware-b43-lpphy-installer". This installed the drivers needed for my specific card, and now my computer detects wireless!!!! On that note, should I keep the 64 bit version? I really don't want to delete/reinstall everything, but if 64 bit is going to give me too many problems, I should just do it now and get it over with, yes?

Well, I'm running Ubuntu 10.10 32 bit from my flash drive, I have internet access via Ethernet cable, and here's some issues I have:

I tried installing the necessary drivers using Synaptic. These drivers should allow me to access wireless networks. Instead I got "unknown error"

E: initramfs-tools: subprocess installed post-installation script returned error exit status 1
E: bcmwl-kernel-source: subprocess installed post-installation script returned error exit status 1

The second error, bcmwl-kernal-source, looks like the same one I was getting on 64 bit ubuntu.

I also can't play .mp4 files, and when it automatically searches for the drivers needed, it comes up with none. Are these issues due to running ubuntu from my flash drive? If so, I'll just install the 32 bit version and get things worked out, but if these issues will persist, I really don't see a purpose of using ubuntu. I love the way it looks, but not having wireless and not being able to play mp4 files are HUGE drawbacks to me. It's like having a ferrari but not being able to leave 2nd gear... it looks nice, but it doesn't perform the way it should :P

---

