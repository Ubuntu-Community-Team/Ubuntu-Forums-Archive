---
title: "Please help with install"
date: 2009-01-06
forum: General Help
---

### Post by froggyone on 2009-01-06
Hello,
I am 100% new to Linux I do not know all the commands to get this working. I can install Ubuntu just fine in seems, I am able to get the Ubuntu logo and the progress bar under it, but after that all I seem to get is a command line. I have posted here about this subject but have not heard anything new from the people I was talking to and the problem is still there. I am lost any help would be great. Where we left of was looking at the contents of your /etc/X11/xorg.conf file and this is what I had.
[B][I]Section "Device"
Identifer "Configured Video Device"
EndSection

Section "Monitor"
:[/I][/B]

Thanks for any help to get this fixed

My system:
Motherboard:Biostar TPower Nvidia NForce 750a SLI
CPU: AMD Phenom 9950 Quad-Core @ 2.6
Memory: 2, 2 gigs sticks OCZ (DDR2 800)
Video: 2, Nvidia GeForce 8600 GT setup for SLI
DVD Burner: Pioneer DVD-RW
Hard Drive: WD 500 gigs

---

### Post by x22 on 2009-01-06
OK, first try

"startx"

then when that fails, try

"sudo dpkg --configure xserver-xorg"

---

### Post by gettinoriginal on 2009-01-06
This is what mine looks like:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```
It sounds like maybe you have a bad live disk, did you burn the ISO? did you burn it at the slowest speed? did you do a disk check before installing?  All of these can cause a bad install.  Did the live CD let you into Ubuntu without install?

---

### Post by Loosewheel on 2009-01-06
Hi froggyone
You can try 'recovery mode' at the startup boot menu which should get you a GUI. Then click on 'System>Administration>Hardware Drivers. See what it says in there about nVidia drivers for your card. (xorg.conf can be a little tricky)

---

### Post by froggyone on 2009-01-06
I tried the live cd and it took me to the same command line, I did not burned the ISO at the slowest speed and did not do a disk check.
when I ran "sudo dpkg --configure xserver-xorg" it gave me this

[B][I]dpkg: error processing xserver-xorg (--configure):
package xserver-xorg is already installed and configure
Errors were encountered while processing: xserver-xorg [/I][/B]

Others have said the it might be the drivers for the video card, I have read a few things on installing the drivers for nvidia, but none of them have told he how to do it and what code to type to install them from a flash drive, unless there is another way to do it.

---

### Post by thedarkwinter on 2009-01-06
Hi Froggy

You can trying setting your xorg.conf to use the vesa driver, just to see if you can get into the GUI.


```
Section "Device"
    Identifer "Configured Video Device"
    Driver    "vesa"
EndSection
```

Restart X (or the computer) and see if it boots into the graphic interface. From there, you can experiment further, either with the "Hardware Drivers" or with envyNG.

(Lets see if vesa works first...)

Cheers,
Michael

---

### Post by lord_lethris on 2009-01-06
Does SLI work under Linux ;)

---

### Post by thedarkwinter on 2009-01-06
haha, i don't know actually.

I presume it "works" but i doubt that its optimized...

---

### Post by froggyone on 2009-01-06
> **thedarkwinter said:**
> Hi Froggy

You can trying setting your xorg.conf to use the vesa driver, just to see if you can get into the GUI.


```
Section "Device"
    Identifer "Configured Video Device"
    Driver    "vesa"
EndSection
```

Restart X (or the computer) and see if it boots into the graphic interface. From there, you can experiment further, either with the "Hardware Drivers" or with envyNG.

(Lets see if vesa works first...)

Cheers,
Michael

Ok I will try that but like I said before I have no clue how it do that could please add a little more detail

---

### Post by froggyone on 2009-01-07
> **thedarkwinter said:**
> Hi Froggy

You can trying setting your xorg.conf to use the vesa driver, just to see if you can get into the GUI.


```
Section "Device"
    Identifer "Configured Video Device"
    Driver    "vesa"
EndSection
```

Restart X (or the computer) and see if it boots into the graphic interface. From there, you can experiment further, either with the "Hardware Drivers" or with envyNG.

(Lets see if vesa works first...)

Cheers,
Michael

I have changed it but still have the command line, this has the be a problem with video drivers, but no matter where I search I can only find how to install the through a GUI not for a command line interface.

---

### Post by Unforgiven247 on 2009-01-07
I'm gonna take a stab at this, I could be wrong. But are you sure all the packages are installed that are required by the binary ? 

Example is here for my ATI DO NOT DO THIS IT"S FOR ATI unless you find instructions to do so.

sudo apt-get install dpkg-dev debhelper libstdc++5 dkms build-essential cdbs fakeroot

I had to add those before I could use the binary

The I had to do

./ati-driver-installer-8.443.1-x86.x86_64.run --buildpkg Ubuntu/<version> 

To see m supported builds

Then I did

sudo dpkg -i fglrx-kernel-source_<version>.deb

That built my .deb package

sudo dpkg -i xorg-driver-fglrx_<version>.deb

That installed it.

I would make sure you are not missing any dependancies, then try the 

sudo ./NVIDIA-Linux-x86-180.06-pkg1.run --buildpkg

See what it says

Quick question, are you 64bit or 32 ? I took 64 off since it was such a pain making things work.

---

### Post by thedarkwinter on 2009-01-07
Hi

you can try using envy in text mode:

> 
sudo apt-get install envyng-qt
envyng -t


this will give you the option to install nvidia drivers, and then restart X

good luck...

---

### Post by lord_lethris on 2009-01-07
> **thedarkwinter said:**
> haha, i don't know actually.

I presume it "works" but i doubt that its optimized...

Its just that I know Vista has issues with SLI, they managed to get it resonably stable in XP... So i'm just wondering if it works at all in Linux.

I'm only saying because froggyone in his/her system spec, has his/her system setup in SLI mode.  I'm wondering if his/her issues (like in Vista) will "disappear" if SLI is switched off ;) ;) ;)


[COLOR="Red"]*[SIZE="1"]FTR - Lord Lethris will still insist that SLI/CrossFire is heavily over rated theses days.  And its real purpose is completely misunderstood thanks to nVidia's B*llsh** propaganda.[/SIZE][/COLOR]

---

### Post by froggyone on 2009-01-11
The problem is fix, all I had to do was to take out one of my video cards and everything come right up. 

Thanks for you help

---

### Post by gettinoriginal on 2009-01-11
Glad it is fixed :p  Please go to thread tools and mark this as solved.

---

