---
title: "Ubuntu 10.04 running slow after standby/resume"
date: 2010-08-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cdavid1013 on 2010-08-25
Ubuntu 10.04 (all applications) freeze/run very slowly after standby/resume. Reboot resolves. Ideas?

---

### Post by ghostborg on 2010-08-25
I don't have the answer but I think you need to provide hardware details like motherboard, graphics or computer model number .

I found that Ubuntu boots so fast that if I have a problem with standby/resume I just opt to shutdown until you figure out the problem.

Good Luck.

---

### Post by De Smid on 2010-09-04
I got the same problem since i upgrade tot Ubuntu 10.04. My desktop is a Acer Aspire T151, AMD Athlon 64 3200+ op 2,0 GHz, nVidia nForce 4 chipset met onboard  audio and ATI RV370 [Sapphire X550 Silent] graphic card.

---

### Post by j_freshman on 2010-09-05
I would like to have an answer to this too. It happened to me today while I was working on a Dimension 4550 running Lucid that my cousin uses as a home server.

Dimension 4550, 256MB RAM (low usage server..), 2GHz P4, Intel 845PE chip set

[full list of factory specs]("http://support.dell.com/support/edocs/systems/dim4550/specs.htm")

---

### Post by DjSesso on 2010-09-05
> **j_freshman said:**
> I would like to have an answer to this too. It happened to me today while I was working on a Dimension 4550 running Lucid that my cousin uses as a home server.

Dimension 4550, 256MB RAM (low usage server..), 2GHz P4, Intel 845PE chip set

[full list of factory specs]("http://support.dell.com/support/edocs/systems/dim4550/specs.htm")


I think it has something to do with after it suspends to ram and you come back from standby it doesn't free the ram after. Mine starts slow when coming back on but is fine after 10 secs.

Ya I have 792M left out of 4 G and it should be at least 2G free

---

### Post by cdavid1013 on 2010-09-23
Hi all, sorry I didn't put up specs. Latitude Dimension D830, 4GB, 250GB, 2.40Ghz Intel Core 2 Duo. I'm not...terribly sure as to what motherboard I'm running. I can look into it. However, regarding memory not freeing up, I'm using 9.8% of system memory after resume, but it's still running very, very slowly. I'll continue to provide information as I can

---

### Post by alecz20 on 2010-10-07
I am affected as well by this problem since quite some time.

My system is a Intel i5, 4 GB RAM, ASUS P7P55-M Motherboard, ATI Radeon HD 5770 (proprietary driver), Ubuntu 9.10 64-bit.

You may also want to check out these two bugs:

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/236275](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/236275)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/400413](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/400413)

---

### Post by Flames on 2010-10-13
On lucid I couldn't resume at all (I'd get a black screen).
Now it mainly works on maverick (Except for slowness for a few seconds). 

I'm running Nvidia for video and the drivers seemed to be messed up after resuming.
I seem to have fixed this by uninstalling them, restarting, installing, restarting.



My only complaint now is that specifically google chrome (or chromium)
will run very slowly after resuming. 
Firefox is unaffected.

---

### Post by waperboy on 2010-11-04
Have similar problem too after resume: Mouse cursor still visible when rotating desktop with compiz fusion, system freezes for many seconds when switching to/from opengl applications (starting glxgears for example).

Stopping and then starting gdm resolves the problem.

---

