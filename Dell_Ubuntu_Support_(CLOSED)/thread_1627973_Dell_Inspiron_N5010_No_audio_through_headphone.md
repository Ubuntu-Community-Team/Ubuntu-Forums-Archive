---
title: "Dell Inspiron N5010: No audio through headphone"
date: 2010-11-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by varunvs on 2010-11-22
I'm a new user to Ubuntu and I've a Dell Inspiron N5010 laptop. Well, I installed Ubuntu 10.10 and activated all device drivers (Broadcomm wireless, ATI graphics).

Now, the only problem I face is I do not get any audio out through headphone. I can hear audio through the built-in speakers but not through headphone!

I tried googling and found many suggestions. I don't know how it happened! One day, I can hear audio through headphone. Later again after two-three days, again no audio through headphone.

Now the present state is NO AUDIO THROUGH HEADPHONES. Else everything is fine. I updated everything. But still the issue persists.

Configuration:
Dell Inspiron N5010 (15R)
Intel Core i3 330M
4GiB RAM
320GB HDD
Chipset: Intel HM57

Audio Hardware:
Chipset: Intel 5 Series/34x0 Chipset PCH - High definition audio
High Definition Audio Codec: IDT 92HD81B1X

OS: Windows 7 x64 & Ubuntu 10.10 x64

---

### Post by stratosvoukel on 2010-12-04
I have the same problem, I also own a N5010 inspiron. The line out used to work but it suddendly stoped working, I even unistalled and nothing got fixed :S.

---

### Post by Firedragon1026 on 2011-02-17
I also have a brand new Dell Inspiron N5010 almost the exact same set up.  And the exact same problem.  

I've searched all over the forums and tried nearly every other solution to this problem and every other.  Still nothing fixes it.  Desperately need some help

---

### Post by safwankhan on 2011-02-26
I was having the same problem. However I recently managed to solve it by re-installing the latest version of Alsa-drivers. Here is what you need to do on a maverick terminal:

_**Add the ppa**_

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update

[U][B]Install the linux-alsa-driver-modules package

[/B][/U]sudo apt-get install linux-alsa-driver-modules-$(uname -r)

**Note: After installing the linux-alsa-driver-modules package, your system needs to be rebooted.**

All done. :)

---

### Post by sina_badboy on 2011-04-06
hi i have installed ubuntu recently.my laptop is inspiron n5010 and i need drivers for Graphic and broadcom wireless.
could you please help me to find download links??
thanks

---

### Post by meet.aman7 on 2011-04-23
> **safwankhan said:**
> I was having the same problem. However I recently managed to solve it by re-installing the latest version of Alsa-drivers. Here is what you need to do on a maverick terminal:

_**Add the ppa**_

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update

[U][B]Install the linux-alsa-driver-modules package

[/B][/U]sudo apt-get install linux-alsa-driver-modules-$(uname -r)

**Note: After installing the linux-alsa-driver-modules package, your system needs to be rebooted.**

All done. :)

Thank you safwankhan. It worked effectively for me.

@OP Please mark this thread as solved so that people can come to it quickly via google search.

---

### Post by amithoward on 2011-04-26
Thanks. I will check this out today. Hopefully it will work for me too ;)

---

### Post by poojasaraff on 2011-10-28
@[safwankhan]("http://ubuntuforums.org/member.php?u=1251673") - Thanks alot. It works gr8 now!!!!!!!! yay!!!!!!

---

