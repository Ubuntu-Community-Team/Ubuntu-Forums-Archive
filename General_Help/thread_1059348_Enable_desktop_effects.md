---
title: "Enable desktop effects"
date: 2009-02-03
forum: General Help
---

### Post by Mavro on 2009-02-03
I've been trying to enable the desktop effects, but it wont work....
I get this message both when I try normal and Extra: "Desktop effects could not be enabled"
And when i go to Hardware drivers, no drivers are listed. 
I've just updated to 8.10 from 8.04.
Any ideas to what I should do?:D

thanks, Mavro

---

### Post by 2hot6ft2 on 2009-02-03
You could install envy and use it to install the graphics driver. Assuming that it's a real install and not a wubi install go to
Applications>Accessories>Terminal
and use
```
sudo apt-get install envy-ng
```
then it will be in
Applications>System Tools>EnvyNG
and you can use it to install the graphics driver.

Since you gave no system info like graphics card info or install type that's the best solution I can offer at this point.

---

### Post by Mavro on 2009-02-04
Okay i'll try that then. 
thank you:D

---

### Post by lakersforce on 2009-02-04
Hold on a minute!

Do a lspci  at terminal and paste it here.

---

### Post by Mavro on 2009-02-04
what's that? and how do i do that?
I'm a bit of a newbie:P

---

### Post by lakersforce on 2009-02-04
It's in the gnome menu somewhere. You basicly need a good old commandline and at it type: lspci

---

### Post by Mavro on 2009-02-04
okay, now i've done that, and it says:

simeon@simeon-laptop:~$ Ispci
bash: Ispci: command not found
simeon@simeon-laptop:~$

---

### Post by lakersforce on 2009-02-04
copy-paste this: lspci

---

### Post by Mavro on 2009-02-04
Okay, that worked a little bit better:)

```
simeon@simeon-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
simeon@simeon-laptop:~$ 
```

---

### Post by lakersforce on 2009-02-04
The advice in post #2 definitely will no help you, as you don't have an nvidia card.

If you write this at commandline:
```
glxinfo | grep direct
```
you should get this answer: "Direct rendering: Yes"

If that's the case, then it's just a matter of enabling the effects (although they should be enabled by default). Check for options in the System menu.

You might want to install the "compiz" package to enable a world of graphical customization.

---

### Post by Mavro on 2009-02-04
Okay, did that and got:

```
simeon@simeon-laptop:~$ glxinfo | grep direct
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
simeon@simeon-laptop:~$ 
```

Btw. I got compiz installed, and everything worked fine before I updated to 8.10.
And when I go to System>Administration>Hardware drivers, It does not display any drivers at all, like it used to when i was using 8.04.

---

### Post by Mavro on 2009-02-04
Also I ran the Compiz-Check and got this:

```
simeon@simeon-laptop:~$ wget http://blogage.de/files/9124/download -O compiz-check
--2009-02-04 10:09:41--  http://blogage.de/files/9124/download
Resolving blogage.de... 78.46.34.206
Connecting to blogage.de|78.46.34.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/octet-stream]
Saving to: `compiz-check'

    [ <=>                                   ] 28,360      --.-K/s   in 0.03s   

2009-02-04 10:09:42 (1.01 MB/s) - `compiz-check' saved [28360]

simeon@simeon-laptop:~$ chmod +x compiz-check
simeon@simeon-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

---

### Post by lakersforce on 2009-02-04
Looks like the upgrade broke your X server. That's very common, and the sole reason that you should never upgrade but always re-install. Unfortunately there's not a easy fix. But it might help to boot up your computer in Ubuntu recovery mode and try the "xfix" option. If it does not help you have 4 choices: 1) get a linux guru to sit in front of your screen and fix it for you 2) fix it yourself 3) search forums 4) reinstall ubuntu.

If you choose option 4, don't forget to make a /home partition (if you have not already), so that you will not use loose personal data next time Ubuntu ***** -up.

---

### Post by Mavro on 2009-02-04
Okay, thank you ever so much:)

---

### Post by jordan.exe on 2009-02-26
i have the exact same problem, except i flashed my drives before freshly installing ubuntu 8.10. 

i tried the xfix. dont think it worked.

could u give me step by step on how to fix it. I would rather not have to reinstall everything and I dont really know any linux masters

---

