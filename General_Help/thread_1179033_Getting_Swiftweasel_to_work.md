---
title: "Getting Swiftweasel to work"
date: 2009-06-05
forum: General Help
---

### Post by MechWarrior001 on 2009-06-05
I downloaded Swiftweasel and installed via .deb (swiftweasel-3.0.1_k6_ubuntu-i386.deb), and I'm using a AMD Athlon 1.2gHz 462 Socket processor, and when I try to run Swiftweasel3 in terminal, I just simply get "Illegal Instruction".

Did I do something wrong?

---

### Post by robert shearer on 2009-06-05
I do not think that your processor is a k6 so you probably have the wrong deb.

Try looking on the AMD site or wikipedia for your processor and its designation. (just a guess but I feel it is a k7 Thunderbird??)

Someone more familiar with AMD hardware will,no doubt, enlighten us.:)

EDIT  Here..[http://en.wikipedia.org/wiki/AMD_Athlon](http://en.wikipedia.org/wiki/AMD_Athlon)

Looks like you want one of these

swiftweasel-3.0.1_athlon-tbird_ubuntu-i386.deb     	
swiftweasel-3.0.1_athlon-xpubuntu-i386.deb 

check the link and see if you have an athlon-xp or thunderbird then uninstall the previous k6 version and download and install the version for your processor.

EDIT2 Ok open a terminal and type

```
cat /proc/cpuinfo
```

and this will return info on your cpu including its correct designation.

---

### Post by MechWarrior001 on 2009-06-06
Here's my CPU Info:
```

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 6
model        : 4
model name    : AMD Athlon(tm) Processor
stepping    : 2
cpu MHz        : 1202.118
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
bogomips    : 2404.23
clflush size    : 32
power management:
 
```

---

### Post by robert shearer on 2009-06-06
From this page...

[http://www.cpu-world.com/CPUs/K7/TYPE-Athlon.html](http://www.cpu-world.com/CPUs/K7/TYPE-Athlon.html)

..the grey-highlighted column looks like yours (K7)

and here...

[http://en.wikipedia.org/wiki/List_of_AMD_Athlon_microprocessors#Athlon_.28Model_4.2C_.22Thunderbird.22.2C_180_nm.29](http://en.wikipedia.org/wiki/List_of_AMD_Athlon_microprocessors#Athlon_.28Model_4.2C_.22Thunderbird.22.2C_180_nm.29)

scroll down to model 4 ( as per this line in your output.. "model        : 4"

so according to this an Athlon model 4 is a 'Thunderbird' so that is the deb you should try.
swiftweasel-3.0.1_athlon-tbird_ubuntu-i386.deb

No guarantees, although that is the one I would try were it my call :)
Post back and tell us how it goes.

---

### Post by MechWarrior001 on 2009-06-06
Nope, still gives me a illegal instruction.

---

### Post by fooman on 2009-06-06
> **MechWarrior001 said:**
> ...and when I try to run Swiftweasel3 in terminal, I just simply get "Illegal Instruction".

Did I do something wrong?

what was the command you tried in the terminal?

did you try:

```
swiftweasel
```

?

---

### Post by MechWarrior001 on 2009-06-06
It says "Command not found" if I simply type swiftweasel.

Right now I'm using the swiftweasel-3.0.1_athlon-tbird_ubuntu-i386 variant, but I'm starting to wonder if I'd be better off getting the Source Code and doing a custom compile.

---

### Post by robert shearer on 2009-06-07
Why not try the Firefox 3.5 daily build ??

Here...   [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

and use the drop down on the grey box (karmic koala) for your version. (ibex??).

I am using it on Jaunty and it rockets along...======>:D

---

### Post by MechWarrior001 on 2009-06-08
I'd rather not use firefox, because I've been using it this whole time. thats why I started this thread on Swiftweasel, unless I have to use that to compile Swiftweasel, which I dont entirely understand.

---

### Post by robert shearer on 2009-06-08
> I'd rather not use firefox, because I've been using it this whole time. thats why I started this thread on Swiftweasel

So what is it you are trying to achieve??

If it is speed then consider this..  the FFox you have been using > this whole time is FFox 3.0.x (currently 3.0.10 ? if up to date) and the Swiftweasel you wanted is built from FFox 3.0.1. This is probably older than the FFox you are using now but optimised for your processor.

FFox 3.5beta4 as in my last post is faster than both of these, in my experience, yes tried  all three.

If you want faster still then you could compile FFox 3.5beta4 yourself but I would suggest you try the link I gave first.

If you are trying to achieve **something else** please post with details.

---

### Post by MechWarrior001 on 2009-06-08
The reason I choose SW3.0.1 is becuase it was one I am familiar with, but I guess I'll try the 3.5 RC1 Trunk. Should I grab the source?

---

### Post by robert shearer on 2009-06-08
I am open to correction here but from this site...
[http://www.builderau.com.au/news/soa/Mozilla-testing-near-final-Firefox-3-5/0,339028227,339296725,00.htm](http://www.builderau.com.au/news/soa/Mozilla-testing-near-final-Firefox-3-5/0,339028227,339296725,00.htm)

> Even though RC1 hasn't been released yet, the test day will still go on with the latest nightlies (nightly builds of Firefox based on the latest source code), which are practically RC1 minus some minor uplifts," said Aakash Desai of Mozilla's quality assurance team on Thursday.

so the daily builds as I linked here..

[https://launchpad.net/~ubuntu-mozill...y/+archive/ppa](https://launchpad.net/~ubuntu-mozill...y/+archive/ppa)

may suffice.
If you add the ppa from this site you will find a new update download available through your package manager **each day** and this will, presumably, become RC1, then Final.

if you don't want a daily update then look for a deb or compile.

---

### Post by d_yat on 2009-09-05
Hey, do you still get this problem?
If you are still doing so. I too wanted to try out Swiftweasel on my parents PC, but all I ever get is (from the command line) "Illegal instruction".
HOWEVER!
I also tried it on my laptop, which is using a Hardy (8.04) branch of ubuntu. And on there it worked just fine. (and that's with the latest 3.5.2 build).
So I was wondering it the problem had to do with the version of ubuntu we were using, as my Parents PC is using Jaunty (9.04).

---

