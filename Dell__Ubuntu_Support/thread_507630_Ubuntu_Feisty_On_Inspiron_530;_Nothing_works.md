---
title: "Ubuntu Feisty On Inspiron 530; Nothing works"
date: 2007-07-23
forum: Dell  Ubuntu Support
---

### Post by Phalangees on 2007-07-23
I got an Inspiron 530 that came preloaded with vista. I shrunk vista's partition and made room for ubuntu. I installed ubuntu feisty fawn on the partition that I opened up and it went very well. After the install I rebooted my computer and ubuntu booted up since it was the first option in GRUB. When it booted, I had no network connection so I decided to check if it recognized everything besides that. The only things ubuntu had recognized and were working properly was the SATA hard drive, the video card (partially, needs nvidia drivers still), my modem, and the USB.

I've reinstalled ubuntu and it still doesn't work. Even on the live CD I only get those devices.

Does anyone have any idea on how to fix this without manually installing a driver for everything?

Thanks for any and all help you can offer.

---

### Post by Ek0nomik on 2007-07-23
> **Phalangees said:**
> I got an Inspiron 530 that came preloaded with vista. I shrunk vista's partition and made room for ubuntu. I installed ubuntu feisty fawn on the partition that I opened up and it went very well. After the install I rebooted my computer and ubuntu booted up since it was the first option in GRUB. When it booted, I had no network connection so I decided to check if it recognized everything besides that. The only things ubuntu had recognized and were working properly was the SATA hard drive, the video card (partially, needs nvidia drivers still), my modem, and the USB.

I've reinstalled ubuntu and it still doesn't work. Even on the live CD I only get those three devices.

Does anyone have any idea on how to fix this without manually installing a driver for everything?

Thanks for any and all help you can offer.

You are looking to get your Internet and sound card working I take it?

Are you trying to get wireless or corded Internet to work?

What kind of sound card do you have?

If you don't know, you can have the shell spit it out for you.  (Start/Accessories/Terminal)

```
lspci
```

Paste your output in a reply.

---

### Post by subaru on 2007-07-23
ubuntu device support is somewhat limited, if you want almost all of your devices recognised right out of the box . . try Sabayon linux. . .

---

### Post by Ek0nomik on 2007-07-23
> **subaru said:**
> ubuntu device support is somewhat limited, if you want almost all of your devices recognised right out of the box . . try Sabayon linux. . .

Just because it doesn't work out of the box doesn't mean that he or she can't use it with Ubuntu.

---

### Post by octocore on 2007-07-23
having the same problem w/ my inspiron 530.

my network card is intel(r) 82562v-2 10/100 network connection (integrated)
display adapter: intel(r) g33/g31 express chipset family (integrated)

any help would be great.

---

### Post by Phalangees on 2007-07-23
It's not just my network (wired, integrated) and my sound card (integrated 5.1), but under the devices, there is seriously twice as much unknown hardware as there is recognized hardware. I really don't want to have to configure everything manually.

If I wait say a month or so, and redownload Feisty, would it still be the same or are the downloads updated?

I'm thinking that some of this hardware is just too new. I love ubuntu though. I'll save it's 100 gb partition. I was using ubuntu (dapper) on my old computer actually and I upgraded computers and I thought I'd make a dual boot.

Any ideas?

Thanks for your help.

---

### Post by Ek0nomik on 2007-07-25
> **Phalangees said:**
> It's not just my network (wired, integrated) and my sound card (integrated 5.1), but under the devices, there is seriously twice as much unknown hardware as there is recognized hardware. I really don't want to have to configure everything manually.

If I wait say a month or so, and redownload Feisty, would it still be the same or are the downloads updated?

I'm thinking that some of this hardware is just too new. I love ubuntu though. I'll save it's 100 gb partition. I was using ubuntu (dapper) on my old computer actually and I upgraded computers and I thought I'd make a dual boot.

Any ideas?

Thanks for your help.

So you were using Dapper and your hardware was being recognized, and now it isn't?

I don't think it is a matter of new hardware, at least not entirely.  I have three computers, each is under 3 years old.  In fact, my laptop is only a few months old and 7.04 installed great with the Alternate CD.

Installing Feisty later down the road probably won't solve your problem, at least not if you don't have an Internet connection working.  The hardware will be detected by the Kernel.  As with most distributions, when a new version is released, it includes the newest kernel at the time of release.  However, there have already been kernel updates since the release of Feisty.

---

### Post by Orion2000za on 2007-07-25
I am yet to understand (have not searched for the answer admittedly) why the downloads of Live/Alternate CD/DVDs are not updated when a new kernel or such packages are introduced? 

