---
title: "ATI  9250 Grpahics Card."
date: 2008-12-03
forum: General Help
---

### Post by Grolsche on 2008-12-03
Hi,

I have an ATI Radeon graphics Card. I am new to ubuntu and linux. I went to ati website and found the driver i needed. when i read  the installation notes it says I need the following:

> Before attempting to install the ATI Proprietary Linux driver, the following software must be installed:

    * POSIX Shared Memory (/dev/shm) support is required for 3D apps
    * glibc version 2.2 or 2.3
    * Linux kernel 2.4 or higher
    * XOrg 6.7,6.8,6.9,7.0 or 7.1; XFree86 version 4.3 

I did try to search  for these but got lost in lots of wikis and stuff. Can anyone tell me if ubuntu 8.10 already has these installed as standard?

Also would be good if I knew how I could tell what is installed for future installations, such as a command you can type or a gui  thats avaliable. If these are not already installed, where do i get them from etc..

---

### Post by kevinlw on 2009-01-05
> **Grolsche said:**
> Hi,

I have an ATI Radeon graphics Card. I am new to ubuntu and linux. I went to ati website and found the driver i needed. when i read  the installation notes it says I need the following:



I did try to search  for these but got lost in lots of wikis and stuff. Can anyone tell me if ubuntu 8.10 already has these installed as standard?

Also would be good if I knew how I could tell what is installed for future installations, such as a command you can type or a gui  thats avaliable. If these are not already installed, where do i get them from etc..

I have the same card, have installed Intrepid 8.10 and Blender. Card doesn't work well with Blender, screen keeps flashing on and off.  Anyone hit this before?  Other 8.10 programs seems compatible with card.  XP + Blender works well on the same machine & card. I'm dual-booting from the same machine.  Hardware is AMD Sempron 1.8Ghz, 2.5GB RAM, 80GB HDD, MSI KT880 mobo, ATI 9250 card driving a Samsung 17" LCD

---

### Post by tuxxy on 2009-01-05
It will be ATI drivers at fault, best thing you could do is switch to nvidia for your multimedia needs.

---

### Post by kevinlw on 2009-01-05
> **tuxxy said:**
> It will be ATI drivers at fault, best thing you could do is switch to nvidia for your multimedia needs.

Thanks for your reply but not much help bro.  AGP cards are on their way out here in Malaysia so looking for nvidia AGPs is a very expensive and time consuming affair.  Besides, I'm recycling what I have. If I have to replace each hardware that doesn't run well with ALL linux programs, might as well quit using Linux and stay with Mr. Gates!:-(](*,)

---

### Post by ffxigotenks on 2009-01-05
the installation notes you quoted are more physical requirements than software requirements. As far as I can tell they are present in every ATI card or computer so it shouldn't be an issue, I would just make sure you have the kernel source package installed, I forget exactly what it's called but I think it's something close to "kernel-source"  or "kernel-dev" so that when you run the ATI driver install it will work with your system

---

### Post by kevinlw on 2009-01-05
> **ffxigotenks said:**
> the installation notes you quoted are more physical requirements than software requirements. As far as I can tell they are present in every ATI card or computer so it shouldn't be an issue, I would just make sure you have the kernel source package installed, I forget exactly what it's called but I think it's something close to "kernel-source"  or "kernel-dev" so that when you run the ATI driver install it will work with your system

So how do I go about checking for the kernel?  Last time I ran Ubuntu's update, I had to leave my PC running for two days straight!  Downloaded close to 400 individual updates! 8-(

Regards,

---

### Post by kevinlw on 2009-01-05
*deleted*

---

### Post by kevinlw on 2009-01-05
*deleted*

---

### Post by ffxigotenks on 2009-01-05
> **kevinlw said:**
> So how do I go about checking for the kernel?  Last time I ran Ubuntu's update, I had to leave my PC running for two days straight!  Downloaded close to 400 individual updates! 8-(

Regards,

try typing in a terminal

```
sudo apt-get install linux-headers-$(uname -r)
```
that should get you what you need, then just follow the instructions on the ATI site

---

### Post by zika on 2009-01-08
> **Grolsche said:**
> Hi,

I have an ATI Radeon graphics Card. I am new to ubuntu and linux. I went to ati website and found the driver i needed. when i read  the installation notes it says I need the following:



I did try to search  for these but got lost in lots of wikis and stuff. Can anyone tell me if ubuntu 8.10 already has these installed as standard?

Also would be good if I knew how I could tell what is installed for future installations, such as a command you can type or a gui  thats avaliable. If these are not already installed, where do i get them from etc..

are You still interested in answers to these questions?

---

