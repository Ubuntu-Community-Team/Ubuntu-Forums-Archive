---
title: "Errors, wrong architecture '1386', (null). HELP!"
date: 2009-05-14
forum: General Help
---

### Post by chron-tron on 2009-05-14
I am new to the Linux world, so please be understanding and try to help in lame-man's terms. I installed ubuntu on my PS3 in hope of playing emulators of some of the classics (atari, sega, arcades), but I run into problems when trying to install.... anything. I tried installing some exe's I had on my computer, obviously didnt work. I downloaded gfceu, gens, snex9, and generator files for linux which I assumed should go through flawlessly... wrong. I try to install the .deb files, and it thinks for a bit, and gives "Error wrong architecture 'i386' ". I googled the error messages, and there were a few suggestions. I got to a DSL internet connection, and updated everything in linux, as well as my ps3. it took about 2 hours, so there was a bit. I was able to download the GFCE ultra simply from the synaptic whatever it's called, and that works fine. But the CODE. I found a few force architecture 'codes', but at the kboot screen, nor the strl+alt+F1 screen did I have any success. More dos-style error messages. Please help me, running out of hair to pull out.

---

### Post by mb_webguy on 2009-05-14
Can you not install software from the Ubuntu repositories?

---

### Post by chron-tron on 2009-05-16
I am a greenhorn when it comes to Linux. I don't even know what the repository refers to. The only way I was able to install gfxeu was downloading it through the synaptic manager. If someone can bear with me, and teach me how to successfully install one of these emulators, it would be greatly appreciated. Another question I have... Can you use the sixaxis controller with gfceu? If so, how do you configure it?

---

### Post by chron-tron on 2009-05-16
ok, here's the latest in my battle. 
Code:
sudo dpkg -i --force-architecture gens_2.12a-i386.deb

Error processing...
Cannot access archive: no such file or directory
...

The package is on the desktop, I type code 'ls', and examples is light blue instead of purple. 
Is this because the folder is locked, or is it looking for my package in the folder with blue text?

---

### Post by taurus on 2009-05-16
If you said you are in the right directory where that file, gens_2.12a-i386.deb, is, post the outputs of these two commands, running one at a time.

```
ls -la
uname -a
```

---

### Post by chron-tron on 2009-05-16
I don't know if I'm in the right directory or not. I type in ls -la and get a big list which I dunno what to do with. Uname -a gives
"Linux ubuntu 2.6.25-2-powerpc64-smp #1 SMP tue sep 30 16:40:22 utc 2008 ppc64 gnu/linux"
Using an iPhone, so done mind the upper/lowercase discrepancies. 

Dpkg --help shows --instdir=<directory> but I dunno how to change it to desktop. Getting closer... Keep the help coming. Thanks

---

### Post by taurus on 2009-05-16
> Linux ubuntu 2.6.25-2-**[COLOR="Red"]powerpc64[/COLOR]**-smp #1 SMP tue sep 30 16:40:22 utc 2008 ppc64 gnu/linux

Okay, here is your problem.  You are running Ubuntu on a Mac so you cannot install a i386 (or i686) on it.  That's why you get the wrong architecture message when you try to install gens_2.12a-**[COLOR="Blue"]i386[/COLOR]**.deb.

```
cd ~/Desktop
```

---

### Post by MaxIBoy on 2009-05-16
> **chron-tron said:**
> I am new to the Linux world, so please be understanding and try to help in lame-man's terms. I installed ubuntu on my PS3. that's your problem right there.

The short story is that PS3s use a "cell" processor, whereas most PCs use an "x86" processor. They use a different "language" of zeroes and ones, so computer programs compiled for one will not run directly on another.




The long version:


Your typical off-the-shelf PC uses an x86 computer chip. The Intel 8086 was the original (a 16-bit chip.) Then came the 80186, which was abbreviated to "i186." Then the i286. Then the i386, which was the first 32-bit one. Then the i486. The i586 was called the "Pentium" processor. Then the i686 (Pentium Pro, Core 2) and the i786 (Core i7, Atom.) i386 is the lowest common denominator these days, as it is the earliest 32-bit architecture in the series. Together, they're called the "x86" architecture. The x86 architecture was designed around an "everything and the kitchen sink" philosophy, the idea being that if there was a single command for "wash the dishes" instead of having to spell out each step explicitly, things would run faster. This later turned out to be untrue, and most of the recent work has been an effort to eliminate unneeded functionality.


Meanwhile, there are also RISC (Reduced Instruction Set Computer) architectures, designed to have the fewest features possible. It turns out that fewer features = smaller cores. Smaller cores = less overheating = more powerful processors. Also, smaller cores = more cores per processor, so RISC chips can often have as many as 64 cores per chip. The PowerPC (PPC) processor is a type of RISC chip designed for personal computers. You know those iMac G5 computers? That was the PowerPC G5 processor. Apple has since moved on to x86 for more compatibility. However, PPC has undeniable advantages in video game performance, which is why it was chosen for both the Xbox 360 and the PS3 (the Cell is a PPC chip.)

---

### Post by chron-tron on 2009-05-17
Thanks for that. I guess rather than asking how I can make this work, I should ask what to install. Would xubuntu somehow not be a mac?or are there plentyof good emulators I can run, and ijust need to track them down?

---

### Post by chron-tron on 2009-06-08
I am STILL looking for some help folks. I dl'd xubuntu to try a different version, but it was the wrong ISO. Ps3 couldn't boot it. I search ubuntu+ps3 and all the results are power pc (mac). Where can I find the version of ubuntu software I am looking for? Or alternately, where can I find an assortment or pre-n64 emulators to run on a ppwerpc-Linux system?

---

### Post by plentyTypos on 2010-06-22
> **chron-tron said:**
> I am STILL looking for some help folks. I dl'd xubuntu to try a different version, but it was the wrong ISO. Ps3 couldn't boot it. I search ubuntu+ps3 and all the results are power pc (mac). Where can I find the version of ubuntu software I am looking for? Or alternately, where can I find an assortment or pre-n64 emulators to run on a ppwerpc-Linux system?

I'm absolutely new to gnu/linux too, so this is not going to be much help, but I wanted to say that I'm quite sure that you can find a version of Ubuntu for the PowerPC chips. I know that I did briefly "test drive" an early version of Ubuntu on an old Mac a couple of years ago. Unfortunately I no longer know from where I downloaded that. I think though that the PowerPC architecture is now supported by the community (that is, not by Canonical). If you search around on the various web sites relating to Ubuntu community support you'll surely find it.

---

### Post by rob45 on 2010-06-22
> **plentyTypos said:**
> I'm absolutely new to gnu/linux too, so this is not going to be much help, but I wanted to say that I'm quite sure that you can find a version of Ubuntu for the PowerPC chips. I know that I did briefly "test drive" an early version of Ubuntu on an old Mac a couple of years ago. Unfortunately I no longer know from where I downloaded that. I think though that the PowerPC architecture is now supported by the community (that is, not by Canonical). If you search around on the various web sites relating to Ubuntu community support you'll surely find it.
[http://psubuntu.com/wiki/InstallationInstructions](http://psubuntu.com/wiki/InstallationInstructions)

---

### Post by rob45 on 2010-06-22
[http://psubuntu.com/wiki/InstallationInstructions](http://psubuntu.com/wiki/InstallationInstructions)

---

