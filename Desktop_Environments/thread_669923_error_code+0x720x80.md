---
title: "error_code+0x72/0x80"
date: 2008-01-16
forum: Desktop Environments
---

### Post by Toxicityj on 2008-01-16
Yesterday I installed Kubuntu and went to boot it up and on the loading screen, it just froze. i let it sit for like 5 minutes and the loading bar didn't get any further than about 1/10 of the way. So I tried booting in safe mode and ended up with a screen full of text i didn't understand. and the second to last line mentioned an error. so I figured my computer couldn't handle Kubuntu and went with Xubuntu. It's doing the same thing... took a pic of the screen:

[http://img.photobucket.com/albums/v644/toxicityj/100_1272.jpg](http://img.photobucket.com/albums/v644/toxicityj/100_1272.jpg)

---

### Post by Toxicityj on 2008-01-17
bump

---

### Post by tec_know_joe on 2008-02-18
I have the same error code.* I'm really new to linux so I'm not much help, but I am looking for an answer.

---

### Post by Toxicityj on 2008-02-24
does no one know how to fix this? I've posted this question on 3 different linux boards and no one knows what to do.

---

### Post by Simon Bridge on 2008-03-26
Have you tried passing "ide=nodma" to the kernel?

---

### Post by gcranston on 2008-04-28
> **Simon Bridge said:**
> Have you tried passing "ide=nodma" to the kernel?

I don't think any of us know how to do that.

I'm getting the same error in what looks like a dump after a pretty bad failure on a new install of 8.04.  I'm trying to eliminate hardware sources of the problem by switching out devices one at a time; so far I haven't found a culprit.  the crash occurs (for me) during loading hardware drivers. I did notice earlier in the boot that ata2 port is slow to respond.  I've tried taking off the secondary IDE drives, but that hasn't worked.

Any thoughts?

---

### Post by Simon Bridge on 2008-04-28
> **gcranston said:**
> I don't think any of us know how to do that.Sad - you add the command to the kernel line in menu.lst

---

### Post by gcranston on 2008-04-29
nope, still get the same crash.  I've changed some ofthe hardware in this machine since the last known good configuration.  I'm going to try going all the way back then testing the newhardware one by one to find the culprit.  I'll post what I find then.

---

### Post by gcranston on 2008-04-29
apparently it was the nVidia PCI video card that was causing problems.  Maybe I don't have the BIOS set right.

---

