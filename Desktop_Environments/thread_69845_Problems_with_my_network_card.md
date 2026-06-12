---
title: "Problems with my network card"
date: 2005-09-28
forum: Desktop Environments
---

### Post by tyttuz on 2005-09-28
Hi everyone,
I have problems with my network card in my acer aspire 1690.
My ethernet controller is Broadcom Corporation NetXtreme BCM5788 Gigabit Ehernet (rev03).

I have the device (I downloaded from acer website), and I do this (like said in manual):
***************************************************
rpm -ivh bcm5700-6.2.17-1.src.rpm
cd /usr/src/rpm/
rpm -bb SPECS/bcm5700.spec or rpmbuild -bb SPECS/bcm5700.spec
***************************************************

And said:
***************************************************
...
Executing(%build): /bin/sh -e /var/tmp/rpm-tmp.83156
+ umask 022
+ cd /usr/src/rpm/BUILD
+ cd bcm5700-6.2.17
+ make bcm5700.o
Makefile:18: *** Linux kernel source tree not found.   Stop.
error: Bad exit status from /var/tmp/rpm-tmp.83156 (%build)


RPM build errors:
     Bad exit status from /var/tmp/rpm-tmp.83156 (%build)
***************************************************

And in Control Center I have eth1 (eth0 is wireless card) disabled, and I can't enable.

So I can't install :( ....

Can someone help me to put my network card working?

Thanks
Tito

---

### Post by Paperjam on 2005-09-28
You have to install the kernel-headers:
```
sudo apt-get install linux-headers-`uname -r`
```

Afterwards, retry installing that driver.

---

### Post by tyttuz on 2005-09-28
I tried do :
sudo apt-get install linux-headers-`uname -r`

And show this:
Reading package list... Done
Building dependency tree... Done
Package linux-headers is not installed, so not removed
E: Couldn't find package uname -r

---

### Post by Paperjam on 2005-09-28
[QUOTE=tyttuz]I tried do :
sudo apt-get install linux-headers-`uname -r`
And show this:
Reading package list... Done
Building dependency tree... Done
Package linux-headers is not installed, so not removed
E: Couldn't find package uname -r[/QUOTE]
Strange...
Please do *uname -r*. It gives you your kernel version. Then, do 
```
sudo apt-get install linux-headers-*YourVersion*
```
Where *YourVersion* ist the output of *uname -r*

---

### Post by Tilex on 2005-09-28
I think, the question to ask is, do you have access to the internet with the computer is question?

---

### Post by tyttuz on 2005-09-28
[QUOTE=Tilex]I think, the question to ask is, do you have access to the internet with the computer is question?[/QUOTE]
YES, I have.
I have windows installed too, and when I run windows I have network and internet.

[QUOTE=Paperjam]Strange...
Please do uname -r. It gives you your kernel version. Then, do
Code:

sudo apt-get install linux-headers-YourVersion

Where YourVersion ist the output of uname -r[/QUOTE]

I do what you said:
uname -r

and show me 2.6.10-5-386, then I put
sudo apt-get install linux-headers-2.6.10-5-386

and install everything.

But now, when I try:
****************************************************
rpm -ivh bcm5700-6.2.17-1.src.rpm
cd /usr/src/rpm/
rpm -bb SPECS/bcm5700.spec or rpmbuild -bb SPECS/bcm5700.spec
****************************************************

Show me this:
And said:
************************************************** *
...
Executing(%build): /bin/sh -e /var/tmp/rpm-tmp.83156
+ umask 022
+ cd /usr/src/rpm/BUILD
+ cd bcm5700-6.2.17
+ make bcm5700.o
gcc -DMODULE -D__KERNEL__ -DDBG=0 -DT3_JUMBO_RCV_RCB_ENTRY_COUNT=256 -DNICE_SUPPORT -DPCIX_TARGET_WORKAROUND=1 -dINCLUDE_TBI_SUPPORT -DINCLUDE_5701_AX_FIX=1 -Wall -Wstrict-prototypes -06 -I/lib/modules/2.6.10-5-386/build/include   -c  -o b57um.o b57um.c
make: gcc:Command not found
make: ***[b57um.o] Error 127
error: Bad exit status from /var/tmp/rpm-tmp.83156 (%build)


RPM build errors:
Bad exit status from /var/tmp/rpm-tmp.83156 (%build)
************************************************** *

:(

---

### Post by Paperjam on 2005-09-28
There are some other tools missing. Try installing them with

```
sudo apt-get install build-essential gcc
```

Maybe you need some more tools, we'll have to see... though I think that's all :-)

---

### Post by tyttuz on 2005-09-28
:-) I think there are more tools to install :-)

I write sudo apt-get install build-essential gcc

