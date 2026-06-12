---
title: "Sticky mouse pointer"
date: 2006-01-02
forum: Desktop Environments
---

### Post by RetroFreak on 2006-01-02
Hi all,

I've installed Breezy on a Samsung GT-8000 laptop (PIII 650) with a 3Com 54g card. All works well, except that the mouse pointer will get stuck on the screen for a second then suddenly jump over to where it should be. This makes it very tricky to navigate and accuratley click on things. I've a feeling it sticks while it's accessing the HD. I did a clean server install, then added Gnome afterwards, but it still had the same problem, but not as often (not as much software installed so it was accessing the HD less?) 

I've installed Ubuntu on a similarly specced Toshiba laptop (in fact it was slower, a 600mhz Celeron) without any problems.

Any ideas?

TIA

---

### Post by new2lnx on 2006-01-02
[QUOTE=RetroFreak]Hi all,

I've installed Breezy on a Samsung GT-8000 laptop (PIII 650) with a 3Com 54g card. All works well, except that the mouse pointer will get stuck on the screen for a second then suddenly jump over to where it should be. This makes it very tricky to navigate and accuratley click on things. I've a feeling it sticks while it's accessing the HD. I did a clean server install, then added Gnome afterwards, but it still had the same problem, but not as often (not as much software installed so it was accessing the HD less?) 
TIA[/QUOTE]

Mine is a compaqnx9040 laptop with a usb mouse and a touchpad.  I noticed the past few days that the mouse pointer would get stuck for a minute or sometimes longer with the usb mouse so i have to use the touchpad to move the mouse pointer around.

I appreciate help on this.

---

### Post by ysse on 2006-01-02
Just a thought, RetroFreak: is DMA on for your drive? hdparm -i /dev/hda will tell you.

---

### Post by RetroFreak on 2006-01-03
I shall have a looksee. I've got Win 98 on it at the mo (I know, I know, but it's the only OS so far where everything on the laptop works OK!), so I'm going to ghost the drive then put Ubuntu back on. Hopefully do that tomorrow!

---

### Post by rahz on 2006-01-03
Also, can you post the contents of  /usr/share/powernowd/cpufreq-detect.sh

cheers

---

### Post by RetroFreak on 2006-01-07
[QUOTE=ysse]Just a thought, RetroFreak: is DMA on for your drive? hdparm -i /dev/hda will tell you.[/QUOTE]

That gives this:

 Model=TOSHIBA MK4026GAX, FwRev=PA102D, SerialNo=X5OC8766T
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=48
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=off
 CurCHS=17475/15/63, CurSects=16513875, LBA=yes, LBAsects=78140160
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: device does not report version:

 * signifies the current active mode

So UDMA 2 is on.

---

### Post by RetroFreak on 2006-01-07
[QUOTE=rahz]Also, can you post the contents of  /usr/share/powernowd/cpufreq-detect.sh

cheers[/QUOTE]

Here it is:

#! /bin/bash

if /usr/sbin/laptop-detect; then LAPTOP=1; fi
CPUINFO=/proc/cpuinfo
IOPORTS=/proc/ioports

if [ ! -f $CPUINFO ] ; then
    echo $CPUINFO not detected... >2
    exit 1
fi

MODEL_NAME=`grep '^model name' "$CPUINFO" | head -1 | sed -e 's/^.*: //;'`
CPU=`grep -E '^cpud[^:]+:' "$CPUINFO" | head -1 | sed -e 's/^.*: //;'`
VENDOR_ID=`grep -E '^vendor_id[^:]+:' "$CPUINFO" | head -1 | sed -e 's/^.*: //;'`
CPU_FAMILY=$(sed -e '/^cpu family/ {s/.*: //;p;Q};d' $CPUINFO)

MODULE=none
MODULE_FALLBACK=acpi-cpufreq

# Two modules for PIII-M depending the chipset.
# modprobe speedstep-ich$EXT || modprobe speestep-smi$EXT  would be another way
if [ -f $IOPORTS ] && grep -q 'Intel .*ICH' $IOPORTS ; then
  PIII_MODULE=speedstep-ich
else
  PIII_MODULE=speedstep-smi
fi

case "$VENDOR_ID" in
    GenuineIntel*)
    # If the CPU has the est flag, it supports enhanced speedstep and should
    # use the speedstep-centrino driver
    if [ "`grep est $CPUINFO`" ]; then
	MODULE=speedstep-centrino;
    elif [ $CPU_FAMILY = 15 ]; then
    # Right. Check if it's a P4 without est.
	# Could be speedstep-ich, or could be p4-clockmod. 
	MODULE=speedstep-ich;
	# Disabled for now - the latency tends to be bad enough to make it
	# fairly pointless. 
	# echo "FREQDRIVER=p4-clockmod" >/etc/default/powernowd
	# to override this