then it would make sense to upgrade your installCD now and then. Now you know that if you have to reinstall or install a new PC you are looking at hours and hours of downloads post-install.

Sinclair :confused:

---

### Post by Phalangees on 2007-07-25
Ek0nomic - I had Dapper on a much much older computer and I just got a new computer and installed Feisty Fawn. I can't update it without a network stuff but I'm going to try popping in an older net card, update my Kernel and try to see if that'll work out. Thanks for your help.

EDIT/UPDATE: It didn't work. I updated the Kernel and gave myself a scare because Vista disappeared off of grub but I got it back. The only way I'm able to get a net connection is by using an old net card which is crap. :/  I'll update it again in a month or so and hopefully then I'll have better luck. Thanks again for the help.

---

### Post by Ek0nomik on 2007-07-25
> **Phalangees said:**
> Ek0nomic - I had Dapper on a much much older computer and I just got a new computer and installed Feisty Fawn. I can't update it without a network stuff but I'm going to try popping in an older net card, update my Kernel and try to see if that'll work out. Thanks for your help.

EDIT/UPDATE: It didn't work. I updated the Kernel and gave myself a scare because Vista disappeared off of grub but I got it back. The only way I'm able to get a net connection is by using an old net card which is crap. :/  I'll update it again in a month or so and hopefully then I'll have better luck. Thanks again for the help.

While I am not an expert on the topic, you still never mentioned what type of network card wasn't working.  I'd like to at least search and see if I can find any discussions on the matter so you can get a little more information about it, or even a fix.

---

### Post by rrmoulton on 2007-07-26
> **Phalangees said:**
> I got an Inspiron 530 that came preloaded with vista. I shrunk vista's partition and made room for ubuntu. I installed ubuntu feisty fawn on the partition that I opened up and it went very well. After the install I rebooted my computer and ubuntu booted up since it was the first option in GRUB. When it booted, I had no network connection so I decided to check if it recognized everything besides that. The only things ubuntu had recognized and were working properly was the SATA hard drive, the video card (partially, needs nvidia drivers still), my modem, and the USB.

I've reinstalled ubuntu and it still doesn't work. Even on the live CD I only get those devices.

Does anyone have any idea on how to fix this without manually installing a driver for everything?

Thanks for any and all help you can offer.
I had the same problem with the 530 is just got a couple days ago with Feisty preloaded.  Was referred to Dell Linux support and got awsome help from a really sharp guy.  He emailed me the NIC drivers and instructions.  Email me at my gmail account (rrmoulton) and I will forward them to you.

---

### Post by Ek0nomik on 2007-07-26
> **rrmoulton said:**
> I had the same problem with the 530 is just got a couple days ago with Feisty preloaded.  Was referred to Dell Linux support and got awsome help from a really sharp guy.  He emailed me the NIC drivers and instructions.  Email me at my gmail account (rrmoulton) and I will forward them to you.

Why not post the e-mail content on the forum so everyone can benefit now and in the future?

---

### Post by rrmoulton on 2007-07-26
OK.

This is from the email from Dell support.  Attached is the driver.

Code:
[B]tar xfvz e1000-7.6.5.tar.gz
cd e1000-7.6.5/src
sudo make install
sudo modprobe e1000[/B]

OK, your Ubuntu will try to obtain an IP address automatically now. If not, you might want to edit /etc/network/interfaces to configure it manually, 

[I](I did it in System / Administration / Network)
[/I]
then run this command:

Code:
[B]sudo /etc/init.d/network restart 
[/B]
If it still not work, reboot your Ubuntu.

My NIC came right up.

Let us know how it worked.

Good Luck.

---

### Post by Phalangees on 2007-07-27
It's an integrated ethernet port. I'll try to find some information on it. It's an "Intel(R) 82562V-2 10/100 Network Connection."

EDIT: Didn't see the post above me. :P

Thanks for the update. I'll see if I can get it working.

---

### Post by afx114 on 2007-08-02
Hi, I am trying to install this Network Driver using the instructions given above, but receive the following:

```

Makefile:71: *** Linux kernel source not found.  Stop.

```

This is on an Ubuntu Server 7.04 install.  Where should I get and put the linux kernel source so that this driver can compile?  Can I copy it directly off the install CD?

---

### Post by afx114 on 2007-08-02
Nevermind, I've figured it out.  I had to install linux-headers as well as GCC in order to compile the driver:

```

apt-get install linux-headers-2.6.20-15-server
apt-get install gcc

```

---