and then I try to install the device and showm me this:
************************************************** *
...
Executing(%build): /bin/sh -e /var/tmp/rpm-tmp.83156
+ umask 022
+ cd /usr/src/rpm/BUILD
+ cd bcm5700-6.2.17
+ make bcm5700.o
gcc -DMODULE -D__KERNEL__ -DDBG=0 -DT3_JUMBO_RCV_RCB_ENTRY_COUNT=256 -DNICE_SUPPORT -DPCIX_TARGET_WORKAROUND=1 -dINCLUDE_TBI_SUPPORT -DINCLUDE_5701_AX_FIX=1 -Wall -Wstrict-prototypes -06 -I/lib/modules/2.6.10-5-386/build/include -c -o b57um.o b57um.c
In file included from b57um.c:19:
mm.h:30:31 linux/modversions.h: No such file or directory
In file included from /lib/modules/2.6.10-5-386/build/include/asm/processor.h:18,
                    from /lib/modules/2.6.10-5-386/build/include/asm/thread_info.h:17,
                    from /lib/modules/2.6.10-5-386/build/include/linux/thread_info.h:21,
                    from /lib/modules/2.6.10-5-386/build/include/linux/spinlock.h:12,
                    from /lib/modules/2.6.10-5-386/build/include/linux/capability.h:45,
                    from /lib/modules/2.6.10-5-386/build/include/linux/capability.h:45,
                    from /lib/modules/2.6.10-5-386/build/include/linux/sched.h:7,
                    from /lib/modules/2.6.10-5-386/build/include/linux/module.h:10,
                    from mm.h:32,
                    from b57um.c:19:
/lib/modules/2.6.10-5-386/build/include/asm/system.h: In function '__set_64bit_var':
/lib/modules/2.6.10-5-386/build/include/asm/system.h:193: warning: dereferencing type-punned pointer will break strict-aliasing rules
/lib/modules/2.6.10-5-386/build/include/asm/system.h:193: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from /lib/modules/2.6.10-5-386/build/include/linux/irq.h:21,
                    from /lib/modules/2.6.10-5-386/build/include/asm/hardirq.h:6,
                    from /lib/modules/2.6.10-5-386/build/include/linux/hardirq.h:6,
                    from /lib/modules/2.6.10-5-386/build/include/linux/interrupt.h:11,
                    from mm.h:47,
                    from b57um.c:19:
/lib/modules/2.6.10-5-386/build/include/asm/irq.h:16:21: irq_vectors.h: No such file or directory
In file included from /lib/modules/2.6.10-5-386/build/include/asm/hardirq.h:6,
                    from /lib/modules/2.6.10-5-386/build/include/linux/hardirq.h:6,
                    from /lib/modules/2.6.10-5-386/build/include/linux/interrupt.h:11,
                    from mm.h:47,
                    from b57um.c:19:
/lib/modules/2.6.10-5-386/build/include/linux/irq.h: At top level:
/lib/modules/2.6.10-5-386/build/include/linux/irq.h:71 error: 'NR_IRQS' undeclared here (not in a function)
In file included from /lib/modules/2.6.10-5-386/build/include/linux/irq.h:73,
                    from /lib/modules/2.6.10-5-386/build/include/asm/hardirq.h:6,
                    from /lib/modules/2.6.10-5-386/build/include/linux/hardirq.h:6,
                    from /lib/modules/2.6.10-5-386/build/include/linux/interrupt.h:11,
                    from mm.h:47,
                    from b57um.c:19:
/lib/modules/2.6.10-5-386/build/include/asm/hw_irq.h:28 error: 'NR_IRQ_VECTORS' undeclared here (not in a function)
/lib/modules/2.6.10-5-386/build/include/asm/irq.h:32 error: 'NR_IRQS' undeclared here (not in a function)
In file included from /lib/modules/2.6.10-5-386/build/include/asm/hardirq.h:6,
                    from /lib/modules/2.6.10-5-386/build/include/linux/hardirq.h:6,
                    from /lib/modules/2.6.10-5-386/build/include/linux/interrupt.h:11,
                    from mm.h:47,
                    from b57um.c:19:
/lib/modules/2.6.10-5-386/build/include/asm/irq.h:78 error: 'NR_IRQS' undeclared here (not in a function)
bc57um.c: In function 'bcm5700_init_board':
b57um.c:596 warning: implicit declaration of function 'init_etherdev'
b57um.c:596 warning: assignment makes pointer from integer without a cast make: *** [b57um.o] Error 1
error: Bad exit status from /var/tmp/rpm-tmp.65878 (%build)

error: Bad exit status from /var/tmp/rpm-tmp.83156 (%build)