#	if [ $LAPTOP = "1" ]; then
#	    MODULE_FALLBACK=p4-clockmod;
#	fi
    else
    # So it doesn't have Enhanced Speedstep, and it's not a P4. It could be 
    # a Speedstep PIII, or it may be unsupported. There's no terribly good
    # programmatic way of telling.
	case "$MODEL_NAME" in
	    Intel\(R\)\ Pentium\(R\)\ III\ Mobile\ CPU*)
	    MODULE=$PIII_MODULE ;;
	    
        # JD: says this works with   cpufreq_userspace
	    Mobile\ Intel\(R\)\ Pentium\(R\)\ III\ CPU\ -\ M*)
	    MODULE=$PIII_MODULE ;;
	    
        # [https://bugzilla.ubuntu.com/show_bug.cgi?id=4262](https://bugzilla.ubuntu.com/show_bug.cgi?id=4262)
        # UNCONFIRMED
	    Pentium\ III\ \(Coppermine\)*)
	    MODULE=$PIII_MODULE
	    ;;
	esac
    fi
    ;;
    AuthenticAMD*)
    # Hurrah. This is nice and easy.
    case $CPU_FAMILY in
	5)
	# K6
	MODULE=powernow-k6
	;;
	6)
	# K7
	MODULE=powernow-k7
	;;
	15)
	# K8
	MODULE=powernow-k8
	;;
    esac
    ;;
    CentaurHauls*)
    # VIA
    if [ $CPU_FAMILY == 6 ]; then
	MODULE=longhaul;
    fi
    ;;    
    GenuineTMx86*)
    # Transmeta
    if [ "`grep longrun $CPUINFO`" ]; then
	MODULE=longrun
    fi
    ;;    
esac

Thanks

---

### Post by RetroFreak on 2006-01-23
Ah ha! Turned off 32bit disk access in the BIOS and all is well! Odd that, must be a driver conflict or something, as it also did it in Kubuntu, but not with Slackware. Still sorted now, should hve tried that sooner :/

---

### Post by rahz on 2006-01-23
You might want to change this:

> # Two modules for PIII-M depending the chipset.
# modprobe speedstep-ich$EXT || modprobe speestep-smi$EXT would be another way
if [ -f $IOPORTS ] && grep -q 'Intel .*ICH' $IOPORTS ; then
PIII_MODULE=speedstep-ich
else
PIII_MODULE=speedstep-smi
fi

to this:

> # Two modules for PIII-M depending the chipset.
# modprobe speedstep-ich$EXT || modprobe speestep-smi$EXT would be another way
if [ -f $IOPORTS ] && grep -q 'Intel .*ICH' $IOPORTS ; then
PIII_MODULE=speedstep-ich
else
# PIII_MODULE=speedstep-smi
PIII_MODULE=speedstep_ich
fi

and do a reboot.

that fixes it for everyone I've seen have the problem.

Sorry for the delayed response too.

---

### Post by RetroFreak on 2006-01-23
Ta for that I'll give it a try :) Not noticed any performance drops since turning off the 32 bit access though, but the HD is much newer than the laptop.

Cheers

---

### Post by RetroFreak on 2006-02-07
Finally got round to doing this and it's done the trick. Again no performance changes either way.

Thanks :)

---

### Post by juancnuno on 2006-02-19
Hey rahz,

Was the underscore in PIII_MODULE=speedstep_ich intentional?  Did you really mean PIII_MODULE=speedstep-ich?  I'm going to use the dash to see if it fixes the mouse issues I'm having with my laptop.

I'm going to change this:
```

# Two modules for PIII-M depending the chipset.
# modprobe speedstep-ich$EXT || modprobe speestep-smi$EXT  would be another way
if [ -f $IOPORTS ] && grep -q 'Intel .*ICH' $IOPORTS ; then
  PIII_MODULE=speedstep-ich
else
  PIII_MODULE=speedstep-smi
fi

```
to this:
```

# Two modules for PIII-M depending the chipset.
# modprobe speedstep-ich$EXT || modprobe speestep-smi$EXT  would be another way
# if [ -f $IOPORTS ] && grep -q 'Intel .*ICH' $IOPORTS ; then
#   PIII_MODULE=speedstep-ich
# else
#   PIII_MODULE=speedstep-smi
# fi

PIII_MODULE=speedstep-ich

```

---

### Post by rahz on 2006-02-19
It was intentional.

Changing it to this:

# Two modules for PIII-M depending the chipset.
# modprobe speedstep-ich$EXT || modprobe speestep-smi$EXT would be another way
if [ -f $IOPORTS ] && grep -q 'Intel .*ICH' $IOPORTS ; then
PIII_MODULE=speedstep-ich
else
# PIII_MODULE=speedstep-smi
PIII_MODULE=speedstep_ich
fi

following a reboot, should fix the problem. If you look closely, the change you suggested is already there, which you comment out to then fix it. That's what's causing the bug, and you'd be putting the same problem there twice

---

### Post by juancnuno on 2006-02-19
Alright rahz, thanks.  Just wanted to make sure.

Everyone ignore my previous post!

---

### Post by RetroFreak on 2006-02-20
That's interesting, as I assumed it was a typo so left it as a - , yet it still solved the problem :/

I'll go change it again and see what happens :)

---

### Post by juancnuno on 2006-02-20
Tried it with the dash and the underscore, didn't solve my problem.  Which is my cursor jumps erratically, albeit occasionally, when I'm mousing on my laptop.  The mouse is an external USB one plugged in.

Maybe this [other thread]("http://ubuntuforums.org/showthread.php?t=132064") might help.

---

### Post by johnnybirdman on 2008-02-25
> **rahz said:**
> You might want to change this:
to this:
and do a reboot.
.

Thanks for this.  It stopped the studdering mouse (touchpad or mouse) on my old Dell CPxJ that just got loaded with 7.10
J.

---

