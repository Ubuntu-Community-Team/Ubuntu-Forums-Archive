---
title: "Lightscribe Anyone??"
date: 2008-11-19
forum: Desktop Environments
---

### Post by sauce345 on 2008-11-19
I was wondering if anyone else was having problems installing the deb packages from this Community Ubuntu howto:

[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

Anyway when i try to install the deb packages i get the error:

/tmp/lightscribe-1.14.32.1-linux-2.6-intel.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

I have browsed around a bit about this helper application problem but i have not had any luck yet.:(

---

### Post by Izek on 2008-11-20
Right-Click the deb, and go to the properties or whatever. When the dialog comes up, there should be an open with tab. What's it trying to open with?

---

### Post by binbash on 2008-11-20
instead of selecting 'open with gdebi' download it and install it via command line (sudo dpkg -i name.deb)

---

### Post by sauce345 on 2008-11-20
THanks this got it working for me. It is pretty cool technology.

---

### Post by PayPaul on 2011-09-30
> **sauce345 said:**
> I was wondering if anyone else was having problems installing the deb packages from this Community Ubuntu howto:

[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

Anyway when i try to install the deb packages i get the error:

/tmp/lightscribe-1.14.32.1-linux-2.6-intel.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

I have browsed around a bit about this helper application problem but i have not had any luck yet.:(

I have a similar problem. First of all I'm not even sure if my version if Ubuntu 11.04, already has 64 bit support for Lightscribe built in. I'd like to think it would but you never know. I read on the link you provide that if one tries to force 64 bit installation the Ubuntu install might get broken. I don't want to run that risk. I also tried hunting for packages relating to Lightscribe in both the software center and the Synaptic Manager to no avail. Please help me if you can.

Update: I checked the Lightscribe site and downloaded the Deb file. Yet when i try to open it up on Software Center the error message comes up as being the wrong package i386. What does that mean? Does it mean there NO lightscribe packages for this version of Ubuntu?

---

### Post by JRV on 2011-10-08
There is no support for Lightscribe in 64 bit 11.04.
Fortunately 11.10 has the ability to install 32 bit debs in a 64 bit system.
The simple labeler works in 11.10 beta, the fancy label printer (LaCie 4L) has unmet dependencies. 

 The official release of 11.10 will be Oct 13.

---

### Post by PayPaul on 2011-10-08
> **JRV said:**
> There is no support for Lightscribe in 64 bit 11.04.
Fortunately 11.10 has the ability to install 32 bit debs in a 64 bit system.
It works in 11.10 beta. The official release of 11.10 will be Oct 13.


A good incentive for me to upgrade and yes, that would be a clean install throughout.

---

