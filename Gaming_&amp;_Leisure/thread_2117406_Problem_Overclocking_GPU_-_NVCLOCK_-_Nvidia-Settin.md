---
title: "Problem Overclocking GPU - NVCLOCK - Nvidia-Settings"
date: 2013-02-18
forum: Gaming &amp; Leisure
---

### Post by TheNoobyPro on 2013-02-18
I wasn't sure whether to post this in Hardware or Gaming... But anyways, here's my problem.

I am able to overclock my Core Clock Speed in Nvidia-Settings, but if I move the Memory Clock slider, it says "Failed to overclock!" ( Now this is a problem because your memory clock is what really determines performance ](*,) )  

I can "attempt" to overclock in NVCLOCK, I haven't tried OCing just the Core Clock in NVCLOCK though, I used:
```
nvclock -b coolbits -n 565 -m 700
``` but then it said "Failed to mmap PMC"

I've also got the latest Nvidia Binary drivers. I'm fairly new to Linux, so I don't know how to go about solving this problem. Any help is appreciated :D


The GPU is GeForce 7300 LE
Ubuntu 12.04 LTS 32-bit


EDIT: If it helps, I was able to overclock on Windows XP 32-bit

---

### Post by gordintoronto on 2013-02-18
Have you tried changing the Power Mizer setting in NVIDIA X Server Settings to "prefer maximum performance"?

You might also try:
sudo nvclock ....

I hope you plan to keep an eye on the temperature of the card! Mind you, destroying a seven-year-old video card is not the end of the world.

---

### Post by TheNoobyPro on 2013-02-18
> **gordintoronto said:**
> Have you tried changing the Power Mizer setting in NVIDIA X Server Settings to "prefer maximum performance"?

You might also try:
sudo nvclock ....

I hope you plan to keep an eye on the temperature of the card! Mind you, destroying a seven-year-old video card is not the end of the world.

Well, I did it with Sudo and set the PowerMizer to "prefer maximum performance", and now I've gotten a different error.  
> Requested memory clock:     700.000 MHz
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (NV-CONTROL)
  Minor opcode of failed request:  3 ()
  Value in failed request:  0x17
  Serial number of failed request:  15
  Current serial number in output stream:  15
But I'm not quite sure I typed the NVCLOCK code correctly. I typed ```
sudo nvclock -f -b coolbits -n 565 -m 700

```Also, I won't burn up the GPU, I replaced the heatsink with a fan/heatsink, combo :P

EDIT: Still cant OC memory clock with nvidia-settings

---

### Post by sdowney717 on 2013-04-24
I really wish I could overclock this 6150 gpu using nvclock. 

errors and roadblocks everywhere
so what is the secret your holding back to make it work?

notice these really bogus numbers under current?
```
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ sudo nvclock -sCard: 		nVidia Geforce Go 6150
Card number: 	1
Mode		GPU Clock	Memory Clock
Coolbits 2D: 	100.000 MHz	532.000 MHz
Coolbits 3D: 	425.000 MHz	532.000 MHz
Current: 	-2147483.750 MHz	-2147483.750 MHz
```

```
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ sudo nvclock_gtk

(nvclock_gtk:3942): Gdk-CRITICAL **: IA__gdk_draw_drawable: assertion `GDK_IS_DRAWABLE (src)' failed
The program 'nvclock_gtk' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 53 error_code 2 request_code 156 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ sudo nvclock_gtk

(nvclock_gtk:3993): Gdk-CRITICAL **: IA__gdk_draw_drawable: assertion `GDK_IS_DRAWABLE (src)' failed
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ sudo nvclock_qt
Warning using experimental NV4x lowlevel clock adjustment, if you encounter strange issues, issue a bugreport.
register=0x4000, clockIn=13107000, calculated=-2147483648
PLL=0xc0000033, PLL2=00000000
NVPLL_COEFF: c0000033
NVPLL2_COEFF: 00000000
Warning using experimental NV4x lowlevel clock adjustment, if you encounter strange issues, issue a bugreport.
register=0x4020, clockIn=0, calculated=-2147483648
PLL=0xa000011c, PLL2=00000000
MPLL_COEFF: a000011c
MPLL2_COEFF: 00000000
MPLL_COEFF=00000000
MPLL2_COEFF=00000000
m1=0 m2=0 n1=0 n2=0 p=0
NVPLL_COEFF=c0000033
NVPLL2_COEFF=00000000
m1=0 m2=0 n1=0 n2=0 p=0
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ nvclock -n [new core mhz] -m [new memory mhz] -f 
Error: failed to mmap PMC
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ nvclock -n 130 -m 600 -f Error: failed to mmap PMC
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ sudo nvclock -n 130 -m 600 -f 
Requested memory clock: 	600.000 MHz
Requested core clock: 		130.000 MHz
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  156 (NV-CONTROL)
  Minor opcode of failed request:  3 ()
  Value in failed request:  0x17
  Serial number of failed request:  15
  Current serial number in output stream:  17
dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ sudo nvclock -sCard: 		nVidia Geforce Go 6150
Card number: 	1
Mode		GPU Clock	Memory Clock
Coolbits 2D: 	100.000 MHz	532.000 MHz
Coolbits 3D: 	425.000 MHz	532.000 MHz
Current: 	-2147483.750 MHz	-2147483.750 MHz

dv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ sudo nvclock -n 130 -m 600 -f -b coolbits
Requested memory clock: 	600.000 MHz
Requested core clock: 		130.000 MHz
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  156 (NV-CONTROL)
  Minor opcode of failed request:  3 ()
  Value in failed request:  0x17
  Serial number of failed request:  15
  Current serial number in output stream:  17
^Cdv9000@dv9000-HP-Pavilion-dv9000-EZ452UA-ABA:~$ 
```

---

### Post by sdowney717 on 2013-04-24
the gpu is overclockable in windows 7 using msi afterburner

---

