---
title: "How do I Reinstall?"
date: 2007-09-02
forum: Desktop Effects &amp; Customization
---

### Post by kwandar on 2007-09-02
Installed Ubuntu 7.04 and somehow I screwed up with the new Nvidia drivers (It seems I have a version after the version in the kernel? ).  I wanted to get the Nvidia restricted drivers in, so I could use Beryl.

In any event, I don't seem to be able to fix xorg.config, its been a day of trying things, its 1AM and my brain has shut down.  Please for the love of god - help?!

I don't have much installed, so I don't care if I do a full install, reinstall whatever, but I don't know how to do any of that, and the command line stuff is killing me :(

Suggestion, help?  Please end the suffering :)

---

### Post by PurposeOfReason on 2007-09-02
Try, in recovery mode:
```
 sudo dpkg-reconfigure xserver-xorg
```

And select vesa for your video driver. Then enable restricted drivers upon restart. 

If you do want to reinstall, just pop in the live CD and override your current Ubuntu partition.

---

### Post by kwandar on 2007-09-02
Thank you!!

I'll give that at try - I hadn't selected VESA driver.

But .... with respect to reinstall, I couldn't figure out how to reformat the Linux partition only (it has MS on it too).

Again - thank you, thank you!!  I hope this works!

---

### Post by kwandar on 2007-09-02
Okay, that unfortunately didn't work.  Last night in desperation I "tried" to erase the partition with Grub, didn't think I actually had, but now have a ton of disk errors.  So .... some erased, some didn't.

How exactly do I get the Ubuntu utility for Grub from the Live disk to set a partition as / (root)?  It says I have to do that, but I don't see how to do that.

Ond further question - why did Ubuntu install two versions?  a .16 and a .15 I think?

Thank you!

---

### Post by Blamdarot on 2007-09-15
I'm having this same problem.

I'm brand new to Linux and Ubuntu. I installed it on a clean HDD last night, spent all day today trying to get it to run World of Warcraft. At one point, I could run WoW but after a few minutes of being in-game, it would freeze the whole system and eventually (after 5-10 minutes) WoW would crash.

Then a Linux friend of mine asked if I had updated my NVIDIA drivers. I hadn't, so he helped me get that done.

Now, my computer won't boot into the xserver unless I re-install the NVIDIA drivers (sudo sh <path to file downloaded for Linux from NVIDIA website>. Usually I have to run this twice before it will launch the xserver.

I'm going to try the steps mentioned above by "PurposeOfReason". I hope have better luck than "kwandar".

Thanks to anyone that offers me any other suggestions or helps me reinstall Ubuntu.

EDIT: I ran the " sudo dpkg-reconfigure xserver-xorg" command and it solved my problem of having to reinstall drivers on every boot. I then enabled the Restricted Drivers and my problem returned.

---

