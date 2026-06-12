---
title: "Vista Who?"
date: 2007-04-03
forum: Florida Team - US
---

### Post by nickthegreek78 on 2007-04-03
I am a new Ubuntu user from Clearwater, FL , I had always run Windows and recently bought a new Sony Vaio C 240 Core 2 Duo with Vista installed and I had so many problems I decided to seek an alternative .  A friend at work suggested Ubuntu and I in fact deleted Vista completely, Home Premium, and I wish I had been converted to Linux a long time ago!  Although it takes a little getting used to ( 2-3 days) I am so happy to run a computer on my terms, free from the bondage of MS.  No more crashes, no virus worries, I couldn't be happier with my new laptop.  Everyone in the Ubuntu community has been very helpful  and I look forward to communicating and learning from all of you.[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by 1/0 on 2007-04-03
I'm not from FL but I read your post and just wanted to say congrats and welcome. I hope you'll find GNU/Linux good and I think you've done a wise thing deciding not to dual boot. 

One thing: Don't give up if you get a problem. Look for indications in log files etc. and search. Log files is one of the best things in Linux. You can log everything and that way solve problems. If you don't find the answers you're looking for, just ask.

Also keeping a liveCD close by, such as [Knoppix]("http://www.knoppix.org/"), is really gonna help you to troubleshoot.

---

### Post by feravolo on 2007-04-03
Hello:

One thing that you should keep in mind is if you already paid for a "Premium" copy of  Vista, you just as well should keep it installed on your computer. 

Go ahead and use Ubuntu as your main operating system, but keep Vista as a backup, along with the live Luinx distro (e.g. SLAX or Knoppix). If you haven't already loaded your computer to the extent that you don't feel like reinstalling everything, here is what you can do.

For example your computer has a 100GB disk drive, use 10 or 20GB for vista,  2 or 3 times your ram size for a linux swap partition and the rest for Ubuntu. Loading Vista on a FAT32 partition will allow you to exchange files between the Vista partition and the Linux partition when running Ubuntu. It will also allow you to use your Live CD to read and write files on either partition.NTFS file formats have incompatibilities with Linux and you may be able to write to them by default. although there are (buggy) tools out there that claim to be able to read and write to NTFS. If you are using Linux you aren't going to care about the using NTFS file protections. 

As far as Live Linux CD's go I happen to like SLAX which is based on SLACKWARE 11. The distribution can be customized using the available modules. There are several versions, the "Kill Bill" edition includes programs designed to be compatible with windows. The "popcorn" edition fits on smaller USB key drives, your notebook computer should be boot-able from a USB port. To get SLAX got to [http://SLAX.org](http://SLAX.org) ; All you have to do is download an ISO image and burn a disk.

Keep in mind people like my self that have been in the software trade for years don't dislike windows. We just dislike the how much that we have to pay for it.

If you already paid for it go ahead and keep it around since Direct X10 is going to be a great for extreme gaming and if you have to do own your income taxes.

Peace
Mike F

P.S. Just Some Bonus Info: I was just at "Mega-Mart" and the Vista Home Premium Update Version was $169.00 (4/3/07)

---

### Post by Bordy on 2007-04-03
nickthegreek:
Welcome to our forums, and I am glad you searched us out :)

In case you haven't read up on us, check us out at [http://wiki.ubuntu.com/FloridaTeam](http://wiki.ubuntu.com/FloridaTeam) . We are all in FLorida, and you are welcome to join our group for discussion, help, advocacy, etc (we take all skill levels... I am a linux noob myself). 

In case you are interested, from that wiki page there is a new members section describing what resources we have. Check that out, and I hope to hear back from you soon :)

Chris

---

### Post by nickthegreek78 on 2007-04-03
Thanks for responding so promptly everyone, I do have a question. I read in another forum that Ubuntu does not recognize Core 2 Duo by default and only utilizes one processor, is that correct?  In addition, I found some instructions to fix this issue by changing the shell structure in the terminal.  I want to know if it has worked and I was wondering if there was any kind of widget, etc, that would show this and monitor the speed of the processor, I had a widget when I was first using Vista that did this. I took advice from both of you and downloaded both Knoopix and Slak just to be sure.  I also would like to know what app you are using for bit torrents and how to use them.  I used Automatix and installed Bit tornado but I am not quite sure how to use it, any help would be greatly appreciated.

