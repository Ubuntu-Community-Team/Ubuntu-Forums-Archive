---
title: "install Gigabyte GeForce RTX 2060"
date: 2019-11-12
forum: Gaming &amp; Leisure
---

### Post by call-922 on 2019-11-12
All: I have a Ubuntu 18.04.3 LTS system that I bought with an integrated Intel display. I'm up to date with all updates. I bought an RTX 2060 GPU which I now am getting ready to install. I have never installed something on Linux which requires a new driver. I've read through all the instructions and I'm  ready to start the install.

My question is: Is there a recommended way to "snapshot" the OS so that - if the install goes bad - I can boot and easily roll back to pre-install state? Windows has the notion of a "savepoint". Is there an analogous concept in Ubuntu? (Note - I've already backed up everything.)

Thanks

---

### Post by mastablasta on 2019-11-13
> **call-922 said:**
> 
My question is: Is there a recommended way to "snapshot" the OS so that - if the install goes bad - I can boot and easily roll back to pre-install state? Windows has the notion of a "savepoint". Is there an analogous concept in Ubuntu? (Note - I've already backed up everything.)

Thanks

linux is modular OS and there are some applications that will make that. 

if you used advanced file system like BTRFS or ZFS4Linux, then this feature is actually built in.

you already have it backed up, but there is also the option of making a clone (using clonezilla for example)

---

### Post by oldrocker99 on 2019-11-13
You have an ATI card. Superb drivers are already part of the system. In the old days, nVidia was the choice with their closed-source drivers, which beat the open-source Noveau drivers for NVIDIA all hollow.

Back in the day, ATI's closed-source drivers for Linux were horrible, and would not work with "legacy" cards, like the Toshiba laptop I acquired in 2009, whose card was legacy when I bought it. So, a team of open-source developers started working on a free Radeon driver.

To their great credit, ATI worked with the devs, giving every detail of the hardware to them, and the open source, built-in drivers are excellent, just like Intel's open source drivers. Of course, ATI far outperforms Intel. The new Ryzen APUs have a Vega GPU built-in and can be used as a low-budget gaming machine, as long as you don't strain the GPU/

I have a nVidia 960, and my next card will absolutely be ATI.

---

### Post by mastablasta on 2019-11-14
also ATI has been AMD for a while now.

user might need AMDGPU-pro which is their closed source part used for gaming. however, we can hope that like before they will either help the developers with the opensource driver or open the closed part once the GPU is not commercially relevant anymore.

---

### Post by CatKiller on 2019-11-14
You both seem to be confused. The RTX 2060 is most definitely an Nvidia card.

For the OP: you may find it useful to have an Ubuntu live USB handy. One of the prominent side effects if things were to go a bit sideways when changing graphics drivers is that you might end up without a graphical environment. This can be somewhat intimidating for the inexperienced user. By booting from the live USB you can have the support structure of that environment (and a web browser) while you fix it rather than having to do so from the command line.

Support for the Turing line as a whole came with the 410 branch, but I don't know that the 2060 was specifically included with that version. That means that for 18.04 you're going to need either the updates repository or the graphics drivers PPA to get a driver that's new enough. The 440 branch recently took over as the "long lived" branch from the 430 branch, but the version in the PPA - 440.26 - is still the beta version. 440.31 is the stable one, but it isn't in there yet. The 435 branch is the "short lived" one.

---

### Post by mastablasta on 2019-11-15
> **CatKiller said:**
> You both seem to be confused. The RTX 2060 is most definitely an Nvidia card.



duh. of course. ](*,)[CENTER][COLOR=#000000]
[/COLOR][/CENTER]

---

### Post by yaminb on 2019-12-02
If it helps, I've got the same card. I was running 18.(something), but now I'm on 19.10.
The card works perfectly.

I've found the 4.35 drivers work best.
4.40 I've had some issues with.

I don't really think you need a snapshot to install the driver. Just install the driver. If you need  help, let me know.

The one thing you should probably stay aware of is to know how to get to the shell if you can't login via the GUI.
I had this one issue where the driver installs, it gets to the GUI login, but when I login, it just black screens and goes back to the login.

I believe it is ctrl-alt-f2. So you can have a terminal where you can type commands in again.

---

