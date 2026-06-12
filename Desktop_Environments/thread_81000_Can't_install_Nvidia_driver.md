---
title: "Can't install Nvidia driver"
date: 2005-10-23
forum: Desktop Environments
---

### Post by Daandaan on 2005-10-23
I have a Nvidia Geforce 5200 fx gpu and I use ubuntu 5.10. When I try to install the nvidia driver, I get an error which says:
ERROR: Unable to find the system utility `ld`; please make sure you have the           package 'binutils' installed.  If you do have binutils installed,           then please check that `ld` is in your PATH.
What do I have to do, I'm kinda new to linux.
-= Greetz Daan=-

---

### Post by VR6Pete on 2005-10-23
Try the following from a console:

```
sudo apt-get install binutils
```

---

### Post by Daandaan on 2005-10-23
Waw! That worked, thx a lot! :)
But now I have a new error:( 
It says:
ERROR: You appear to be running an X server; please exit X before
         installing.  For further details, please see the section INSTALLING
         THE NVIDIA DRIVER in the README available on the Linux driver
         download page at [www.nvidia.com](www.nvidia.com).
I guess this readme file can be found [here]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7676/README.txt") but I don't understand a thing of it. Someone can help me?
-= Greetz Daan=-

---

### Post by ippiraman on 2005-10-23
How did you install the nvidia driver by the way?

sudo apt-get install nvidia-glx

---

### Post by VR6Pete on 2005-10-23
Yep, I just ran sudo apt-get install nvidia-glx and it installed version 7667 (which I think is the latest version)

Pete

---

### Post by Daandaan on 2005-10-23
No, I followed the instructions on the Nvidia site. I opened a terminal, went to the place where the file is, typed sudo sh NVIDIA-Linux-x86-1.0-7676-pkg1.run and that's it.
-= Greetz Daan=-

---

### Post by Daandaan on 2005-10-23
[QUOTE=VR6Pete]Yep, I just ran sudo apt-get install nvidia-glx and it installed version 7667 (which I think is the latest version)

Pete[/QUOTE]
I tried this too and it says
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Voorgestelde pakketten:
  nvidia-settings nvidia-kernel-source
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  nvidia-glx
0 pakketten opgewaardeerd, 1 nieuwe pakketten geïnstalleerd, 0 verwijderen en 3 niet opgewaardeerd.
Er moeten 0B/3085kB aan archieven opgehaald worden.
Na het uitpakken zal er 10,3MB extra schijfruimte gebruikt worden.

Voorconfigureren van pakketten...
Selecteren van voorheen niet geselecteerd pakket nvidia-glx.
(Database inlezen ... 60095 bestanden en mappen geïnstalleerd.)
Uitpakken van nvidia-glx (uit .../nvidia-glx_1.0.7667-0ubuntu25_i386.deb) ...
Instellen van nvidia-glx (1.0.7667-0ubuntu25) ...
Creating NVIDIA TLS links... done.
Is it now properly installed?
-=Greetz Daan=-

---

### Post by VR6Pete on 2005-10-23
ahh, looks like there are a newer version of the drivers out....

---

### Post by Incendium on 2005-10-23
I just ended up using the nvidia drivers through synaptic. Better than nothing.

---

### Post by VR6Pete on 2005-10-23
[QUOTE=Daandaan]I tried this too and it says
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Voorgestelde pakketten:
  nvidia-settings nvidia-kernel-source
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  nvidia-glx
0 pakketten opgewaardeerd, 1 nieuwe pakketten geïnstalleerd, 0 verwijderen en 3 niet opgewaardeerd.
Er moeten 0B/3085kB aan archieven opgehaald worden.
Na het uitpakken zal er 10,3MB extra schijfruimte gebruikt worden.

Voorconfigureren van pakketten...
Selecteren van voorheen niet geselecteerd pakket nvidia-glx.
(Database inlezen ... 60095 bestanden en mappen geïnstalleerd.)
Uitpakken van nvidia-glx (uit .../nvidia-glx_1.0.7667-0ubuntu25_i386.deb) ...
Instellen van nvidia-glx (1.0.7667-0ubuntu25) ...
Creating NVIDIA TLS links... done.
Is it now properly installed?
-=Greetz Daan=-[/QUOTE]

Looks good. restart X and you should see the nvidia splash screen - this should tell you if the drivers are installed correctly.

---

### Post by Daandaan on 2005-10-23
The reason why I installed the driver in the first place is because I wanted to have my screen refresh rate fixed. It's to low, I have a 1076*768 screen and my refresh rate is 60 but my screen can handle 75 but I can only choose 60...:(

---

### Post by VR6Pete on 2005-10-23
Give the following a whirl, worked for me!:

[http://ubuntuforums.org/showthread.php?t=76387](http://ubuntuforums.org/showthread.php?t=76387)

---

### Post by Daandaan on 2005-10-23
[QUOTE=VR6Pete]Looks good. restart X and you should see the nvidia splash screen - this should tell you if the drivers are installed correctly.[/QUOTE]
When I rebooted my computer I couldn't see any nvidia splash screen :(

---

### Post by VR6Pete on 2005-10-23
Check /etc/X11/xorg.conf

Look for the following:

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nvidia"

If it only says Driver "nv" try changing it to "nvidia"

Pete

---

### Post by Daandaan on 2005-10-23
Wow! Now I can see the Nvidia splash screen and my refresh rate problem is solved.
Thx for your help, and for the quick replies :) :KS 
-= Greetz Daan=-

---

### Post by VR6Pete on 2005-10-23
That is good news! Hope your Ubuntu experience is as pleasent as mine :)

Pete

---

