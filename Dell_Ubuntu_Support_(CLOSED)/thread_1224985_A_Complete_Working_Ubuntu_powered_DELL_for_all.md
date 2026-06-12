---
title: "A Complete Working Ubuntu powered DELL for all?"
date: 2009-07-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by FirstByté on 2009-07-28
This thread is created to help improve the "Out-Of-The-Box" experience for [SIZE="2"]**DELL Ubuntu**[/SIZE] users. Do you have a unique work around some issues that you faced getting your Ubuntu to run like it is today? Come share it. Do you have suggestions for improvements?
Let's make Ubuntu more "**generic**" for future Ubuntu releases.
Let's expand Ubuntu!

**[SIZE="3"]Ubuntu[/SIZE]** - Linux for Human Beings!

---

### Post by jimmyhacker on 2009-07-28
oh dude,you just touched my sensible part.my friggin mom doesn`t want Ubuntu or NetBSD on her good Dell Inspiron 1525 :( i did everything from compiz to processor benchmarks with hardinfo to convince her..what a fag is my mother :(

---

### Post by FirstByté on 2009-07-28
Ubuntu has evolved tremendously over the recent years. Starting with the success of Ubuntu 7.10 Gutsy Gibbon, then acclaims of Ubuntu 8.10 Intrepid Ibex; it's no doubt "Ubuntu 9.10" would slam us all in the face with Ultimate completion!

Huge thanks to the Canonical group: **Ubuntu** - Linux for Human Beings! They have kept their word, they have kept their promise. Making the next "Ubuntu 9.10" release even a better experience for all (*DELL users*) lie within the hands of this great community.

==========================================
Things that worked Out-Of-The-Box on a fresh Ubuntu 8.04 install

**Graphics:** (Restricted drivers solution)With full 3D/Extra effects support
**Remote Control** (Tested on a none DELL machine)
**Media Buttons**
**Audio** Alsa

:popcorn:

Things that **did not** worked Out-Of-The-Box on a fresh Ubuntu 8.04 install

**Wireless LAN:** Solved in Ubuntu 8.10 Intrepid Ibex release.
**Fingerprint Reader**
**Touch Screen:** (Tablet device)

=================
Things that worked Out-Of-The-Box on a fresh Ubuntu 8.10 install

**Graphics** With full 3D/Extra effects support
**Wireless LAN**
**Media Buttons*** (Except **Eject button**s for DELL Laptops with capacitive touch)
**Audio*** Alsa/PulseAudio (**Except headphone jack mute support**)

:popcorn:

Things that **did not** worked Out-Of-The-Box on a fresh Ubuntu 8.10 install

**Remote Control** (Tested on a DELL machine, works on HP machine)
**Fingerprint Reader**

=================
Things that worked Out-Of-The-Box on a fresh Ubuntu 9.04 install

**Graphics*:** **Without** full 3D/Extra effects support (Tested on Intel GM965[it was blacklisted for stability issues])
**Wireless LAN**
**Media Buttons*** (Except **Eject button**s for DELL Laptops with capacitive touch)
**Audio*** Alsa/PulseAudio (**Except headphone jack mute support**)

:popcorn:

Things that **did not** worked Out-Of-The-Box on a fresh Ubuntu 8.10 install

**Remote Control** (Tested on a DELL machine, works on HP machine)
**Graphics:** Full 3D/Extra effects support disabled (Tested on Intel GM965[it was blacklisted for stability issues])
**Fingerprint Reader**

---

### Post by FirstByté on 2009-07-28
**Bump** 
**Bump**

Anyone with fixes for DELL for these hardware issues:

**Remote Control **
**Graphics:** Full 3D/Extra effects support disabled (Tested on Intel GM965[it was blacklisted for stability issues])
**Fingerprint Reader**
**Audio Jack / mute support**

Thanks for making Ubuntu great on DELL!

---

### Post by josephe on 2009-07-29
Hi there
I have an Inspiron 1520, dual booting Vista ( I know why???) and Ubuntu 9. Both working ok, Vista is Slooow (what's new) to start up. anyway,my question is that when I shut down Ubuntu, my screen show the Ubuntu logo as normal then it fills with thin horizontal white lines, almost looks like static. I think its a screen driver Nvideo (I think) problem.
 
Any clues on fixes this, I'm sure it's not good for the machine. or my eyes
 
Thanks 
 
Joseph

---

### Post by FirstByté on 2009-07-30
> 
anyway,my question is that when I shut down Ubuntu, my screen show the Ubuntu logo as normal then it fills with thin horizontal white lines, almost looks like static. I think its a screen driver Nvideo (I think) problem.


can you post the output of 

```

~$ lspci -nn | grep -i vga

```

and

```

~$ uname -r

```

---

### Post by avacado on 2009-12-29
Dell Inspiron 1520 4GB RAM 250GB HDD
Karmic 9.10
My wifi stopped working suddenly and I have more or less isolated it to the physical 'WI-FI CATHCHER" switch on the side.
I changed the bios setting to 'ignore switch' and now it can disable wifi whether turned on or off after boot, and must be enabled in likewise fashion.
You can check the bios status using code
sudo rfkill -list

---

### Post by reiki on 2009-12-31
Dell Zino HD, AMD Neo X2 e6850, 8GB memory, 750GB hard drive, 512MB ATI HD4330 graphics card in MXM slot, DVDRW.
Karmic (9.10)

Everything worked out of the box except the rear analog sound jack. I had to have my speakers plugged into the front headphone jack. I bought a USB sound adapter until I can get that sorted out.

Zino HD is aabout 7.5" square footprint and 3 and a half inches tall. VERY ultra small form factor box and super quiet.

---

### Post by FirstByté on 2010-01-05
> **avacado said:**
> Dell Inspiron 1520 4GB RAM 250GB HDD
Karmic 9.10
My wifi stopped working suddenly and I have more or less isolated it to the physical 'WI-FI CATHCHER" switch on the side.
I changed the bios setting to 'ignore switch' and now it can disable wifi whether turned on or off after boot, and must be enabled in likewise fashion.
You can check the bios status using code
sudo rfkill -list

Thanks for the heads-up on this. You mentioned that you isolated it to the 'Wifi Catcher' button. Was this issue repeatable?

A more subtle 'wl' module fix was introduced in Karmic with the 

```
~$ sudo apt-get install bcmwl-kernel-source
```

and enabling backports at the Software Resources. 

However this may not be necessarily in your case as you reported that it worked before & that the button conflicts with its functionality.

---

