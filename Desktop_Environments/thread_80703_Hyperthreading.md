---
title: "Hyperthreading"
date: 2005-10-22
forum: Desktop Environments
---

### Post by VR6Pete on 2005-10-22
It doesnt seem to be detected/enabled by default in 5.10... is there any way of telling if it's been detected? How do I go about enabling it, I understand that most people dont like HT, but I fancy having a play with it. Any help is most welcomed.

Thanks,

Pete

---

### Post by thumbsoup on 2005-10-22
I am a newbie to Ubunto, but I saw a couple posts elsewhere about this, in case it helps.  At least you can try searching using terms from these posts.

1) ...to enable hyperthreading.....if the kernel of your distro supports it and your processor can do it.....
change this in your grub line or lilo
acpi=ht"

Post from Sept 2005:
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=367154](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=367154)

2) "You need to enable SMP, and also ACPI CPU Enumeration... either
CONFIG_ACPI_HT_ONLY or CONFIG_ACPI_PROCESSOR. In the former case, you
may also need to use the boot parameter "acpismp=force". If memory
serves, it's no longer required as of 2.4.22. "

Post from 2003: 
[http://linux.derkeiler.com/Mailing-Lists/Debian/2003-09/4973.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2003-09/4973.html)

---

### Post by dbott67 on 2005-10-22
Can you post the output of your **/proc/cpuinfo** file?  Type in **cat /proc/cpuinfo** at a terminal:
```
dbott@breezy:/proc$ cat cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 5
model name      : Pentium II (Deschutes)
stepping        : 2
cpu MHz         : 299.970
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr
bogomips        : 591.87
```
I believe there should be 2 instances of your CPU (0 & 1).

-Dave

---

### Post by VR6Pete on 2005-10-22
I've noticed that only the server install installs SMP kernel by default (if it's detected)... I've now installed kernel-smp:

Linux ubuntu 2.6.12-9-686-smp #1 SMP

cat /proc/cpuinfo now shows 2 CPU's :)

pete@ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 4
cpu MHz         : 3330.351
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid  xtpr
bogomips        : 6602.75

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 4
cpu MHz         : 3330.351
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid  xtpr
bogomips        : 6651.90

pete@ubuntu:~$



That should be about it shouldnt it?

---

### Post by dbott67 on 2005-10-22
Well. I would say so, as it looks like the OS sees it.

Of course, I'm just limping along on this little old P2-300, so you'll have to excuse me if my jealosy gets in the way of offering you any real assistance! :)

-Dave

---

### Post by VR6Pete on 2005-10-22
No worries dave :)

I've been using Linux since I was 13 - God knows why I didnt forgot that smp kernel had to be installed. perhaps overlooked it as most distro's would install or promt you to install the relevant kernel during install :)

---

### Post by bluck on 2005-10-22
[QUOTE=VR6Pete]I've noticed that only the server install installs SMP kernel by default (if it's detected)... I've now installed kernel-smp:

Linux ubuntu 2.6.12-9-686-smp #1 SMP

cat /proc/cpuinfo now shows 2 CPU's :)

pete@ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 4
cpu MHz         : 3330.351
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid  xtpr
bogomips        : 6602.75

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 4
cpu MHz         : 3330.351
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid  xtpr
bogomips        : 6651.90

pete@ubuntu:~$



That should be about it shouldnt it?[/QUOTE]


looks good.
the two cpu's means hyperthreading is working for you.   unless of course you have two physical cpu's capable of hyperthreading ;)

---

### Post by VR6Pete on 2005-10-22
[QUOTE=bluck]looks good.
the two cpu's means hyperthreading is working for you.   unless of course you have two physical cpu's capable of hyperthreading ;)[/QUOTE]

I'm not that lucky :)

---

### Post by fezzik on 2005-10-25
Hyperthreading was way too slow when got the 686smp.  Switched to 686 instead.  Much faster than 386 and none of the problems of 686smp.

---

### Post by aev on 2005-11-05
well... First thanks for the "cat /proc/cpuinfo" idea. 

I installed the Linux ubuntu 2.6.12-9-686-smp and I see two processors - "0" and "1"

Then I did test with the Pi calcualtion for 20 significant digits for both "smp" and "normal" kernel - NO difference at all in the calculation times.

---

### Post by dbott67 on 2005-11-05
[QUOTE=aev]well... First thanks for the "cat /proc/cpuinfo" idea. 

Then I did test with the Pi calcualtion for 20 significant digits for both "smp" and "normal" kernel - NO difference at all in the calculation times.[/QUOTE]

You're welcome!

By the way, what program or command did you use to calculate Pi to 20 significant digits?

-Dave

---

### Post by riggsd on 2005-11-05
[QUOTE=aev]Then I did test with the Pi calcualtion for 20 significant digits for both "smp" and "normal" kernel - NO difference at all in the calculation times.[/QUOTE]

You will only see a difference on multi-threaded applications. Having 64 processors won't speed up a single-threaded application, though the more CPUs you have, the faster a single-threaded app will be when running *multiple* applications.

---

### Post by aev on 2005-11-06
the Pi-test I got from this thread

[http://ubuntuforums.org/showthread.php?t=60264&highlight=pi+test](http://ubuntuforums.org/showthread.php?t=60264&highlight=pi+test)

just enter ./pi *number* - number is the digits after the point.

I have done MPI computing and know that no matter how many cpu you have , the program will run as if there is only one cpu if you are no running a multi-thread.

But still the hyperthreading should give you more calculation speed. At least it gives me on windows with the same computer specs for both hyperthreading and without.

 will try some MPI here :)

---

