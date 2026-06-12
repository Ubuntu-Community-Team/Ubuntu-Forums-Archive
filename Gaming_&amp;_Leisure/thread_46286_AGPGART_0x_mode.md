---
title: "AGPGART 0x mode"
date: 2005-07-04
forum: Gaming &amp; Leisure
---

### Post by c0rN_g0aT on 2005-07-04
Ok I love RMS and all but I went ahead and installed the Binary only nvidia driver.  I used the apt method in the howto ;)

I have a AGP 3.0 (4x/8x) geforce fx 5200 plugged into a AGP 2.0 slot (2x/4x).  The card should work just fine with the 1.5v instead of 0.8v and it does.  It works, and I can even play 3d games etc....

However its a little slugish.

here is my cat /proc/driver/nvidia/agp/host-bridge

#############################################
Host Bridge:     VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x]
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       2x 1x
Registers:       0x1f000213:0x00000100
#############################################

??? its a 4x/8x card in a 4x slot ???
I checked the BIOS and everthing is set correctly

My /etc/modutils/nvidia-kernel-nkc reads

#############################################
alias char-major-195
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_ReqAGPRATE=2
#############################################

and i put Option  "AGPMode" "2x" in my xorg.conf

here is what dmesg gives me

#############################################
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
#############################################

it happens every single time!!!
I set xorg.conf and the modutils stuff to 4x and I still get the same stuff about 0x mode

here is my cat /proc/driver/nvidia/agp/status

#############################################
Status:          Enabled
Driver:          AGPGART
AGP Rate:        0x
Fast Writes:     Disabled
SBA:             Disabled
#############################################

recap-------
AGP 4x, SBA and Fast Writes are all set correctly in the BIOS
Host-Bridge says that SBA and FW are supported and for some reason lists my 4x8x card as 1x2x

I can't for the love of god get anything but 0x outta my card

Please help!

P.S.  I tried using the nvAGP "1" but it wouldn't load because AGPGART was already loaded :(

---

### Post by Lord Illidan on 2005-07-04
Run glxgears..How many fps can u get?

---

### Post by c0rN_g0aT on 2005-07-04
With the terminal in one corner of the screen and the glxgears window in the other (standard size) I get an average of about 2850fps.

If i maximize the glxgears window, my average drops to around 400fps.

Again my card is a ASUS GeForce FX 5200 with 128mb of ram

---

### Post by Teren on 2005-07-04
[QUOTE=c0rN_g0aT]With the terminal in one corner of the screen and the glxgears window in the other (standard size) I get an average of about 2850fps.

If i maximize the glxgears window, my average drops to around 400fps.

Again my card is a ASUS GeForce FX 5200 with 128mb of ram[/QUOTE]
 Isn't 2850fps very good for a FX5200?

---

### Post by t2kburl on 2005-07-04
I have a 5200 and I've never seen over 2500 fps

---

### Post by Lord Illidan on 2005-07-04
Forget about the 0x mode..try and run some opengl games..if they work satisfactorily...then you are fine!

---

### Post by c0rN_g0aT on 2005-07-05
I can play A Tale In The Dessert (ATITD) on the highest settings with a few dropped frames here and there.  So even if we can't get it fixed I will be ok.

With that said......

I hate typing dmesg and seeing AGPGART setting my card up in 0x mode and aparently completely disregarding the SBA and FW stuff.  Its like having a spotless wine glass with one big greasy fingerprint on it.  Unless two different methods of checking (see first post) are reporting incorrectly, my card is running in 0x mode which I am assuming is regular PCI speed.

More Info on my PC

ABIT VP6 MoBo with Dual PIII 933Mhz and 2GB PC 133 ram
Via Apollo chipset

I guess what I want to here is "its a know issue there is nothing you can do" *or* "thats an easy one here is what you do to fix it".

Thanks guys :)

---

### Post by citizenr on 2006-07-09
sudo gedit /etc/modprobe.d/blacklist

append at the end

blacklist agpgart
blacklist via_agp


and NO mate, your host-bridge is AGP x2, not x4 

>P.S. I tried using the nvAGP "1" but it wouldn't load because AGPGART was already loaded 

try now, you must have 1 for nvagp to load, it will now that agpgart is blacklisted

---

