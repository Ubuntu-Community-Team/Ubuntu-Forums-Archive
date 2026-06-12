---
title: "radeon x1600 vesa driver can't get widescreen res"
date: 2006-03-28
forum: Desktop Environments
---

### Post by theFunkyDonkey on 2006-03-28
Hi! I have a brand new Toshiba A100-155 notebook equipped with Ati Radeon x1600 which as u may know isn't yet officially supported by ati and also by "radeon" or "ati" drivers of xorg. I managed a 1024x768 with the vesa driver on a Breezy 5.10 with xorg 6.8.2. I still can't get 1280x800 which is the actual res of my display. I created a custom modeline watching the xorg's log file but still can't get the wide res.

Here's my xorg.conf:

```

Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
#!Description "Toshiba Satellite Wide LCD Screen @ 60.25 Hz"
#!MaxRes 1280x800
Identifier "Generic Monitor"
HorizSync 31.5-100
VertRefresh 58-76
Option "DPMS"
Modeline "1280x800" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection 

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection


```

And that's the noticeable part of the xorg's log:

```

(II) VESA(0): Manufacturer: LPL  Model: 0  Serial#: 0
(II) VESA(0): Year: 2005  Week: 0
(II) VESA(0): EDID Version: 1.2
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) VESA(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 71.2 MHz   Image Size:  289 x 21 mm
(II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) VESA(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) VESA(0):  LGPhilipsLCD
(II) VESA(0):  LP154W01-TLA2

```

and then...

```

II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Generic Monitor: Using default hsync value of 49.48 kHz
(II) VESA(0): Generic Monitor: Using default vrefresh value of 60.12 Hz
(II) VESA(0): Not using mode "1280x1024" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0):  Built-in mode "1024x768"
(**) VESA(0):  Built-in mode "1024x768"
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0):  Built-in mode "720x400"
(**) VESA(0):  Built-in mode "640x400"
(**) VESA(0):  Built-in mode "640x400"
(**) VESA(0):  Built-in mode "640x350"
(--) VESA(0): Display dimensions: (330, 210) mm
(--) VESA(0): DPI set to (78, 92)
(**) VESA(0): Using "Shadow Framebuffer"


```


Thanks in advance, any help will be appreciated.

---

### Post by Teroedni on 2006-03-28
Hmm yor max at 1280x800 is 60hz right.
Therefore you need a modeline with 1280x800@60 or something similars


You may have specified that.
So if you have.



add
	```
SubSection "Display"
		Depth		24
		Modes		"1280x800_60" "1280x800"
	EndSubSection
EndSection
```

or if the above dont work

	```
SubSection "Display"
		Depth		24
		Modes		"1280x800@60" "1280x800"
	EndSubSection
EndSection
```

---

### Post by theFunkyDonkey on 2006-03-28
[QUOTE=Teroedni]Hmm yor max at 1280x800 is 60hz right.
Therefore you need a modeline with 1280x800@60 or something similars

add
	```
SubSection "Display"
		Depth		24
		Modes		"1280x800_60" "1280x800"
	EndSubSection
EndSection
```

or if the above dont work

	```
SubSection "Display"
		Depth		24
		Modes		"1280x800@60" "1280x800"
	EndSubSection
EndSection
```[/QUOTE]

I tried changing the Modes as you specified but nothing changes. I also tried modifying the modeline's name adding the @60 but I'm still stuck the same as above :-k

I'm not pretty sure about the frequency of my panel, I inserted 60 Hz in the modline generator, is there a way to understand the actual freq?

Anyway...thanks for the the quick reply ;)

---

### Post by Teroedni on 2006-03-28
a new modeline
Try it 

Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828



and also try with thoose 2 display modes on the new modeline generator.



If that fails to work
add this command to section device
```

Option “IgnoreEDID” “true
```

---

### Post by Hairy_Palms on 2006-03-28
if your screen is anything like mine, modelines alone wont work, use read-edid,
[http://john.fremlin.de/programs/linux/read-edid/](http://john.fremlin.de/programs/linux/read-edid/)
it should give you a whole new monitor section which you can replace it with and it will then have widewscreen fine.

---

### Post by theFunkyDonkey on 2006-03-30
[QUOTE=Hairy_Palms]if your screen is anything like mine, modelines alone wont work, use read-edid,
[http://john.fremlin.de/programs/linux/read-edid/](http://john.fremlin.de/programs/linux/read-edid/)
it should give you a whole new monitor section which you can replace it with and it will then have widewscreen fine.[/QUOTE]

First of all, thanks a lot for the support :KS.

I successfully started read-edid and had this output:

```

./get-edid | ./parse-edid
./get-edid: get-edid version 1.4.1

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 300
        VBE string at 0xc0248 "ATI ATOMBIOS"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
./parse-edid: parse-edid version 1.4.1
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination supports DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call successful

./parse-edid: EDID checksum passed.

        # EDID version 1 revision 2
Section "Monitor"
        # Block type: 2:0 3:0
        # Block type: 2:0 3:fe
        # Block type: 2:0 3:fe
        Identifier "LPL:0000"
        VendorName "LPL"
        ModelName "LPL:0000"
        # Block type: 2:0 3:0
        # Block type: 2:0 3:fe
        # Block type: 2:0 3:fe
        # DPMS capabilities: Active off:no  Suspend:no  Standby:no

        Mode    "1280x800"      # vfreq 60.120Hz, hfreq 49.479kHz
                DotClock        71.250000
                HTimings        1280 1328 1360 1440
                VTimings        800 802 808 823
                Flags   "-HSync" "-VSync"
        EndMode
        # Block type: 2:0 3:0
        # Block type: 2:0 3:fe
        # Block type: 2:0 3:fe
EndSection

```

Added then the new "correct" section to the xorg.conf and changed the references for the monitor's identifier but nothing changed :( 

That's what the log says:

```

(II) VESA(0): LPL:0000: Using default hsync value of 49.48 kHz
(II) VESA(0): LPL:0000: Using default vrefresh value of 60.12 Hz
**(II) VESA(0): Not using mode "1280x800" (no mode of this name)**
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0):  Built-in mode "1024x768"
(**) VESA(0):  Built-in mode "1024x768"
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0):  Built-in mode "720x400"
(**) VESA(0):  Built-in mode "640x400"
(**) VESA(0):  Built-in mode "640x400"
(**) VESA(0):  Built-in mode "640x350"

```

---

### Post by theFunkyDonkey on 2006-04-04
Just an update for my scenario... Upgraded to Dapper Drake to have xorg's latest version but nothing changed ](*,)

---

### Post by e00878 on 2006-04-06
No one can run linux on brandnew ati x1600-x1800 series video card. Looks like Microsoft and ATI have good deal!

---

### Post by theFunkyDonkey on 2006-04-10
[QUOTE=e00878]No one can run linux on brandnew ati x1600-x1800 series video card. Looks like Microsoft and ATI have good deal![/QUOTE]

Yes I know but I'm trying to get the best from the vesa driver. There are people who report this driver to work also with 1280x800 resolution, all I get is a standard 1024x768 right now :mad:

---

### Post by theFunkyDonkey on 2006-04-18
Ati finally released the official driver for this card... :D 

Check out this 3d:

[http://www.ubuntuforums.org/showthread.php?t=159233&highlight=x1600]("http://www.ubuntuforums.org/showthread.php?t=159233&highlight=x1600")

---

