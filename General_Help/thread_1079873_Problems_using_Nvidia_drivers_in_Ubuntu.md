---
title: "Problems using Nvidia drivers in Ubuntu"
date: 2009-02-24
forum: General Help
---

### Post by planet-reptile on 2009-02-24
Hi.

When i install Nvidia driver (version 173 or 177) from Hardware drivers and reboot my laptop slows down alot. There are delays in loading the desktop after logging in and loading firefox takes longer to load. In gennerel everything slows down. I know that it is the Nvidia drivers who is causing this problem because when i uninstall the drivers, everything runs normal. But i need the drivers to adjust the resolution of the screen.

Hope someone can help.

Edit:
Acer Aspire 8930G
Intel Core 2 Duo processor P8600
2.4GHz, 1066MHz FSB
4Gb DDR3 Ram.
Nvidia GeForce 9700M GT

---

### Post by taurus on 2009-02-24
Perhaps you want to use the newer driver, 180 instead of the 173 (legacy driver) or 177!  Go into synaptic and **Search** for envy and see if it includes the new driver for your nvidia graphic card.

---

### Post by planet-reptile on 2009-02-24
Searched for envy in synaptic but don't know which of them to install.
Tryed to search for nvidia and marked the ones called 180, but still no success.

Hope i'm not the only one with this problem.

---

### Post by BGFG on 2009-02-24
You could try to install the latest driver manually.

here it is:
[ftp://download.nvidia.com/XFree86/Linux-x86_64/180.35/](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.35/)

you want to grab the pkg2 file. Download to the desktop then follow these instructions.


How to install this drivers:

Uninstall any existing drivers first.

1) 
```

CONTROL + ALT + F1 

```
Takes you to a black screen. text input only. This is fine :)

3) Turn off x.org:
```

sudo /etc/init.d/gdm stop

```

4) Go to your desktop:
```

cd Desktop

```

5) Run the installer:
```

sudo sh ./NVIDIA-Linux-x86_64-180.35-pkg2.run

```

Don't forget to choose x.org automatic configuration at the last step inside the installation program.

6)  
```

sudo /etc/init.d/gdm start

```

Since copy and paste won't be available, you should write down the commands exactly.

Have Fun! :)

---

### Post by mb_webguy on 2009-02-25
Install the envyng-gtk package, then run EnvyNG from the terminal using "envyng -t".  Unfortunately, the actual GTK interface is still in development, but the text version is menu-driven and just as easy to use.

---

### Post by planet-reptile on 2009-02-25
Is that for 32bit or 64bit?
Tryed your codes on my 64bit and it didn't worked very well.

```
cd Desktop
```
does not work. I'm stuck in the black screen and have to shut it down using Alt + F4

```
sudo sh ./NVIDIA-Linux-x86_64-180.35-pkg2.run
```
Does not work either

Am i supposed to stay in black screen through all the commands or should i get to the desktop when i type cd desktop?

---

### Post by mb_webguy on 2009-02-25
> **planet-reptile said:**
> Is that for 32bit or 64bit?
Tryed your codes on my 64bit and it didn't worked very well.

```
cd Desktop
```
does not work. I'm stuck in the black screen and have to shut it down using Alt + F4

```
sudo sh ./NVIDIA-Linux-x86_64-180.35-pkg2.run
```
Does not work either

Am i supposed to stay in black screen through all the commands or should i get to the desktop when i type cd desktop?

If you're typing commands, you need to be in the terminal.  The command "cd" means "change directory", and is how you move from one folder to another in the terminal.  So "cd Desktop" means to change to the Desktop directory, which is in your home folder (which is where you start when you first open the terminal).  

The command "sudo" means to perform the next command using superuser privileges, and is generally required when you're making system-wide changes.  The "sh" command means to start a shell, and if you give it a file (specifically a script, such as the NVIDIA-Linux-x86_64-180.35-pkg2.run file) it will run the commands in the script.  If the script is executable (which you can set using the command "chmod +x NVIDIA-Linux-x86_64-180.35-pkg2.run"), you can just type "sudo ./NVIDIA-Linux-x86_64-180.35-pkg2.run" instead, without using "sh".

