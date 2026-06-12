---
title: "WiFi LED does not work but WiFi does"
date: 2008-10-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by riahc3 on 2008-10-02
I have a small issue that my WiFi LED does not work but WiFi does I know this issue exists and there is a fix [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work) but I have a different kernel and it tells me that my version is not found. How can i fix it?

---

### Post by riahc3 on 2008-10-06
Bumping up.

---

### Post by me_ben on 2008-10-06
i do not think that it is problem involved with Ubuntu or any other OS When your wifi is working ok then it is just a hardware problem

---

### Post by Teamgeist on 2008-10-06
You will have to install the linux-backports-modules-2.6.24-19-generic package.

In a Terminal type ```
sudo apt-get install linux-backports-modules-2.6.24-19-generic
```

or just search for it in the Synaptic Package Manager.

---

### Post by anjilslaire on 2008-10-06
Agreed. Just alter the command to mimic whatever kernel version you have.

---

### Post by riahc3 on 2008-10-06
You didnt even read the first post did you?

I already tried changing my kernel version but it says its not found

---

### Post by anjilslaire on 2008-10-06
Yes, I did.
> 
I have a small issue that my WiFi LED does not work but WiFi does I know this issue exists and there is a fix [http://linux.dell.com/wiki/index.php..._does_not_work](http://linux.dell.com/wiki/index.php..._does_not_work) but **I have a different kernel and it tells me that my version is not found**. How can i fix it?


Your post implied that you copied and pasted the command staight from the wiki, which would not work if you don't have kernel 2.6.24-16-generic. It appears you didn't read what you wrote, and are being a bit rude about it.

If you would provide more details such as which kernel you do have, we can give you more help on how to fix it.

---

### Post by Teamgeist on 2008-10-07
```
sudo apt-get install linux-backports-modules-hardy-generic
```
This will install the correct version for your kernel.

---

### Post by riahc3 on 2008-10-10
> **anjilslaire said:**
> Yes, I did.


Your post implied that you copied and pasted the command staight from the wiki, which would not work if you don't have kernel 2.6.24-16-generic. It appears you didn't read what you wrote, and are being a bit rude about it.

If you would provide more details such as which kernel you do have, we can give you more help on how to fix it.

I think 26-19 generic or 24-19 generic. I tried my version and it said it was not found.

---

### Post by Hyper Tails on 2008-10-10
same here

my laptop is an acer apsire 5715-4740 and it runs ubuntu 8.04 LTS and the wireless works but not the leds

i'l try that command on it now

---

### Post by sbrbot on 2008-10-11
You have to install:

--> [Compat Wireless](http://linuxwireless.org/en/users/Download)

If you have original Ubuntu 8.04 (kernel 2.6.24-something) then you have to compile and install:

--> [compat-wireless-old.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2)

It's easy, you have all instructions on this site. This upgrades wireless card components and adds led_class module for controlling WiFi LED.

---

### Post by bolex100 on 2008-10-11
I have the same problem.  I have an off-the-shelf Dell 1525 laptop, and I needed to completely reinstall the o/s.  I thought that the included CD ROM had all the factory settings, but no....:(

My kernel is 2.6.24.19  The command doesn't cause any error messages.  It just doesn't make the LED work. 
I don't know about this Compat wireless site.  The instructions look complicated. I don't like messing with .tar files unless I know what I'm doing ..... and how to undo it!  Is there another way?

---

### Post by jespdj on 2008-10-11
I'm not sure, but if it can be solved by installing something from backports, then it's probably a problem that has been solved in a future version - it will probably be fixed in Intrepid. It's just a few weeks until Intrepid is released, so you could just wait and upgrade when it comes out.

The WiFi LED also doesn't work in Ubuntu 8.04 on my XPS M1530. (It does work in Windows Vista). I don't worry about it, and it's certainly not a problem that I would want to risk messing with my kernel or WiFi drivers for - it's more important that my computer and WiFi work smoothly than that a stupid little LED doesn't work.

---

### Post by riahc3 on 2008-10-12
> **sbrbot said:**
> You have to install:

--> [Compat Wireless](http://linuxwireless.org/en/users/Download)

If you have original Ubuntu 8.04 (kernel 2.6.24-something) then you have to compile and install:

--> [compat-wireless-old.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2)

It's easy, you have all instructions on this site. This upgrades wireless card components and adds led_class module for controlling WiFi LED.

Im on 2.6.24-19-generic. Ubuntu 8.04.1

> **bolex100 said:**
> I have the same problem.  I have an off-the-shelf Dell 1525 laptop, and I needed to completely reinstall the o/s.  I thought that the included CD ROM had all the factory settings, but no....:(

My kernel is 2.6.24.19  The command doesn't cause any error messages.  It just doesn't make the LED work. 
I don't know about this Compat wireless site.  The instructions look complicated. I don't like messing with .tar files unless I know what I'm doing ..... and how to undo it!  Is there another way?

Im gonna try it out and Ill reply :)

> **jespdj said:**
> I'm not sure, but if it can be solved by installing something from backports, then it's probably a problem that has been solved in a future version - it will probably be fixed in Intrepid. It's just a few weeks until Intrepid is released, so you could just wait and upgrade when it comes out.

The WiFi LED also doesn't work in Ubuntu 8.04 on my XPS M1530. (It does work in Windows Vista). I don't worry about it, and it's certainly not a problem that I would want to risk messing with my kernel or WiFi drivers for - it's more important that my computer and WiFi work smoothly than that a stupid little LED doesn't work.

Might be a "stupid little LED" for you but I find it alot more stupid that my Vostro cost less than your XPS yet it has the same (or better) features.

---

### Post by riahc3 on 2008-10-12
Im compling and installing compat-wireless-old.tar.bz2 Right?

Lets see how this goes.

(On a side note, Ubunutu is VERY slow today...)

---

### Post by riahc3 on 2008-10-17
Bumped as I still havent been able to fix this.

---

### Post by smooth3006 on 2008-10-20
> **riahc3 said:**
> Bumped as I still havent been able to fix this.

my hp dv6809 led wont work either along with the wireless kill switch. i do have wifi working though, i heard intrepid 8.10 will fix this issue so you will have to wait.

---

### Post by flakrat on 2008-10-23
Try this:

sudo apt-get install linux-backports-modules-hardy

Without any 'generic' or kernel versions. that worked on my m1330, although after 30 minutes with that wifi light blinking at me, I'm about to disable it :-)

---

### Post by riahc3 on 2008-10-23
> **smooth3006 said:**
> my hp dv6809 led wont work either along with the wireless kill switch. i do have wifi working though, i heard intrepid 8.10 will fix this issue so you will have to wait.

The "wireless kill switch" is the one that switches WiFi on/off? It doesnt depend on the OS; It depends on the BIOS.

> **flakrat said:**
> Try this:

sudo apt-get install linux-backports-modules-hardy

Without any 'generic' or kernel versions. that worked on my m1330, although after 30 minutes with that wifi light blinking at me, I'm about to disable it :-)

And how/can do you disable it?

---

### Post by jsschreck on 2008-10-30
I have a Dell 1525 Inspiron, and the fix given on the Dell wiki (and also posted here multiple times) worked for me in 8.04. However, after upgrading to 8.10 (and having an up to date kernel), the light will stay constant for about 10-15 seconds, and then it will flicker for about the same time. When I was running 8.04, the light remained constant, which was not annoying, unlike now....

Any ideas about this?

---

### Post by riahc3 on 2008-10-30
In 8.10 this has been fixed but the blinking can get annoying; If it blinked data rate (slower=slower data rate, faster=faster data rate) then it would be great. But it just blinks with activity.

Anywayt to disable this?

---

### Post by eyime on 2009-01-02
Hi,

this hack works for me,

> sudo apt-get install linux-backports-modules-hardy-generic

thanks a lot for you guys.

I have also a suggestion:

why don't use a DELL repository for automatically use/update this hack and others ?.

The main idea is that people like me (who purchase a DELL XPS with Ubuntu installed and are new to Linux) can enjoy a better user-experience with Ubuntu because the bugs are solved automatically.

Thanks.

---

### Post by AmyRose on 2009-01-03
If you have to reinstall your factory-installed Ubuntu, don't they have factory install ISOs on their site? [http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO)

And another way to reinstall:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/OS_Reinstallation](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/OS_Reinstallation)

> **riahc3 said:**
> In 8.10 this has been fixed but the blinking can get annoying; If it blinked data rate (slower=slower data rate, faster=faster data rate) then it would be great. But it just blinks with activity.

Anywayt to disable this?Yeah, I'd like to know if there's a way to disable it too. It's kinda distracting since it's blinking almost all the time I'm on-line (which, at home, is nearly the whole time I have the machine running) and never stops.

---

### Post by Kareeser on 2009-01-03
Problem also exists on the Dell Inspiron 700m.

However, this laptop came around before Dell signed on with Ubuntu, so it's no wonder that it doesn't work. No official support from Dell either :)

Installing linux-backports-modules-intrepid-generic causes Wireless to cease functioning. That is, wireless network can be detected, but I cannot connect or browse.

Unfortunate :)

---

### Post by Lockheed on 2009-08-30
There is this command that supposed to work:
```
sudo apt-get install linux-backports-modules-2.6.24-19-generic
```
But what if I upgraded karnel on my Jaunty 9.04 x64 to 2.6.30.1 and added custom name to it, which is 2.6.30.1-azure? 
How do I now install backports?

---

### Post by Lockheed on 2009-09-10
bump...

---

### Post by Lockheed on 2009-09-20
hump

---