---

### Post by nickthegreek78 on 2007-04-03
Bordy, I registered with the mailing list Thanks

---

### Post by Bordy on 2007-04-03
First bit of help: stay the heck away from Automatix. Good for installing, but seems to be a bit of a chore when updating things.

;)

---

### Post by lamalex on 2007-04-03
for the 2 processors, do a uname -a in terminal and if you see SMP then you are using both. if not you need a SMP kernel, which we can help you with if you don;t have it. im pretty sure edgy has smp by default.

---

### Post by tlcoffee on 2007-04-03
> **nickthegreek78 said:**
> I also would like to know what app you are using for bit torrents and how to use them. 


Azureus
[http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

It is a bt client built on the java platorm. very nice control options.

---

### Post by raptor2552 on 2007-04-03
I like Azureus as well. It's easy to setup through the applications menu and the frog is cool.

---

### Post by feravolo on 2007-04-03
If you want to know about your computer open a Terminal and type:

cat /proc/cpuinfo

I have a hyperthearded p4 Northwood and it returns the following:

mike@Cocoa-Beach:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.40GHz
stepping        : 9
cpu MHz         : 2394.397
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 4793.34

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.40GHz
stepping        : 9
cpu MHz         : 2394.397
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 4788.35

mike@Cocoa-Beach:~$

---

### Post by nickthegreek78 on 2007-04-04
Thanks for the info i really appreciate it. Here's are my stats please help                             
me to decifer this info is it recognizing both cores?

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 cx16 xtpr lahf_lm
bogomips        : 3329.68

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 cx16 xtpr lahf_lm
bogomips        : 3325.19

---

### Post by Praill on 2007-04-04
Yes you are using both cores there.
If you want graphical proof you can install a nifty little tool called gkrellm.
Open up a terminal and type:
```
sudo apt-get install gkrellm
```

You can then simply type gkrellm in the terminal to run it, or click on the link in applications-->system tools.


Oh, and welcome to the ubuntu world. Give yourself a couple more weeks and  you'll never go back to windows. Actually, you wont even like using a windows machine, and will finally understand all those other people that had such a distaste for it.

---

### Post by ep2011 on 2007-04-04
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 3
cpu MHz         : 3000.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6009.46

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 3
cpu MHz         : 2800.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6002.45

---


Am I using both cores?

---

### Post by martinw89 on 2007-04-04
Yup, dual core power it is

---

### Post by feravolo on 2007-04-04
For any system that has only one CPU on the motherboard and shows up as two processor means that you have successfully enabled either hyper-threading (p4/800FSB) or both processor cores on the newer dual-core machines. In the case of the older hyper-threaded P4's (northwood) like mine I had to enable the feature in the BIO's by entering setup mode at boot up. I am not sure if the dual-cores have one or two cores enabled off the shelf.

---

### Post by feravolo on 2007-06-08
Hey:

Did anyone see "Dr. Bill Gates" speech at that same Ivy League College that he flunked out of back in the 1970's? 

I saw the part of it where he was addressing the "inequities of the world", I wonder if he was speaking about the "inequities" of a bloated software monopoly that forces it's product on it's customers, while threating them with legal action if they don't continue to pay over and over again for the same capability. 

So let all save the world from those "inequities" with Ubuntu.

Peace

---

### Post by NeoTaoistTechnoPagan on 2007-06-09
> **Bordy said:**
> First bit of help: stay the heck away from Automatix. Good for installing, but seems to be a bit of a chore when updating things.

;)

Thanks Chris - way to throw it under the bus there....   ;)

IMHO you might be referring to the older version of Automatix. The latest edition is very easy to set up and use. The only reason I need it is to quickly add features to a system that I build for OEM and then I remove it. I had it on the laptop at the last meet only so I could install the JDK and NetBeans.

---

### Post by loserboy on 2007-06-09
heh Automatix is always been fine for me,  I think all you have to do when upgrading is uninstall AX and then remove the repos that it added

---

