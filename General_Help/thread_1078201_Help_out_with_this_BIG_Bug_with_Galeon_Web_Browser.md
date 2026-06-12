---
title: "Help out with this BIG Bug with Galeon Web Browser!"
date: 2009-02-23
forum: General Help
---

### Post by Saurabhdua on 2009-02-23
Guys!!

If anyone has ever used Galeon Web Browser? As soon as I tried to "Customize" the Toolbar to add the "New Tab" button with Drag-n-Drop, whole system got STRUCK!...or what you call as System Freeze! It got in such to such an extent that I have to press the POWER Button to make a FORCEFUL Shutdown of the system!!

I replicated the whole thing to see the same result!...Any fixes??

---

### Post by orethrius on 2009-02-23
I'm looking at 2.0.6 right now.  What are the exact steps you followed to get this result?

---

### Post by Saurabhdua on 2009-02-23
O..O..My version for Galeon is 2.0.4. I wonder, why hasn't it got updated as of yet?!
I couldn't see any separate "Check for Update" option within any menu. It should have been done by Repository update only..Isn't it?

---

### Post by orethrius on 2009-02-23
It may have been fixed in Ibex (8.10).  Please post the contents of the version.log that will be created on your desktop after running the following (hold Alt and hit F2, type **gnome-terminal**, and hit enter; you can paste from the menu bar, or use Shift-Ctrl-V).

```
cat /boot/grub/menu.lst | grep recovery | grep \`uname -r\` | awk -F, '{print $1}' > ~/Desktop/version.log
```

---

### Post by Saurabhdua on 2009-02-23
Hi There!!

It is coming up with grep: invalid option --- 

& hence version.log is blank!

---

### Post by orethrius on 2009-02-23
My bad, I thought I removed all the backslashes.  Let's try this again.

```
cat /boot/grub/menu.lst | grep recovery | grep `uname -r` | awk -F, '{print $1}' > ~/Desktop/version.log
```

What does that return for version.log?

---

### Post by Saurabhdua on 2009-02-23
Hi again Orethrius!

This time it worked well to come up with:

title		Ubuntu 8.04.2

---

### Post by orethrius on 2009-02-23
I picked up the 2.0.4 release before going to bed last night, I'll test it in a bit.

Incidentally, you're running Hardy Heron (8.04) as indicated by that result.  There's probably a way I could parse that out more reliably with another awk command, but now we (you and I) know what version you have.

Update #1: I'm pulling in the 8.04 ISO from Oregon State University.  I should have it downloaded in about one hour, and a test worked out in a Virtual Machine within the next few hours.

---

### Post by DagMan on 2009-02-23
> **orethrius said:**
> There's probably a way I could parse that
cat /etc/lsb-release

Didn't know that for ages myself.

---

### Post by orethrius on 2009-02-23
ACK thanks, I knew I forgot something like that! :)

---

### Post by Saurabhdua on 2009-02-24
So Dear!!

Did the test work fine for you? Iam really glad that u are putting in an earnest effort to scour this thing!

Iam waiting to say "JAI HO" after we'll reach on to something crucial!...am from India!

---

### Post by orethrius on 2009-02-24
Yes, sorry for the delay, I've been doing quite a few other things as well.  I have the install of 8.04 running in a backgrounded VM and should have an answer for you shortly.

UPDATE: Very strange.  It seems to work in an i386 VM running 8.04, and Galeon 2.0.4.

Would you mind running the below in a terminal (as before, Alt+F2 then gnome-terminal and enter) and posting the contents of config.log?

```
cat /etc/lsb-release > ~/Desktop/config.log; echo >> ~/Desktop/config.log; cat /proc/cpuinfo >> ~/Desktop/config.log; echo >> ~/Desktop/config.log; lspci >> ~/Desktop/config.log
```

(Thanks to DagMan for remembering /etc/lsb-release!)

---

### Post by Saurabhdua on 2009-02-24
Sorry Dear!!

For delay at my end..going a bit casual now..!! Please do not "Kill Me", if I tell you at this stage  that I have been using Ubuntu within Windows like any other Software application.On getting my FREE CD, I preferred to install Ubuntu "Inside Windows"...Excuse me, if this uncover spoilt your enthu.

Anyways, here goes the thing you have asked for:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 1
model name	: Intel(R) Pentium(R) 4 CPU 1.90GHz
stepping	: 2
cpu MHz		: 1904.429
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
bogomips	: 3812.86
clflush size	: 64


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet Controller (rev 81)

---

