---
title: "Vostro 1700 Audio Problem"
date: 2007-12-12
forum: Dell  Ubuntu Support
---

### Post by someone777 on 2007-12-12
Hi i am experiencing audio problem like most of the people in the forums. i have looked around the forums and tried all solutions to get the sound working and get the ubuntu find the driver, but no luck.i don;t know what to do anymore..:confused: some info i can tell you right now is that i can run three os(vista,xp,ubuntu) :lolflag: where vista and xp is having no problem, only ubuntu is. also when i load into different kernel, the sound is perfect and recognized the driver. both sigmatel and intel's. i would appreciat the help thks.

---

### Post by soapytheclown on 2007-12-21
hi did u figure this out yet its the only thing stopping me switching, otherwise im going to wait till 8.04

---

### Post by someone777 on 2007-12-21
yes i know what the problem it is
but i just can;t get the cd to work on the dell. ill just have to make the new one.
okay the kernel that my sound works was 7.04's and when i upgrade to 7.10. it doesn;t work, so i think the upgrading caused some kind of problem with the audio devices. you'll require a new or clean install of 7.10. i hope this works though

---

### Post by soapytheclown on 2007-12-21
ive been using a 7.10 live cd with the problems didnt get my laptop till after 7.10 was released so never tried it with 7.04 :(

---

### Post by chamakits on 2008-01-04
Well, i don't know if you still have the problem or not, but I had this same problem.
I found this on these forums:
[http://ubuntuforums.org/showthread.php?t=580645](http://ubuntuforums.org/showthread.php?t=580645)

The solution works, although the sound is sub-par, but it works.
If you found a better solution, let me know.

---

### Post by soapytheclown on 2008-02-03
just tested out ther latet hardy cd number 4 , and the sound works out of the box im so happy :) well the output did, input didnt, but atleast thats something less for us to worry about.. i didnt get the nvidia drivers installed with the new xorg yet though but this release hopwfully will makeubunt on our vostros perfecto!

---

### Post by adityakiran on 2008-02-04
I think the command

sudo aptitude install linux-backports-modules-generic

ought to solve the problem

---

### Post by StefAndrew on 2008-02-05
> **adityakiran said:**
> I think the command

sudo aptitude install linux-backports-modules-generic

ought to solve the problem

That would be my suggestion to try as well.  The backports module has always made my sound work on my Vostro 1500 with the same sound card.  An alternative to running from the command line is to search available packages via Add Programs or Synaptic and search for backports and you should find this package as well.

---

### Post by seaq on 2008-02-07
I made sometime ago a wikipage for vostro 1700.

I've solved the audio issue with the Dells' s conexant provided modules

[https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700](https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700)

---

### Post by pingnak on 2008-04-26
With Hardy/8.04, the 64 bit version worked out of the box, and the 32 bit version I had to install the 'linux-rt' package through Synaptic Package manager and boot that kernel, and it worked fine.

This is where the bug's being reported on Hardy, and where I found the fix.
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/211644](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/211644)

---

