---
title: "Dell XPS (NEW) gets hot from the start"
date: 2011-03-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by senca on 2011-03-05
hey,
A couple of weeks ago I bough a new Dell XPS 15.
Whats inside: 6G RAM, 500Gb HDD, intel i5 560m dual core (with 4 threads in total)
I removed windows and replaced it with Ubuntu 10.10 64-bit.
When I turn it on it takes about 2 minutes before the fans start up. I don't even run  a lot of programs, even if the laptop is just in standby mode with nothing running on it, it starts getting hot and the fans start.
The place where it turns hot is the left upper part. 
I installed sensors-applet and put it on the panel. It shows me:
27°C - 0°C - 0°C - 27°C which I presume are my cores?

I also tried hddtemp:
sudo hddtemp /dev/sda with this result:
/dev/sda: ST9500420AS: 45°C

Are there any other things to test? Because this really doesn't seem hot enough to make the fans turn on after just 2 minutes :s

---

### Post by tgalati4 on 2011-03-05
Did it run hot under Windows?  What graphic card is on this machine?

---

### Post by senca on 2011-03-05
I used windows for like 3 days. It never went as hot as it does now.

These are the spec's from my hdd and graphics processor(from my Dell offer):

Hard Drive : 500GB Serial ATA (7200RPM)
Graphics : NVIDIA GeForce GT 420M 1GB graphics with Optimus

and this is a commandline output: (lspci)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)

---

### Post by Slave2Metal on 2011-03-06
That reading is for the motherboard or HDD I believe.  Most likely a combination of a couple things.  In linux, these machines are using the intel graphics and the nvidia card is just sitting there idle, making heat and drawing power.  Then, the thermal paste is probably not first rate.

---

### Post by senca on 2011-03-07
Basically my graphics card is never used? :s

---

### Post by Slave2Metal on 2011-03-07
Correct.  Powered on, doing nothing but creating heat and draining your battery.
> **senca said:**
> Basically my graphics card is never used? :s

---

### Post by senca on 2011-03-07
I tried installing an additional driver and it found one for nvidia but when I rebooted (as told) my GUI was gone :s. Had to reinstall ubuntu to fix it. 

Is there a way of making ubuntu use the proper graphics processor?

---

### Post by cascade9 on 2011-03-07
> **senca said:**
> I tried installing an additional driver and it found one for nvidia but when I rebooted (as told) my GUI was gone :s. Had to reinstall ubuntu to fix it. 

Is there a way of making ubuntu use the proper graphics processor?

If there isnt a way to force the nvidia GPU, or disable the iX video, then no. Nothing you can do AFAIK.

---

### Post by Slave2Metal on 2011-03-07
Some people are having success in turning off the nvidia card with an acpi_call script for the alienware m11xr2.  It does work, but I'm having trouble getting it to run at boot.
> **senca said:**
> I tried installing an additional driver and it found one for nvidia but when I rebooted (as told) my GUI was gone :s. Had to reinstall ubuntu to fix it. 

Is there a way of making ubuntu use the proper graphics processor?

---

### Post by senca on 2011-03-07
The nvidia is the one that should be working:p Thats the expensive one :p

---

### Post by senca on 2011-03-07
Maybe I should try to install the driver again for NVidia?

Edit: Is this actually an ubuntu issue or is Dell the 'ruiner' of my system?

---

### Post by senca on 2011-03-08
This is the driver that should work for my GPU but crashed it the last time. Got this by searching additional drivers throug the system menu.

3D-accelerated proprietary graphics driver for NVIDIA cards.

This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D acceleration of newer cards.

If you wish to enable desktop effects, this driver is required.

If this driver is not enabled, you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, such as some games.

---

### Post by Slave2Metal on 2011-03-08
I'm unable to find any information documenting an optimus card working with linux.  Doesn't mean its impossible.  How are the system 76 machines running ubuntu with these cards?  I hear they're getting horrible battery life, so maybe its not working in those either.

---

### Post by senca on 2011-03-08
[http://www.nvidia.co.uk/object/linux-display-amd64-260.19.44-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-260.19.44-driver-uk.html)

This seems promising. On the other hand a lot of people have trouble with their GPU.

---

### Post by cascade9 on 2011-03-09
> **Slave2Metal said:**
> I'm unable to find any information documenting an optimus card working with linux.  Doesn't mean its impossible.  How are the system 76 machines running ubuntu with these cards?  I hear they're getting horrible battery life, so maybe its not working in those either.

No, its not impossible, but you need a BIOS switch to force the nVidia GPU, disable the intel video, or (very rare cases) you can hack it with software. Thats all there is. 


> **senca said:**
> Maybe I should try to install the driver again for NVidia?

Edit: Is this actually an ubuntu issue or is Dell the 'ruiner' of my system?

You can blame dell for not putting a BIOS switch in, and nVidia for not releasing optimus drivers. Or yourslef for not checking out linux comptibility before buying. You choose.  

You can try to install the nVidia drivers all you want. With any of the ptions listed above, all you will do is bork your ubuntu install.... 

> **senca said:**
> If you wish to enable desktop effects, this driver is required.

If this driver is not enabled, you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, such as some games.

I thought that desktop effects would work with the newer iX video? I'm not sure, I dont use intel video unless I have no other choice, and I dont use compiz anyway.

---

