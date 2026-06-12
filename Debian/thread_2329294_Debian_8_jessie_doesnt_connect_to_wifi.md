---
title: "Debian 8 jessie doesnt connect to wifi"
date: 2016-06-29
forum: Debian
---

### Post by gunner5 on 2016-06-29
Hello guys, im testing some debian distros and i picked the lexd x64 installed on my hp 14. The problem is wifi doesnt seem to work, i get the lan working installing a non-free package from [here](https://packages.debian.org/jessie/kernel/firmware-realtek) but that just fixed lan, wifi still is not working. And a laptop without wifi isnt a laptop... jaja. Hope you guys give me a hand with this.
So, i forgot, this is the firmware aparently misses: rtl8106e-1.fw
Thank you!

---

### Post by arochester on 2016-06-30
lexd x64 ?

---

### Post by gunner5 on 2016-06-30
Yeah, amd64 actually. Dont know if theres a difference. Downloaded from [here](http://cdimage.debian.org/debian-cd/current-live/amd64/bt-hybrid/) lexd desktop.

---

### Post by arochester on 2016-07-01
I think you may have downloaded the wrong version.  

You have downloaded a version with NO "non-free", therefore you don't have the wireless firmware built in.  If you are using it as a Live-CD you can download the firmware, but the wifi will only work on reboot ---and then you have lost the firmware!

You need a download from here: [http://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/8.5.0-live+nonfree/amd64/iso-hybrid/](http://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/8.5.0-live+nonfree/amd64/iso-hybrid/)

---

### Post by gunner5 on 2016-07-01
Ops... im really not familiar with debian... jaja, but well, linux is always a challenge. Going to download that distro and im telling you guys how it goes. Can i download the same distro? I mean lexd or you can recommend me some other taste. Im using it for doing some vnc and dns projects.
Thx a lot!

---

### Post by arochester on 2016-07-02
Download the lxde version from the link I gave - debian-live-8.5.0-amd64-lxde-desktop+nonfree.iso

---

### Post by gunner5 on 2016-07-02
Great, now wifi and lan works smooth. Thx a lot, with previous distro (free i guess) i cant install any package, always getting error about non existing package or something like that. This have relation with non-free distro?
Once again, thx a lot!

---

### Post by arochester on 2016-07-03
I'm not sure what you mean.

With a LiveCD  everything is in the CD.  When the LiveCD is running you can download an application, but it will not be placed (magically) on the CD. When you switch off the download will be lost. You will go back to just having what is on the LiveCD.***

There are other ways to try Linux without messing up your existing OS. 

A.
You can use a USB Flash Drive (if your computer  will boot from USB)
1) The "normal" install  just puts the same LiveCD on a USB Flash Drive
2) The "persistent" install. This is where you put another partition on the USB - like having  a "Home" on the stick, where you can save SOME stuff. 
3 The "full-install" where you just install the whole OS on the stick. Depending on the size of the stick it should save all changes.

B.
Dual Booting. This is where you install TWO OSs on you hard drive and you can choose which one to use.

C.
Virtualisation. This is where you create a "virtual machine" inside your existing OS, where you can fully run the new OS.

*** One exception to the LiveCD  not saving, is "Puppy Linux" which will save changes to the Hard Drive as a file with the extension . sfs ---Puppy Linux is an acquired taste.

---

### Post by gunner5 on 2016-07-03
No, i installed previous lexd on my laptop, installed that non-free package. With that lan works but not wifi, with lan working in terminal cant find any package nor install, for example i wanted to install tightvncserver but aptitude gives me an error, cant find the package. Im talking of first debian distro i installed.
But now works great, now i can do some experiments with vnc.
Oh, another thing, doing some vnc with a raspberry pi (raspbian) i can see the desktop with a cellphone (remote ripple) but with debian i cant, just with vnc viewer

---

### Post by T.J. on 2016-07-03
Because of ethics and laws, Debian does not distribute proprietary firmware with the kernel.  I'm glad you have your wi-fi working.  

Just for future reference, you can download a special boot image for installing Debian that includes some of the firmware if you need it for installs.  Your hardware is Realtek, so installing the "firmware-realtek"  package should help.  

Best of luck to you!

---

### Post by etimer on 2017-03-12
Having a wirless comp sitting in a room without Ethernet kind of makes a live try worthless wouldn't you say?  So there is an issue with Wifi drivers but why not the ethical issue for the Ethernet Controller Driver?  Doesn't the OS need to have something to shake hands with the ECD? 

I guess Kubuntu live doesn't have the same ethical issues or the rest in the stack of DVD's?

If the world ran like the tech industry we would have HVAC systems in our house that would have a thermostat that couldn't talk to the furnace.  You would be required to only buy the furnace manufacturers thermostat. :confused:

> **T.J. said:**
> Because of ethics and laws, Debian does not distribute proprietary firmware with the kernel.  I'm glad you have your wi-fi working.  

Just for future reference, you can download a special boot image for installing Debian that includes some of the firmware if you need it for installs.  Your hardware is Realtek, so installing the "firmware-realtek"  package should help.  

Best of luck to you!

---

### Post by T.J. on 2017-03-12
> **etimer said:**
> Having a wirless comp sitting in a room without Ethernet kind of makes a live try worthless wouldn't you say?  So there is an issue with Wifi drivers but why not the ethical issue for the Ethernet Controller Driver?  Doesn't the OS need to have something to shake hands with the ECD? 

I guess Kubuntu live doesn't have the same ethical issues or the rest in the stack of DVD's?

If the world ran like the tech industry we would have HVAC systems in our house that would have a thermostat that couldn't talk to the furnace.  You would be required to only buy the furnace manufacturers thermostat. :confused:

That is why I suggested the install disc with additional drivers. The decision to include or not include a particular driver was not my doing.  The sarcasm is understandable, but not helpful.   Use what works for you, and agrees with your particular stance of inclusiveness.  Outside of that, welcome to the world of computing.  I’ve written code and used many different systems over the years, Windows and Linux included.  All of them have deficiencies.  There is no such thing as a perfect OS.

I do wish you the best of luck and if I can answer anything else, you are welcome to ask.

---

### Post by QIII on 2017-03-12
> why not the ethical issue for the Ethernet Controller Driver? 

It may be open source or otherwise publicly available.  That is an issue to take up with Debian.

Is there a particular reason you chose such an old thread -- not one of your own -- to use for stirring things up?

Rest in Peace, good thread.

Closed

---

