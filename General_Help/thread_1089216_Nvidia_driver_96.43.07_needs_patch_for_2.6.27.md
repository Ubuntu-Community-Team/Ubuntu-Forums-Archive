---
title: "Nvidia driver 96.43.07 needs patch for 2.6.27"
date: 2009-03-06
forum: General Help
---

### Post by ozguitarplayer on 2009-03-06
I'm way out of my depth here...
Installed video card Nvidia Quadro4 380 GLX
Downloaded the Linux driver from Nvidia
When I try to run the driver I get...

nigel@kubu8:~$ sh NVIDIA-Linux-x86-96.43.07-pkg1.run sh: Can't open NVIDIA-Linux-x86-96.43.07-pkg1.run
nigel@kubu8:~$

If I try to install the driver with Hardware Drivers the system locks up.
When I reboot the system stalls during the check stage and I see...


#Running DKMS auto installation service for Kernel 2.6.27-7-generic
#Nvidia 96.43.09                                               fail

I searched and found a nvidia-96.43.07kernel2.6.27.patch

My questions are; 
1. Can terminal not open the driver because the .patch is missing?  
2. Do I run the patch in terminal first?
3. The Nvivia 96.43.09 I believe is a beta driver, does anyone know if this driver works well with Intrepid Ibex

Any advice would be most welcome as I know nothing about video cards and drivers and i'm reluctant to proceed as i feel I was lucky to get around the stalled boot that was caused from trying to install the driver.

---

### Post by martrn on 2009-03-06
To install the nVidia kernel module (driver) you can not 'sh NVIDIA-Linux-x86-96.43.07-pkg1.run' but you can :

```
sudo sh ./NVIDIA-Linux-x86-96.43.07-pkg1.run
```

'sudo' allows the process to run as root for that process only which is necessary if installing kernel modules (drivers),

---

### Post by ozguitarplayer on 2009-03-07
thanks martrn however the result is the same...terminal says it can't open the file and if I try to view the file in text editor (kate) the editor locks up and can lock up the computer, there must be something wrong with the file, is this possible?

...and is a driver downloaded from Nvidia better than what can be found in the repositeries?

---

### Post by martrn on 2009-03-07
> **ozguitarplayer said:**
> thanks martrn however the result is the same...terminal says it can't open the file and if I try to view the file in text editor (kate) the editor locks up and can lock up the computer, there must be something wrong with the file, is this possible? ...and is a driver downloaded from Nvidia better than what can be found in the repositeries?

Envy is the best way to install the nvidia driver from ubuntu and is a program / script writen by a pyton programmer to download and install the binary driver from nvidia See : [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html").

Installing The Binary Driver from nvidia either via Envy or by downloading the driver is the best way to install binary drivers for nvidia cards.  You need to remove already installed binary blobs from the reposotories or wherever first and then re-install the nvidia kernel module if you do.

The ubuntu nvidia manual is at : [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

Do not open any binary in kate or any text editor as it will likely crash or exit the text editor.

If you wish to do it the nVidia way (the way I do it), yes it will give you a upto date nVidia kernel module for your kernel and will be more upto date, and for your kernel that you are using.  However the process is thwart with a few difficulties.  Firstly you have to install the cpp headers for your kernel package and build essential tools.  See again the [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual") for instructions.

The Envy method you will see is a lot easy and achieves similar results but do not know about weather it will be the latest version but will be upto date or fairly upto date.

---

### Post by ozguitarplayer on 2009-03-07
ok thanks again martrn, sounds like I need to fiddle for a while, if it's alright with you I will reply again with an update in a couple of days...I'm working with both Hardy and Intrepid and from searching I think Intrepid isn't so easy...

---

### Post by ozguitarplayer on 2009-03-07
all good now, thanks for the advice martrn

---

