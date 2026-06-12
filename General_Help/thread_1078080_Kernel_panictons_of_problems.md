---
title: "Kernel panic/tons of problems"
date: 2009-02-22
forum: General Help
---

### Post by jdmnynja on 2009-02-22
Hello all,

So my Ubuntu experience so far has been horrible. I have been trying all week to get 8.10 to work, 64 bit and now 32 bit. Mainly my issues have been constant freeze's from the desktop after logging in. I finally got 32 bit installed tonight, but after I began running the updates, it froze and after my manual reboot (from the CPU button) it tries to start up and tells me 
[  0.692102] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I was getting desktop freezes before this, so I swapped out my nVidia GeForce FX 5200 for a spare card I had laying around. I thought it was hardware at first, but I really have no idea. I'm pretty sure that everything that can go bad, has gone bad. I am going to reinstall Ubuntu 32 bit and go from there. But I am exhausted from trying to get it to work. Any help is appreciated.

I am running the following specs..
AMD Athalon 64bit
1gb RAM
AMD K8-800T motherboard
ATI Rage 128MB
80GB HDD IDE

---

### Post by kattman on 2009-02-23
Try running memtest86

---

### Post by sahabcse on 2009-02-23
Hi

Try the following for solving kernel-panic error.

================================================
[http://sahabm.blogspot.com/2009/02/kernel-panic-not-syncing-ubuntu-810.html](http://sahabm.blogspot.com/2009/02/kernel-panic-not-syncing-ubuntu-810.html)
================================================

Regards,
Sahab

---

### Post by jdmnynja on 2009-02-23
I followed the directions on the link given and I have now gotten past the start-up screen, but now I am dealing with continuous lock-ups and freezing after logging in.

---

### Post by sahabcse on 2009-02-23
Try to find which process taking more memory utilization..........

---

### Post by jdmnynja on 2009-02-24
It doesn't give me that opportunity, it freezes immediately after log in. I've tried openSUSE and it does the same thing there.

---

### Post by halok on 2009-02-24
As has been previously suggested try running memtest86 it sounds like you possibly have some faulty RAM.

---

### Post by jdmnynja on 2009-02-24
testing memory now. :guitar:

Just to update, everything is fine with the kernel panic. That is over. Now my major problem is consistent freezing and lock-ups. It usually happens immediately after I login and shortly after the opening music plays. It gives me no time to check anything and it is a complete lock up, I have to reboot from the button on my CPU. I have swapped out an old video card, and I am now convinced it is not graphics. I am running memtest86 to see how my RAM is.

---

### Post by halok on 2009-02-24
i suggest letting it do at least 5 passes somtimes these errors dont show up till things get a bit warm. I've had ram that didn't show as faulty for a few hours in memtest. Somtimes with really intermittent problems i leave the machine running overnight.

---

### Post by jdmnynja on 2009-02-24
So you suggest I run memtest 5 times?

---

### Post by jdmnynja on 2009-02-24
After 3 passes, it has brought back no errors. It is still running, but I'm starting to think it isn't my RAM...

---

### Post by jdmnynja on 2009-02-25
I let memtest86 run over night, made 18 passes. No error with my RAM. I checked the md5sum of the download and of the CD, both checked out okay. I'm using a Rage Pro 128 graphics card, I don't think it is the problem though. Anymore ideas on how to fix this problem?

---

### Post by jdmnynja on 2009-02-25
Trying a lighter desktop environment with Xubuntu, but it still freezes. It froze in the installation, it froze after I installed it during updates, but it runs fine from the CD. I've ruled out RAM, cannot be BIOS since this happens after I log in, the only thing I can think of would be graphics. Somebody out there has to have some ideas on how to fix this. I have been unable to do anything with Linux for 2 weeks now trying to install and run the different versions.:mad:

---