RPM build errors:
Bad exit status from /var/tmp/rpm-tmp.83156 (%build)
***************************************************
:(

---

### Post by Paperjam on 2005-09-28
Now it gets more difficult to see what the problem is. Could you give me a link to the driver, so that I can have a look at the readme?

---

### Post by kleeman on 2005-09-28
Why are you trying to install the rpms? I downloaded the package into a directory went in there and did 

tar zxvf bcm5700-8.1.55.tar.gz
cd bcm5700-8.1.55
cd src
make

and it compiled the module you need: (bcm5700.ko)


make -C /lib/modules/2.6.10-5-686-smp/build SUBDIRS=/home/richard/netter/bcm5700-8.1.55/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686-smp'
  CC [M]  /home/richard/netter/bcm5700-8.1.55/src/b57um.o
  CC [M]  /home/richard/netter/bcm5700-8.1.55/src/b57proc.o
  CC [M]  /home/richard/netter/bcm5700-8.1.55/src/tigon3.o
  CC [M]  /home/richard/netter/bcm5700-8.1.55/src/autoneg.o
  CC [M]  /home/richard/netter/bcm5700-8.1.55/src/5701rls.o
  CC [M]  /home/richard/netter/bcm5700-8.1.55/src/tcp_seg.o
  CC [M]  /home/richard/netter/bcm5700-8.1.55/src/b57diag.o
  LD [M]  /home/richard/netter/bcm5700-8.1.55/src/bcm5700.o
  Building modules, stage 2.
  MODPOST
  CC      /home/richard/netter/bcm5700-8.1.55/src/bcm5700.mod.o
  LD [M]  /home/richard/netter/bcm5700-8.1.55/src/bcm5700.ko

---

### Post by tyttuz on 2005-09-28
[ftp://ftp.support.acer-euro.com/notebook/aspire_1690_ddr2/driver/lan5788.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_1690_ddr2/driver/lan5788.zip)

---

### Post by kleeman on 2005-09-28
General note: Using rpms on a Debian system is a BAD IDEA unless you have a binary rpm package and convert it to a deb using the alien utility.

---

### Post by kleeman on 2005-09-28
Those drivers are outdated. Use the link I gave in the other thread and then follow my directions above. Works for me.....

---

### Post by tyttuz on 2005-09-28
[QUOTE=kleeman]Those drivers are outdated. Use the link I gave in the other thread and then follow my directions above. Works for me.....[/QUOTE]

Ok I will try

---

### Post by tyttuz on 2005-09-28
I already make what you said... 
tar zxvf bcm5700-8.1.55.tar.gz
cd bcm5700-8.1.55
cd src
make

there is no errors... but I still without network/internet

---

### Post by Paperjam on 2005-09-28
[QUOTE=tyttuz]I already make what you said... 
tar zxvf bcm5700-8.1.55.tar.gz
cd bcm5700-8.1.55
cd src
make

there is no errors... but I still without network/internet[/QUOTE]
Probably *sudo make install* is missing. (But I don't know for sure.)

---

### Post by tyttuz on 2005-09-28
[QUOTE=Paperjam]Probably *sudo make install* is missing. (But I don't know for sure.)[/QUOTE]
I already made *make install*, but I tried *sudo make install* and show me this: make: *** No rule to make taget 'install'. Stop.

---

### Post by Paperjam on 2005-09-28
[QUOTE=tyttuz]make: *** No rule to make taget 'install'. Stop.[/QUOTE]
That's because the rule has already been applied, so the module is installed.

Now, you need to do
```
modprobe bcm5700
```
to load the module (it might have another name, I was unable to download that zip-file to have a look at the readme).
Then, if you want to load the module on every system start, do
```
sudo nano /etc/modules
```
and put the name of the module at the bottom of the file.

Now, install the wireless-tools (though I think they are installed by default): ```
sudo apt-get install wireless-tools
```

and enter ```
iwconfig
``` to see if your card has been detected.

---

### Post by tyttuz on 2005-09-29
[QUOTE=Paperjam]That's because the rule has already been applied, so the module is installed.
Now, you need to do
```
modprobe bcm5700
```
to load the module (it might have another name, I was unable to download that zip-file to have a look at the readme).
Then, if you want to load the module on every system start, do
```
sudo nano /etc/modules
```[/QUOTE]
and put the name of the module at the bottom of the file.
I made this... no results...nothing :(.
I'm still without network...
[QUOTE=Paperjam]
Now, install the wireless-tools (though I think they are installed by default): ```
sudo apt-get install wireless-tools
```[/QUOTE]
The wireless-tools are already installed.
[QUOTE=Paperjam]
and enter ```
iwconfig
``` to see if your card has been detected.[/QUOTE]
The card is detected but don't run...


I tried with live cd, and I went to Control Center and put eth1 in Automatic Mode and I click in Aplly.And works fine.But in kubuntu that I installed in my hard disk, doesn't work.

---

### Post by kleeman on 2005-09-29
Tito,
If you see the card with iwconfig chances are the driver is working. You now need to figure out wireless networking. Here is a good howto:

[https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29](https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29)

---

### Post by tyttuz on 2005-09-29
I re-install the kubuntu and now works fine... I don't know what happened ....

---