Like I said, though, I'd use EnvyNG to make it easier on yourself, and also make sure you're installing the best driver for your card.

---

### Post by planet-reptile on 2009-02-25
> Install the envyng-gtk package, then run EnvyNG from the terminal using "envyng -t". Unfortunately, the actual GTK interface is still in development, but the text version is menu-driven and just as easy to use.
Thank you!
I installed NVIDIA 177 (there were no 180 driver) and everything was the same as before, slow system and so on. But when i uninstalled the driver, the desktop kept the good resolution and my system is running perfect now.
Thanks man :-)

---

### Post by caryb on 2009-02-25
I am in the process of going back to 180.29 All I get is a black screen & it saying no screens found on my IBM T61


Cary

---

### Post by BGFG on 2009-02-25
> **caryb said:**
> I am in the process of going back to 180.29 All I get is a black screen & it saying no screens found on my IBM T61


Cary

Try this:
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by avilella on 2009-04-13
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

If you have access to any of the laptops below and have tried to run Linux, please take a moment to provide the DSDT information for the laptop in this link:

[http://bugs.launchpad.net/bugs/312756](http://bugs.launchpad.net/bugs/312756)

Sony Vaio Z-series (intel/nvidia)
Fujitsu Siemens Amilo XI 3650 (intel/nvidia)
BenQ Joybook S42 (intel/nvidia)
ASUS N10J (intel/nvidia)
Dell Studio XPS 13 (nvidia/nvidia)
ASUS Intros G71Gx (?/nvidia GeForce 260M)
MSI GT628 (?/nvidia GeForce 160M)
LG Xnote P510 Laptop (?/nvidia GeForce GT 130M)
HP HDX 18t (?/nvidia GeForce GT 130M)
Dell XPS M1730 (nvidia/nvidia)
MSI EX630 (nvidia/nvidia -- )
Toshiba Qosmio X305-Q706/Q708 (nvidia/nvidia -- 9400m + 2x9800m GTS)
Acer Aspire 7530 (nvidia/nvidia -- 9100M G + GeForce 9300M GS)
ASUS X83Vm-X1 (?/nvidia)
+ Clevo M860TU (?/nvidia GeForce 9800M GTS)
+ Acer Aspire 8930G (?/nvidia GeForce 9700M GT)
+ Asus G50V (?/nvidia GeForce 9700M GT)
Lenovo ThinkPad T500 (intel/ati)
Lenovo ThinkPad T400 (intel/ati)
ASUS M51Ta (intel/ati)
Fujitsu-Siemens Amilo Sa 3650 (intel/ati)
MSI PX211 12'' (intel/ati)
HP Pavilion tx2500 (intel/ati)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

---

### Post by spudtheimpaler on 2010-03-24
> **avilella said:**
> [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

If you have access to any of the laptops below and have tried to run Linux, please take a moment to provide the DSDT information for the laptop in this link:

[http://bugs.launchpad.net/bugs/312756](http://bugs.launchpad.net/bugs/312756)

...
Fujitsu Siemens Amilo XI 3650 (intel/nvidia)
...

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

Hi, I have the Amilo mentioned and on looking up why none of the recommended nvidia drivers seem to work (although i have at least working graphics, I'm guessing through intel, on clean install)

I wanted to help so tried the above, but acpidump is a package that couldn't be found. Any ideas?

Cheers,
Mitch.

---

### Post by realzippy on 2010-03-24
[https://launchpad.net/ubuntu/+source/acpidump/20071116-1](https://launchpad.net/ubuntu/+source/acpidump/20071116-1)

---

### Post by spudtheimpaler on 2010-03-24
> **realzippy said:**
> [https://launchpad.net/ubuntu/+source/acpidump/20071116-1](https://launchpad.net/ubuntu/+source/acpidump/20071116-1)

cheers :)

---

