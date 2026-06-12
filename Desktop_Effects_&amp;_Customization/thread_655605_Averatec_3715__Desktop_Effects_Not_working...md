---
title: "Averatec 3715 / Desktop Effects Not working.."
date: 2008-01-01
forum: Desktop Effects &amp; Customization
---

### Post by Spitphire on 2008-01-01
Unable to enable desktop effects (System->Preferences->Appearance->Visual Effects)
              "Desktop effects could not be enabled"

Not sure what I'm doing wrong here's some info:

```
am@lp:~$ uname -a
Linux lp 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

```

```
am@lp:~$ lspci |grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

```

/etc/X11/xorg.conf:
```

Section "Device"
        Identifier      "Generic Video Card"
        BoardName   "via"
        VendorName  "VIA Tech"
        Driver "via"
        Option "DisableIRQ"
EndSection

```

compiz
```

am@lp:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "pixmap",
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "pixmap",
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "pixmap",
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "pixm
```

```

am@lp:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 44
model name      : Mobile AMD Sempron(tm) Processor 3000+
stepping        : 2
cpu MHz         : 1800.000
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
bogomips        : 3612.68
clflush size    : 64

```

---

### Post by Ub1476 on 2008-01-01
I believe your card is [blacklisted]("http://ubuntuforums.org/showthread.php?t=582112"). Might be the latest driver from VIA is working alright thought.

---

### Post by Spitphire on 2008-01-02
compiz doesn't report that it's blacklisted (compiz shoudl report "you have a blacklisted driver"... or something along thos elines), just says that i don't have a whitelisted driver, is there a different driver i should be looking for - besides the VIA?  

Maybe someone out there has some experience with and Averatec 3715...... Or maybe I'm a rambling idiot.. just need some assistance here.

Thanks.

---

### Post by Ub1476 on 2008-01-02
You can also check if it's blacklisted by running:

```
SKIP_CHECKS=yes compiz
```

This won't do any changes to the compiz configuration files.

If it has no effect you may want to try to install XGL. It's available in Synaptic (GUI) or:

```
sudo apt-get install xserver-xgl
```

Logout and login.

---

### Post by Spitphire on 2008-01-02
Ok, I'll give it a shot and let you know how it turns out, thank you very much.

---

