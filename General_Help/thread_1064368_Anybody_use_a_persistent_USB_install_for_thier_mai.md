---
title: "Anybody use a persistent USB install for thier main/only Linux system?"
date: 2009-02-08
forum: General Help
---

### Post by Rubicon421 on 2009-02-08
I would like to have a persistent install on a 8GB usb drive as my main linux install so I can take it with me at any time and have all the changes, updates, apps, etc... on the go. 

I have gotten a persistent install of 8.10 to work a few times but it always fails to update and quits booting after that. 

If you have a persistent install that you use regularly-

1. What distro do you use?
2. What method did you use to create the bootable USB disc?
3. Have you been able to add apps and get updates for the distro and apps?
4. What size/brand USB drive do you have?
5. How stable/reliable is it compared to a regular HD install? 
6. How long have you had it running without error?

Sorry about all the questions, but hey- that's what this place it for. It's one of the reasons Ubuntu is so awesome!

---

### Post by grndslm on 2009-02-08
No

---

### Post by niteshifter on 2009-02-08
Hi,

I use Heron-an-a-stick ;) regularly - an installation of 8.04.1 on a SanDisk 2GB Cruzer for use with on my work laptop. 

Pitfalls encountered:
The Cruzer was a U3 device. Had to de-U3 it with SanDisk's tool (requires a Windows machine).

Persistence was broken "out-of-the-box" (known issue, with fixes available).

Does not shutdown the file system cleanly. No breakage or corruption, just an unclean shutdown. I fsck the casper-rw partition on it when I connect it to my Ubuntu laptop, otherwise bootup gets slower.
==

It boots and works faster than CD, but still nowhere near as fast as an install to hard disk goes. I was able to install what software I needed, which wasn't much. Keep in mind that persistence has limits - the more files you modify out of the fixed set equals slower response and not everything is persistable (to coin a word).

My needs are different from what you stated. I just wanted to be able work on OOo docs, and have a means for keeping personal emails off the corporate radar (I use it with a 3G phone).

Keep in mind a persistent install has a very generic view of hardware, especially video. It's meant to be portable, so things like compiz aren't doable since the "advanced" (proprietary) drivers aren't available. Even should you manage to install NVidia, that's not going to work an a machine with ATI video, etc.

---

### Post by Rubicon421 on 2009-02-10
Would this be any easier to set up on an external HD? Would you still be able to make it persistent and bootable from different computers?

---

