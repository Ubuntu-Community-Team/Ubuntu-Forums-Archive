---
title: "Dapper CPU Scaling on a Desktop"
date: 2006-06-05
forum: Desktop Environments
---

### Post by xice on 2006-06-05
Hi guys
it seems that my PC is having its CPU scaled by Dapper 6.06

Is this just AMD Cool and Quiet? and Can i turn it off?

```
ben@xice:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 47
model name      : AMD Athlon(tm) 64 Processor 3000+
stepping        : 0
cpu MHz         : 1007.582
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 2016.37

```

---

### Post by Sutekh on 2006-06-05
Yes you should be able to turn off Cool 'n' Quiet from your BIOS.

You can also stop the powernow daemon in Ubuntu (controls frequency scaling)
```
sudo /etc/init.d/powernowd stop
``` Not yet sure how you can disable the service, powernow will start again upon reboot.  I know it can be done, but haven't found the information yet.

You can also add a frequency scaling applet to control the frequency if you want.  If you right-click a panel and choose Add to Panel, you can find the frequency scaling applet.

---

### Post by xice on 2006-06-05
ok thanks, i found out its not a too badder thing to have anyway

---

### Post by Sutekh on 2006-06-05
No I agree its not too bad a thing.  I really like the frequency scaling on my AMD X2, its quite responsive.

---

