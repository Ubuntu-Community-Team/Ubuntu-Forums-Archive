---
title: "i installed ubuntu today but????"
date: 2007-06-30
forum: Dell  Ubuntu Support
---

### Post by ashrafhumax on 2007-06-30
hello again
i instaled it on my dell 1505
but not supporting my 1390 dell wirelee card , i will handel it
my screen resolution not 1280*800, why??

---

### Post by liquidfunk on 2007-06-30
You don´t supply enough information. What graphics card do you have?

 What Ubuntu are you using?

---

### Post by fjgaude on 2007-06-30
> **ashrafhumax said:**
> hello again
i instaled it on my dell 1505
but not supporting my 1390 dell wirelee card , i will handel it
my screen resolution not 1280*800, why??

If you are using the latest kernel update, 2.6.20-16, the driver for the 1390 is already installed. If memory serves, its the Broadcom 43xx series.

What video is in your 1505, ATI, Intel, or nVidia?

frank

---

### Post by ashrafhumax on 2007-06-30
sorry
my card is intel 945g my windows resolution is 1280*800but i get 1024*800 as max.
the dell wirelss card is not supported by 7.4 ubunutu

---

### Post by fjgaude on 2007-06-30
To fix your video issue, install 915resolution using apt-get or Synaptic Package Manager.

I still believe the wifi driver is already there, but can't remember how to get to it. Maybe someone else here will help. Your 1505 is not what most of us have, e1505n comes with another Intel board other than Broadcom.

frank

---

### Post by ashrafhumax on 2007-06-30
thanks

---

### Post by neptho on 2007-06-30
Try following [this guide](http://pervasivecomputing.net/ubuntu_feisty_7_04_on_dell_inspiron_e1505) to get your 1390 working.  Obviously, ignore the bit about the ATI drivers.  :)

---

### Post by Robertorps on 2007-07-02
Thanks for the tutorial. I have a Dell Inspiron 1300 with a Boradcom 1370 Wireless card and it worked.

The 915resolution software fixed my resolution automatically.

thanks again for the post.

Roberto

---

### Post by sk9 on 2007-07-12
> **Robertorps said:**
> Thanks for the tutorial. I have a Dell Inspiron 1300 with a Boradcom 1370 Wireless card and it worked.

The 915resolution software fixed my resolution automatically.

thanks again for the post.

Roberto

I have installed 7.04 on an 1100 and I only have about a 9' screen (about 2" of black border all the way around. installed 915resolution but no change?

---

### Post by Robertorps on 2007-07-14
What's your resolution?

Mine is 1280 x 800 pixels (size of the screen). There wasn't any change until I restarted the computer.

---

### Post by TD-Linux on 2007-07-14
I also have a Broadcom chipset, though not Dell. I found an even easier way to get wireless working, without having to install the ndiswrapper driver. All you need to do is install the bcm43xx-fwcutter package, and say yes when it asks you do download the driver. That will use the built-in native linux driver, with the firmware downloaded from Broadcom's webpage.

---

### Post by strabes on 2007-07-15
> **sk9 said:**
> I have installed 7.04 on an 1100 and I only have about a 9' screen (about 2" of black border all the way around. installed 915resolution but no change?

Have you checked the your bios settings where it asks you if it will stretch out fullscreen resolutions lower than the native resolution or just show black around the edges? Also, have you installed [video card drivers](https://help.ubuntu.com/community/BinaryDriverHowto/)?

---

### Post by dougleduck on 2007-07-23
I had problems with my 1100 screen res. I had to alter some video setting file. Simple to do. If you want I can find the fix I had to do to make mine work when I get back to my laptop.

---

