---
title: "How to remove the virus?"
date: 2009-06-03
forum: General Help
---

### Post by blazemore on 2009-06-03
I have a virus, as shown in the screenshot. I was browsing a website for ways to make money online and the popup came up.
I clicked to remove and downloaded the file to my desktop. How do I run the file to remove the virus? DO it run it on a windows pc and then can it remove the virus from my linux ubuntu?
Look at screenshot

---

### Post by albinootje on 2009-06-03
> **blazemore said:**
> I have a virus, as shown in the screenshot.

That's fake. Only trying to get you interested in their software.
Ignore it.

I suggest to use the WOT addon in Firefox, and try also the NoScript addon (NoScript has a learning-curve, and is imho not for everyone).

---

### Post by Johnsie on 2009-06-03
Click the X button on the top right hand side to close the window. This is just a website pretending to be a virus checker.

---

### Post by blazemore on 2009-06-03
Here's the debug info from Wine
```
$ wine Install_2009-3.exe 
wine: Unhandled page fault on write access to 0x7b8b6ff4 at address 0x41142d (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x7b8b6ff4 in 32-bit code (0x0041142d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0041142d ESP:0032fea8 EBP:0032ffe8 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:7b8b6ff4 EBX:7b8b6ff4 ECX:7ffd8000 EDX:0032ff2c
 ESI:00000000 EDI:00820fb6
Stack dump:
0x0032fea8:  00410bf8 cd7767be adf89c1f 00a2e2ea
0x0032feb8:  00410b48 feb680f8 3ac7e1b7 00410a78
0x0032fec8:  35d415d5 cc706942 fffbe000 00410997
0x0032fed8:  dcbee747 2c664d91 00410886 2ba857a1
0x0032fee8:  42f693fb 004107a5 b3086c3e 004106de
0x0032fef8:  860b150a 467fbdcc 0041062e 6dd904a4
Backtrace:
=>0 0x0041142d in install_2009-3 (+0x1142d) (0x0032ffe8)
  1 0xb7e36da7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0041142d: addb	%al,0x0(%eax)
Modules:
Module	Address			Debug info	Name (16 modules)
PE	  400000-  a30000	Export          install_2009-3
ELF	7b800000-7b948000	Deferred        kernel32<elf>
  \-PE	7b820000-7b948000	\               kernel32
ELF	7bc00000-7bcb0000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb0000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7efa1000-7efad000	Deferred        libnss_files.so.2
ELF	7efad000-7efc6000	Deferred        libnsl.so.1
ELF	7efc6000-7efec000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c90000-b7c99000	Deferred        libnss_compat.so.2
ELF	b7c9a000-b7c9e000	Deferred        libdl.so.2
ELF	b7c9e000-b7e01000	Deferred        libc.so.6
ELF	b7e02000-b7e1b000	Deferred        libpthread.so.0
ELF	b7e2f000-b7f6a000	Export          libwine.so.1
ELF	b7f6c000-b7f8a000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Y:\Desktop\Install_2009-3.exe
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000019 
	0000001a    0
Backtrace:
=>0 0x0041142d in install_2009-3 (+0x1142d) (0x0032ffe8)
  1 0xb7e36da7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

---

### Post by dmizer on 2009-06-03
As the others have said. It's fake. It can't hurt your machine.

---

### Post by WatchingThePain on 2009-06-03
Is that the Registry mechanic thing?.
How do sites get away with that.
"oh we have found 1000 problems on your machine which only our software can fix".
Those Douchebags.
Your Linux should be fine, just run a scanner/fixer on your Windows.
Put windows into safe mode first.

I would also get rid of all restore points but it's upto you.

---

### Post by blazemore on 2009-06-03
But how can I run it in Wine

---

### Post by benj1 on 2009-06-03
regarding viruses on wine read [this]("http://www.linux.com/archive/feature/42031")

why are you trusting a website pop up telling you, you have a virus anyway, its  more likely do be a virus itself (well trojan, don't start).

---

### Post by blazemore on 2009-06-03
I don't want to run a virus in wine, I want to run a virus REMOVAL in wine

---

### Post by t0p on 2009-06-03
In addition to what you've already been told, I'd like to add a warning: ***It can be very dangerous to your machine if you download and run the fake "virus removal software" offered by sites like these***.  Probably not so dangerous to a computer running linux; but if you ran that program on a windows machine you would probably be installing trojans/viruses/goddess knows what awful malware.  Sites like this are dangerous, and should be avoided at all costs.  In fact, **it would be nice if the OP posted here the url of that site so everyone else knows to avoid it**.

Also, think about it for a second: the pop-up was designed to look like a windows system pop-up.  If you saw this while using ubuntu, it's obvious that it is not real.  And the so-called "virus remover" is being touted as a windows utility - so if it was real, it wouldn't work on an ubuntu system anyway, would it?

---

### Post by WatchingThePain on 2009-06-03
Install the scanner into wine and scan your wine c: drive I think should work.
The wine registry should be checked too.
I don't know which AV scanner will work in wine of the top of my head.

Since its in Wine forget what I said about safe mode and restore.

---

### Post by tarps87 on 2009-06-03
> **blazemore said:**
> But how can I run it in Wine

You don't, I doubt very much that that is even the layout of your wine 'drive'. It definitely isn't the layout of your Ubuntu system. It will come up the same even if you weren't dual booting.

It you want to check if you have a virus I suggest using clamav, it is in the repos.

NEVER trust a virus scanner from a website especially not a trusted one trying to sell you the product

---

### Post by blazemore on 2009-06-03
Link is here <link removed>

---

### Post by blazemore on 2009-06-03
**This has been a drill. You have all performed very well. Congratulations.**

---

### Post by t0p on 2009-06-03
> **blazemore said:**
> I don't want to run a virus in wine, I want to run a virus REMOVAL in wine

1. It's not real.

2. If you really want to check for windows viruses on your ubuntu system, use a proper, reputable av utility designed for this purpose.  Do a search in synaptic: there are av programs in the repositories.  Personally, I wouldn't bother.  But it's your machine...

---

### Post by albinootje on 2009-06-03
> **blazemore said:**
> I don't want to run a virus in wine, I want to run a virus REMOVAL in wine

If you really want that, then install proper anti-virus software in Ubuntu.

Why would you install software from a pop-up, coming from a website you've never heard of ?

They've managed to scare you, and almost managed to make you run *their* software.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

---

### Post by StooJ on 2009-06-03
> **blazemore said:**
> **This has been a drill. You have all performed very well. Congratulations.**

Glad to hear it. :D

---

### Post by benj1 on 2009-06-03
hey i might actually bookmark that page, its good for checking your ip address, doesn't work too well with adblock and noscript :(

---

### Post by dmizer on 2009-06-03
It's not necessary to drill our userbase.

Closed thread.

Thank you. :)

---

