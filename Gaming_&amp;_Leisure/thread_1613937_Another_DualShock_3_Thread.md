---
title: "Another DualShock 3 Thread"
date: 2010-11-05
forum: Gaming &amp; Leisure
---

### Post by BrentonPHX on 2010-11-05
So, I'm sure this has been beaten to death, but I cant get my DualShock 3 controller to connect to Ubuntu. It was working in 10.04 using qJoypad...But now Im running 10.10 and my comp doesnt even recognize that its plugged in when I run {lsusb}...No flashing lights, nothing...Any help would be appreciated.

---

### Post by BrentonPHX on 2010-11-05
I seriously am going crazy over here.........anyone?

---

### Post by WeAreLinux on 2010-11-06
I don't have a solution to your problem, sorry.

Just a suggestion though. If it's very important for you, why not keep using 10.04 since it's a long term release version.

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Also maybe experiment with some alternative programs to qJoypad?

---

### Post by St0 on 2010-11-06
Can someone PLEEEEEase tell me how to install things in ubuntu, it's driving me insane!!

The readme in Qjoypad says to do this

./config
   make
   make install

I tried inputing it in terminal but didn't work. Please help!

---

### Post by WienerWuerstel on 2010-11-06
> **St0 said:**
> Can someone PLEEEEEase tell me how to install things in ubuntu, it's driving me insane!!

The readme in Qjoypad says to do this

./config
   make
   make install

I tried inputing it in terminal but didn't work. Please help!

First you should install [QtSixa]("https://launchpad.net/~falk-t-j/+archive/qtsixa"). This Program lets you use a Sixaxis/DS3 Pad over USB/Bluetooth. You can even choose multiple Profiles to use the DS3 as a Gamepad or as a Mouse/Keyboard

PS: Take a Chill Pill...

---

### Post by St0 on 2010-11-07
> **WienerWuerstel said:**
> First you should install [QtSixa]("https://launchpad.net/~falk-t-j/+archive/qtsixa"). This Program lets you use a Sixaxis/DS3 Pad over USB/Bluetooth. You can even choose multiple Profiles to use the DS3 as a Gamepad or as a Mouse/Keyboard

PS: Take a Chill Pill...

Ok thanks for the info. I still don't get how to install things though. 

first it tells me to put "sudo add-apt-repository ppa:falk-t-j/qtsixa" in terminal, then I think it says type in "deb [http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu](http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu) YOUR_UBUNTU_VERSION_HERE main" but change to "Maverick" in the command? 

all the gives me is 

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found


I don't get this linux stuff :(

---

### Post by St0 on 2010-11-07
Never mind, I've had enough of Linux now, I'll just go back to god awfull windows until a lot more stuff works in linux. Atleast you know programs are going to work most of the time in windows :(

---

### Post by WienerWuerstel on 2010-11-07
> **St0 said:**
> Never mind, I've had enough of Linux now, I'll just go back to god awfull windows until a lot more stuff works in linux. Atleast you know programs are going to work most of the time in windows :(

```
sudo add-apt-repository ppa:falk-t-j/qtsixa
```
```
sudo apt-get update
```
```
sudo apt-get install qtsixa
```

3 simple Commands and you have it installed. Linux can be so easy sometimes if you know what you are doing....

Ps: QtSixa+Sixaxis+Bluetooth= Epic Win :)

---

