---
title: "Linux on Dell Alienware m15x (PM55,i7)"
date: 2009-11-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mjbommar on 2009-11-15
Has anyone tested Linux on one of these machines yet?  I returned an HP dv6t because its quirky BIOS made Linux worthless and was hoping to get confirmation from someone that these machines work without too much trouble.  Current EDD for mine is early December, so if not, I'll make sure to update the thread when I do receive it.

Note that this is not the old Alienware m15 - it's the newer line with the i7 and the PM55 chipset.

---

### Post by mjbommar on 2009-11-23
My m15x will be delivered on Wednesday.

The only other source of information about Linux on this machine is here:
[http://www.youtube.com/watch?v=Hzot3B94iCk](http://www.youtube.com/watch?v=Hzot3B94iCk)

The uploader claims "the driver are not compatible (video driver) it keep on restart for no reason, and there for i have to removed it.. "

Unclear whether they were installing i386 or x64 and whether or not they tried the alternate install method from the console...

---

### Post by uncon on 2009-11-24
Cool.  I'm currently waiting on my M15x and should have it in a few weeks.  Let me know how it goes.  I'd also like to see the output of 'lspci -v' and 'lsusb -v' (maybe 'dmesg' too), if you get a chance.

---

### Post by mjbommar on 2009-11-24
> **uncon said:**
> Cool.  I'm currently waiting on my M15x and should have it in a few weeks.  Let me know how it goes.  I'd also like to see the output of 'lspci -v' and 'lsusb -v' (maybe 'dmesg' too), if you get a chance.

Sure, anything in particular you're worried about?

---

### Post by uncon on 2009-11-24
> **mjbommar said:**
> Sure, anything in particular you're worried about?

I wouldn't say I'm worried.  I just want to look into the hardware and how well it's supported.  I'm also curious about how to interface with the RGB LEDs.

---

### Post by mjbommar on 2009-11-25
I'm writing this message from Win7, as there seems to be some significant performance differences between Linux native and Linux under VirtualBox.  

I'm not sure whether this has to do with ACPI or scheduling, but the results are an enormous difference in phoronix scores...Ubuntu/VirtualBox has TWICE the scimark2 score as Ubuntu/Native.

---

### Post by uncon on 2009-11-25
> **mjbommar said:**
> I'm writing this message from Win7, as there seems to be some significant performance differences between Linux native and Linux under VirtualBox.  

I'm not sure whether this has to do with ACPI or scheduling, but the results are an enormous difference in phoronix scores...Ubuntu/VirtualBox has TWICE the scimark2 score as Ubuntu/Native.

Might be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036").  Where you able to get the lspci and lsusb outputs while you were running it native?

---

### Post by HeadHunter00 on 2009-11-25
You're so lucky to get such an awesome computer

---

### Post by AutumnStone on 2009-11-25
I'm also in the market for a new laptop, and since I have had the one I'm typing this on for the past 6 years (Thankyou linux!) I can afford something shiny.

I'm looking at the m15x with eyes besotted by all the shiny, but would really like to know if ubuntu installs well on it.

I've been windows free at home for years now, and spend the work days where I'm in the office cursing the windows box they've foisted on us.  So I really don't want a laptop - especially an expensive one - that fails to install ubuntu.

Please let us know how the install goes, whether there are any hiccough with the hardware (I know the old m15x pre dell had sound issues, and there's a rumour this one has video issues)

Thanks so much to all people testing this for us.

Cheers - AutumnStone

---

### Post by mjbommar on 2009-11-26
**[SIZE="3"]RE: Install[/SIZE]**
I'm running 64-bit 9.1.  There weren't any issues when I installed - either through the default install path or within the Live CD.  I'm not sure what issue that YouTube poster was suffering from.

**[SIZE="3"]RE: Hardware Support[/SIZE]**
I've uploaded the following output:
[LIST]
[*]dmesg
[*]lspci
[*]lsusb
[*]lshw
[/LIST]

For the following configs:
[LIST]
[*]tb: factory defaults, turboboost enabled, virt enabled
[*]no-tb: factory defaults, turboboost disabled, virt enabled
[/LIST]

You can find them in the corresponding directories here:
[http://www-personal.umich.edu/~mjbommar/m15x/](http://www-personal.umich.edu/~mjbommar/m15x/)

---

### Post by mjbommar on 2009-11-26
URL: [http://global.phoronix-test-suite.com/index.php?k=profile&u=mjbommar-10157-25021-1778](http://global.phoronix-test-suite.com/index.php?k=profile&u=mjbommar-10157-25021-1778)

I've also been running benchmarks on the machine with various BIOS settings:
* With and without turbo boost
* With stock Ubuntu 9.1 kernel and latest linus git kernel (2.6.32-rc8)
* Native and virtualized under VirtualBox

You can see that native significantly underperforms virtualized, regardless of TurboBoost and even with the latest kernel.  I'm excited by the virtualized results but still disappointed by the 

The rightmost column is my current machine, a Precision M4400 with an X9100 and DDR2 RAM.

[IMG]http://global.phoronix-test-suite.com/global-graph.php?g=BAR_GRAPH&t=SciMark&s=Computational%20Test:%20Composite&n=2.0&u=Mflops&i=mjb-tb-ss;mjb-tb-ss1;mjb-tb-ss-2.6.32-rc8;mjb-notb-ss-2.6.32-rc8;mjb-vbox-tb-ss;m4400-x9100;&v=526.29;530.07;529.16;463.36;669.14;550.99;&p=HIB&x=2.0.0[/IMG]

[IMG]http://global.phoronix-test-suite.com/global-graph.php?g=BAR_GRAPH&t=RAMspeed&s=Type:%20Average%20-%20Benchmark:%20Integer%20-%20Length:%203%20Times&n=2.5.2&u=MB/s&i=mjb-tb-ss1;mjb-tb-ss-2.6.32-rc8;mjb-notb-ss-2.6.32-rc8;mjb-vbox-tb-ss;m4400-x9100;&v=6680.69;6956.85;6803.51;7005.00;2973.50;&p=HIB&x=2.0.0[/IMG]

---

### Post by mjbommar on 2009-11-26
I also just built a fresh kernel without ACPI, SMP, or SMT in response to the bug #429036 - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036?comments=all) .

The takeaway is still that the kernel is not where it needs to be for the i7's.

---

### Post by AutumnStone on 2009-11-26
Thankyou again for being test guinea pigs.  It's greatly appreciated.

-Autumnstone

---

### Post by paulchinnz on 2009-12-19
I'm considering this beast myself in the near future. Some questions for those with 9.10 on it:
1) Anyone have a SSD with it?
2) What's the battery time with a 6 (or 9 cell) with 9.10, not gaming, just surfing/emailing/using OOo/playing music or videos? (PS - I find setting the screen to negative using Compiz makes a big difference to battery endurance with my current Inspiron)
3) Any trouble with the 260M GPU?
4) Does the multi-card reader work? (this is like a final frontier for my Inspiron, still doesn't do it in Ubuntu!)

Thanks!

---

### Post by uncon on 2009-12-19
> **paulchinnz said:**
> I'm considering this beast myself in the near future. Some questions for those with 9.10 on it:
I can highly recommend this laptop.  I've very pleased with it so far.  I've been running Linux exclusively on it since I received it.

> 1) Anyone have a SSD with it?
Yes, and I'm very happy with it.  If you want more information on it, it's a "SAMSUNG SSD PM800 Series 2.5" 256GB, VBM19D1Q".

> 2) What's the battery time with a 6 (or 9 cell) with 9.10, not gaming, just surfing/emailing/using OOo/playing music or videos? (PS - I find setting the screen to negative using Compiz makes a big difference to battery endurance with my current Inspiron)
I have the 9-cell battery and I get about 2.5 hours doing standard desktop activities (not gaming) and leaving compiz as is.

> 3) Any trouble with the 260M GPU?
I got the GeForce GT 240M GPU, but I have no issues whatsoever.  Also, while Dell's site specifically says this card has 512MB, it actually has 1GB of memory.

> 4) Does the multi-card reader work? (this is like a final frontier for my Inspiron, still doesn't do it in Ubuntu!)
I've only tested with SD, and it works fine.

One thing to note is that the Turbo mode on the CPU doesn't appear to be working at all on the current kernel (2.6.31-16-generic x86_64).

---

### Post by paulchinnz on 2009-12-19
Cheers for the quick reply.

Hopefully the 128GB I'll be getting is from the same Samsung lineup.

Turbo mode doesn't matter too much as I suspect I'll only need the Turbo mode with Windows playing Crysis etc.

By the way, is this virtual/native performance difference for real? It'd be great justification for running 9.10 (where I do 95% of my stuff) in Win7 (for gaming/some pesky applications Ubuntu hasn't quite got sorted out yet).

---

### Post by uncon on 2009-12-20
> **paulchinnz said:**
> Cheers for the quick reply.

Hopefully the 128GB I'll be getting is from the same Samsung lineup.

Turbo mode doesn't matter too much as I suspect I'll only need the Turbo mode with Windows playing Crysis etc.

By the way, is this virtual/native performance difference for real? It'd be great justification for running 9.10 (where I do 95% of my stuff) in Win7 (for gaming/some pesky applications Ubuntu hasn't quite got sorted out yet).

As far as I can tell, the benchmark that indicates this is actually only single threaded, and the difference we see here is due to the CPU not going into Turbo.  However, I have not extensively researched this.

---

### Post by Sum Guy on 2009-12-20
It looks like Intel's virtualisation hardware is helping with this bug, as it appears the virtual Ubuntu machine is outpacing the native Windows install it's running on.

---

### Post by paulchinnz on 2009-12-20
I don't really understand any of this. However, like any good layperson, what I really want to know is: do these benchmarking figures translate to real-world differences i.e. has anyone actually noticed a significant difference between using 9.10 on one of these machines virtualised (on Windows 7 preferably) vs. native?

---

### Post by uncon on 2009-12-20
> **paulchinnz said:**
> I don't really understand any of this. However, like any good layperson, what I really want to know is: do these benchmarking figures translate to real-world differences i.e. has anyone actually noticed a significant difference between using 9.10 on one of these machines virtualised (on Windows 7 preferably) vs. native?

It's doubtful that you will notice this unless you are running one single threaded app (e.g., audio/video encoder).  In this case, under Windows, the CPU would over clock one core and slow down the other cores (Turbo mode).  However, in Linux (at this point in time) no core will over clock, and the other cores will not change.  Thusly, the single threaded app will appear to preform better in Windows than in Linux.

Short answer: You'll probably never notice.

---

### Post by Sum Guy on 2009-12-21
How's the graphics card run with Ubuntu? Also, is there any sign of an i7 kernel in the future (to enable its new features)?

Also, since this is the only tech forum I'm a member of, and it relates to this unit, I'll ask it here:
Would you say this laptop justifies the additional cost over the XPS 16? I'd like to mess around with a few random high end games, but above all I'd like something with enough kick now in all of its faculties to last at least 2-3 years, preferably more.

---

### Post by uncon on 2009-12-21
> **Sum Guy said:**
> How's the graphics card run with Ubuntu? Also, is there any sign of an i7 kernel in the future (to enable its new features)?

Also, since this is the only tech forum I'm a member of, and it relates to this unit, I'll ask it here:
Would you say this laptop justifies the additional cost over the XPS 16? I'd like to mess around with a few random high end games, but above all I'd like something with enough kick now in all of its faculties to last at least 2-3 years, preferably more.

Your GPU question has already been answered in this thread.  As for i7 support, we *should* already have it.  From what I can tell, it's in the kernel version that we're running, but not working in Ubuntu.

I don't use this system for gaming at all.  The reviews I read about the structural integrity, the cooling system and the display are what won me over.

---

### Post by Sum Guy on 2009-12-21
That's great to know! Sorry I missed ther bit about the GPU, should have paid more attention. Anyway, thanks for the info, looks like this will be my new system (eventually)!

---

### Post by paulchinnz on 2009-12-21
The touchpad has been a notorious problem, which unfortunately I didn't notice much improvement with 9.10 on my Inspiron. Is the experience with the M15x any different? (admittedly only really an issue when flying economy class!)

---

### Post by uncon on 2009-12-21
> **paulchinnz said:**
> The touchpad has been a notorious problem, which unfortunately I didn't notice much improvement with 9.10 on my Inspiron. Is the experience with the M15x any different? (admittedly only really an issue when flying economy class!)

I'm not familiar with the issues with the touch pad on the Inspirons.  The Windows driver that is preinstalled on the M15x is very crappy.  I'm not even sure how they managed past QA like that, but it doesn't matter.  In Windows you can just remove the driver and use the MS one.  In Linux this isn't an issue at all.  My touch pad behaves about as good as any other I've used.

---

### Post by paulchinnz on 2009-12-21
MS as in M$ or some other MS?

I think the touchpad is an issue on lots of different laptops with Ubuntu and has been for some iterations of (at least 7.xx from memory).

---

### Post by uncon on 2009-12-21
> **paulchinnz said:**
> MS as in M$ or some other MS?

I think the touchpad is an issue on lots of different laptops with Ubuntu and has been for some iterations of (at least 7.xx from memory).

MS, as in Microsoft.

I've been using Ubuntu on laptops for a long time and never had an issue.  *shrug*

---

### Post by paulchinnz on 2009-12-21
Thanks for the advice re: Microsoft drivers for the touchpad. I'll google them when my M15x arrives.

---

### Post by uncon on 2009-12-21
> **paulchinnz said:**
> Thanks for the advice re: Microsoft drivers for the touchpad. I'll google them when my M15x arrives.

These are the drivers included with the Windows...  You'll already have them.

---

### Post by paulchinnz on 2009-12-21
> **uncon said:**
> I'm not familiar with the issues with the touch pad on the Inspirons.  The Windows driver that is preinstalled on the M15x is very crappy.  I'm not even sure how they managed past QA like that, but it doesn't matter.  In Windows you can just remove the driver and use the MS one.  In Linux this isn't an issue at all.  My touch pad behaves about as good as any other I've used.

I see. Did you mean the Alienware driver rather than Windows driver (above)? Or are you implying that there was a better Windows driver available than the preinstalled one also from Windows?

---

### Post by uncon on 2009-12-21
> **paulchinnz said:**
> I see. Did you mean the Alienware driver rather than Windows driver (above)? Or are you implying that there was a better Windows driver available than the preinstalled one also from Windows?

The driver that is installed from the factory (from Synaptics, IIRC) is nearly useless.  If you remove this driver and use the standard Windows driver, the touch pad works as well as can be expected from a touch pad.

---

### Post by paulchinnz on 2009-12-21
Cool thanks for clearing that up. The touchpad, even in Windows, has been one of the issues that some M15x reviewers have nitpicked on, which may be because of the driver issues you note. Now for the big wait for the box to arrive...

---

### Post by danilius on 2009-12-31
I have just installed 9.10 64-bit, and so far everything runs just dandy - graphics card, trackpad, webcam and sound. 

Now, can anyone tell me ho to change the backlighting LEDs for the keyboard, alien head and so on?

As for the build quality, it is quite frankly the finest piece of kit I have laid my hands on for a while.

---

### Post by Sum Guy on 2009-12-31
I don't think anyone has any idea how the LED controller works. The big things will be finding the interface, and then finding out how to use it (obviously). Try using dmesg and looking for anything weird.

---

### Post by paulchinnz on 2009-12-31
Anyone have any thoughts on how best to play Crysis (PC version) on this machine while minimising Windows 7's footprint? VM W7 or dual-boot?

---

### Post by Sum Guy on 2009-12-31
Dual boot for sure. Ubuntu currently does not utilise the Core i7 correctly, and so W7 would not only run faster, but Ubuntu would run faster in a Virtual Machine, until this is fixed (look at earlier pages in the thread).

---

### Post by paulchinnz on 2009-12-31
I guess that's the third option isn't it, to VM 9.10 as noted earlier in this thread. Given how secure W7 is meant to be, and using Shadow Defender and VM W7 *and* 9.10 within W7, life might be almost as secure as 9.10 alone, but more functional. However, VMing 9.10 within W7 just doesn't seem right.

I'll probably ultimately dual boot: 9.10 with VM W7 to use some work apps (still having issues with Wine) and native W7 for gaming.

---

### Post by HunterThomson on 2010-01-23
This thread is just fantastic :) Thanks guys

I do technically "Have" enough money to buy this new M15x with the i7-720QM.(AKA I really shouldn't spend this money but Awe the hell with it I want a Core i7 Quad Core :)

It seems the Turbo Mode IS working, At lest in the New Linux Kernel. It is just that the real speed is not being properly reported by the Kernel. There is this tool that will tell you the Real clock speed as it Over clocks it self. I don't know about Ubuntu though. But they guy said that it will only do the Single Core Over Clocking not the Dule or Quad. I would guess that this will be all worked out vary soon anyway. Here is the thread on the Arch Linux forums that I got this info from.

[http://bbs.archlinux.org/viewtopic.php?id=86343](http://bbs.archlinux.org/viewtopic.php?id=86343)

I've been thinking the VB speed increase sounds kind of fishy ever sens I first read that. The bench marks don't lie but some times they can be misleading.

As for Win7 being "More" secure then XP. Sure, ya it is. But, it is VARY VARY far from "Secure". It is still windows. Also, the benchmarks on Win7 are Without running Anti-Virus software that has to scan every bit of everything read off of the HHD, CD, Every Web Page, Every download, And then just run in the background all the time scanning every bit of the HDD. Then When your not using it for a Sec it has to start building backups of the Win system files and stuff. Using every spare CPU clock cycle scanning for more Viruses and checking for Key-loggers and Spy-ware... This list go's on and on. Also the NTFS Unbelievable problem with fragmentation. Then Win7 downloading and installing updates taking up all your bandwith and CPU and RAM.... Really in real life Win7 runs WAY slower on this laptop then Linux even if Turbo Boost is not working. Hell in Linux you still get 8 Logical CPU cores to work with and NO Ani-Virus taking up All the CPU making up for a crazy insecure Windows OS.

With all that running I am fairly certen that you will get a large performance DROP running Linux in a VM under a Win7 Host. In the real world.

-----------
Wow I got off topic sorry.... preaching to the quire

Any way, So it sounds like this is a vary good Linux laptop. I am going to buy it. It seem like Just Don't flash the BIOS to A03 and everyone has written glowing reviews of this laptop. Everyone seems to love the build quality. I'm stoked. And if the one I get has 1GB of Video RAM on the 240 WOW I would be stoked :)

---

### Post by uncon on 2010-01-23
This issue we are seeing with turbo boost not kicking in is fixed in 2.6.33-rc5 (Kernel [Bug 15064]("http://bugzilla.kernel.org/show_bug.cgi?id=15064")).  Karmic is currently on 2.6.31...  You can also read more on [this i7z thread]("http://code.google.com/p/i7z/issues/detail?id=1").

---

### Post by paulchinnz on 2010-01-23
Well there may have been some major improvements in the last fortnight since I moved from native to Windows 7 hosted Ubuntu, but at the time, native Ubuntu 9.10 simply slowed to a crawl once I had a few programs going (Evolution, Firefox, Pidgin, OOo and maybe one or two others), whereas hosted it's fine.

A bit off topic HunterThomson, but I'll make one reply, and promise to say no more on this thread about it: on Windows 7, using Standard User Account (which superficially works similarly to Linux requirement for password any time admin/root type changes are intended) and despite Microsoft Security Essentials in the background I can play Crysis on high settings very smoothly. Let me know when you can do this in Ubuntu. 

I still really like Ubuntu though, which is why I'm VMing it and doing most of my non-gaming in it.

---

### Post by HunterThomson on 2010-01-23
Right on, ya it was late at night I went a little overboard.

But, Win7 is not a Secure system. Ubuntu is Not a secure system ether. Though still far more secure then Win7.

OpenBSD, NetBSD,... Hardened-Gentoo, RedHat, SUSE... These are secure as long as they are administered properly. Hardened-Gentoo being one of the most secure. I don't know much about Solaris and I am sure there are other secure systems too. If your interested you should start learning how to crack into Linux systems. You will learn that the vanilla Linux Kernel is actually vary insecure.

There is far more to security then the sudo password. There is memory management, How the software was compiled, other internal Kernel processes, the file system ACL... loads of stuff. The network stack....

All of this is on a scale of...
Imposable to crack dream system<--------------to---------------->Win98
---------------------

Right on. Well at lest the new 2.6.33 Kernel will support the i7 Turbo Mode.

---

### Post by paulchinnz on 2010-01-23
You make some valid comments about security.

Anyway, let us know your experience when you've got your M15x running with some flavour of Linux HunterThomson.

Has anyone got Face recognition working in Ubuntu?

---

### Post by HunterThomson on 2010-01-23
Right on ya I am still going a little over board about that sorry...
Honestly, I'll be Dule-booting Win7. I hate windows but Ahe, you can't have an Alianware Laptop and not run cool new games on it like Left 4 Dead :)

I'll post. I'll use the new 2.6.33 Kernel. I bet it will be in the Stable Archlinux repo by the time I get my M15x.

Owe, also I read someone asking about the Dell XPS 16 with the i7-720QM
I was reading a lot of forums and it seems that the XPS 16 has Over Heating problems with the Core i7. Also, there was a report of a Linux user having lots of problems with the BIOS on it and it causing lots of problem in Linux. He even returned it to Dell because it didn't run Linux well at all. So, I'd spend the extra money and get the M15x. If for no other reason then the better cooling system in the M15x.
((of course the guy may not have really known what he was talking about..))
The XPS 16 is a much better deal though... maybe read more about it on Linux. And get a nice cooling pad.

------------

Also, I have yet to find anyone that has gotten the "Changing" of the Alianware lighing to work under Linux. Maybe there is. Maybe no one has really tried. It makes sents to me that there should be a way I'd look in /proc/acpi for the stuff.

The Facial Recognition is all in the software. So, there needs to be that software written for Linux.

However, Facial Recognition is Insecure. There is only ONE camera so it can't tell Depth. SO, you can just hold up a picture of the persons face and the system will let you in. Even if it did have 2 camras to get Depth. Your showing your password (your face) to the world all the time. One could make a sculpture of your face and it would work.

---

### Post by paulchinnz on 2010-01-23
I've had similar thoughts regarding depth with face recognition. Novelty's wearing off now; will be returning to typed passwords!

---

### Post by HunterThomson on 2010-01-24
> **paulchinnz said:**
> I've had similar thoughts regarding depth with face recognition. Novelty's wearing off now; will be returning to typed passwords!

If you have a nice printer try it out. I cracked my finger print reader with tape and crushed up pencil lead. It did take several tries though.

Ya, check out this quick page on beating biometric sensors
[http://www.theregister.co.uk/2002/05/23/biometric_sensors_beaten_senseless/](http://www.theregister.co.uk/2002/05/23/biometric_sensors_beaten_senseless/)

Really though clicking a link is a big secure risk too.... but that link is all clean.
It is VARY, vary hard to stay secure. Linus Torvalds said that his production computer is not even connected to the Internet. He said that he takes security vary seriously. He's worked for banks and stuff. So you know, he has had to be secure.

---

### Post by svrep on 2010-01-25
> **HunterThomson said:**
> 

However, Facial Recognition is Insecure. There is only ONE camera so it can't tell Depth. SO, you can just hold up a picture of the persons face and the system will let you in. Even if it did have 2 camras to get Depth. Your showing your password (your face) to the world all the time. One could make a sculpture of your face and it would work.

Although certainly true for most implementations of facial recognition, in this case AlienSense (also called FastAccess in the Dell version) has extremely robust photo rejection. It intentionally takes into consideration many evironmental variables such as lighting and face positioning. This makes a standard photo of a user very unlikely to grant access. 

In a future version, AlienSense will also have a feature that FastAccess already does...called "Face + Password". By periodically prompting for just a few characters from your password in addition to a recognition, all questions of photographic access are virtually eliminated. 

Keep in mind too that all security is balance. AlienSense/FastAccess uniquely can fill in a security gap that almost no other software can...an unattended, wide open computer. It can be set to automatically lock your desktop when your face is no longer visible. For most users, an open desktop is a far more common and easily exploited issue than photographic access that is, in reality, quite difficult. 

For a great many details on photographic access and other security topics as it relates to AlienSense/FastAccess, see this comprehensive FAQ. It's written for the Dell version so some of it won't apply, but the general concepts are all very valid. 

[http://www.sensiblevision.com/v/dell/faq.pdf](http://www.sensiblevision.com/v/dell/faq.pdf)

---

### Post by HunterThomson on 2010-01-27
OK, it is settled I am buying one of the bad boys :)

I'v been looking into getting the AlienFX to work in Linux. It seems that the lighting is seen as a USB device so some Linux drivers would need to be written for sure. I was hoping it was just through ACPI (I know ACPI sucks). If it was just ACPI I could have fixed up the BIOS device tables and probably gotten it to work. It mite have just worked anyway with by setting values in the /proc directory. However, this info is from the OLD Area-51 m15x not the new "M15x". So maybe it is deferent in the new M15x.

Do any of you owners see a strange USB device on your computer?

Boy bad naming of their new laptops, bad for googleing. They should have came out with a distinctly new name like N15x or Z15x. Especially sens the Area-51 got kind of bad reviews. But whatever this new one has only gotten grate reviews (as long as you don't flash the BIOS to A03 but all new ones come with it so no problem)

---------
Ya, sure it takes a little/more then a little trickery to get the photo to work for the Facial Recognition but it dose work. Taking advantage of other security weaknesses in Window an Attacker could vary easily take control of the laptop WebCam and take the perfect picture with that. One could even do this remotely with browser based attacks. As for the idea of Facial Recognition + Password. There is no added security. You may as well just use a Password. Also, it is a standard option to lock the desktop when it goes to Screen Saver. Networkmanager also has the option to Lock and Unlock the desktop when your BlueTooth device gets out/in of a predefined range.

Biometrics will never be secure because it is just far to easy to get the needed information i.e. fingerprint, face, even DNA. Then the only thing that needs to be done is to replicate it. Hell, you could even kidnap an employee then cut out his eye and hold it up to the retina scanner. Or Cut off his hand or head. However, there is no way to cut out a Password, as log as the guy is willing to die to keep his secret.

With a long Pass-phrase it is going to take forever to crack no matter what.

Though truth be told, cracking your Windows password it really the last thing I'd try. There are far easier ways to gain administrative access to a Windows box. Certainly if I have physical access to the box i.e. just boot up a Linux live CD or Kon-Boot.

---

### Post by HunterThomson on 2010-01-28
Hum, If the AlienFX are a USB device. Then there is a vary good chance you could pass that device to a Windows VirtualBox and change the lights in there. That would be a vary cool thing.

Hum, looking at your lsusb output it dose seem to have some strange USB device listings.

Bus 002 Device 007: ID 413c:8156 Dell Computer Corp. 
Bus 002 Device 006: ID 413c:8158 Dell Computer Corp. 
Bus 002 Device 005: ID 413c:8157 Dell Computer Corp. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 002 Device 003: ID 187c:0512  
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:6412 Microdia 
Bus 001 Device 003: ID 046d:c52a Logitech, Inc. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The ones that don't have any name ...
Bus 002 Device 003: ID 187c:0512  
Bus 002 Device 002: ID 8087:0020
Bus 001 Device 002: ID 8087:0020

Or maybe it is the Dell Computer Corp.

They mite be the AlienFX devices. Could you run Virtual-box and see if the AlienFX devices are found? Like if they are listed in the menu of USB devices you can pass to the VM.

---

### Post by svrep on 2010-01-28
> **HunterThomson said:**
> 
---------
Ya, sure it takes a little/more then a little trickery to get the photo to work for the Facial Recognition but it dose work. Taking advantage of other security weaknesses in Window an Attacker could vary easily take control of the laptop WebCam and take the perfect picture with that. One could even do this remotely with browser based attacks. As for the idea of Facial Recognition + Password. There is no added security. You may as well just use a Password. Also, it is a standard option to lock the desktop when it goes to Screen Saver. Networkmanager also has the option to Lock and Unlock the desktop when your BlueTooth device gets out/in of a predefined range.

Biometrics will never be secure because it is just far to easy to get the needed information i.e. fingerprint, face, even DNA. Then the only thing that needs to be done is to replicate it. Hell, you could even kidnap an employee then cut out his eye and hold it up to the retina scanner. Or Cut off his hand or head. However, there is no way to cut out a Password, as log as the guy is willing to die to keep his secret.

With a long Pass-phrase it is going to take forever to crack no matter what.

Though truth be told, cracking your Windows password it really the last thing I'd try. There are far easier ways to gain administrative access to a Windows box. Certainly if I have physical access to the box i.e. just boot up a Linux live CD or Kon-Boot.

Certainly your point that all security measures can be bypassed is correct. With unlimited time and physical access to a machine getting in is just a matter of "when", not "if". Theoretical, extreme security situations are also interesting to think about. 

Good real-world security implementation is really not a question of absolutes (or of beheadings), but is one of thoughtfully identifying the most likely vulnerabilities and choosing tools to address them that balance the need to protect a particular set of data with the need to conveniently use the machine. This is no different than choosing the level of security for your house based on where you live and the value of your possessions.   

Absolutely long, complex, highly secure passwords are an *excellent *security measure. The truth is, however, that the average user will choose not to use them because they're difficult to type. AlienSense critically provides convenient login to Windows (actually allowing for *more *complex passwords) in addition to providing a great way to lock the desktop when the user moves away - a vulnerability that for many people is quite common and also easily exploited with no particular time, effort or expertise. Of course there are other ways to lock the desktop and the use of *any *of them is better than leaving the desktop open. This simply gives people another choice - and a particularly strong one, IMO, because it relies on the face being visible instead of standard kbd/mouse timers.

No question that if you're willing to use complex passwords and be strict/consistent with their usage that you will have a highly secure system and may not need something like AlienSense. For the vast majority of people, however, having security that's convenient enough to use 100% of the time is far better than the alternative!

---

### Post by uncon on 2010-01-28
There is a Pidgin plugin (Windows only) for notifications via AlienFX [here]("http://3d.benjamin-thaut.de/?p=11").  You can download the source to get an idea of the protocol for communicating with the AlienFX controller.

lsusb shows the AlienFX controller thusly:
```
Bus 002 Device 003: ID 187c:0512  

```

---

### Post by HunterThomson on 2010-01-31
Owe Uncon that is perfect :)

I've never coded in C I could vary passably be missing something BIG like is it talking to a Driver that is installed on the Windows Box or is it talking to the device firmware?

If it is talking to the device firmware then WOW it would be way easy to write a AlienFX control center for Linux. I'd just need to open one of the 20+ C programing books I downloaded and never looked at :p

Really though I'd start off with just chopping up this code and starting with a command to turn the lights on/off.

----------

SO, if it is in fact just a USB device then I would guess that you can just control it with a Win7 VirtualBox in the meen time.

---

### Post by uncon on 2010-01-31
> **HunterThomson said:**
> Owe Uncon that is perfect :)

I've never coded in C I could vary passably be missing something BIG like is it talking to a Driver that is installed on the Windows Box or is it talking to the device firmware?

If it is talking to the device firmware then WOW it would be way easy to write a AlienFX control center for Linux. I'd just need to open one of the 20+ C programing books I downloaded and never looked at :p

Really though I'd start off with just chopping up this code and starting with a command to turn the lights on/off.

----------

SO, if it is in fact just a USB device then I would guess that you can just control it with a Win7 VirtualBox in the meen time.

There is no specific driver per se.  Based on the research I've done, it seems the AlienFX controller is based on the TI TUSB3410.  I think that it should be fairly trivial to write a command line application to change the settings of the AlienFX controller.  However, I haven't really spent much time to this end.

---

### Post by HunterThomson on 2010-01-31
Right on, Well ETA 2/12/2010 for my M15x so I'll see what I can pull off. Would be a fun thing to do. There are a lot of Alienware users and no Linux control panel for the lights. So, I think it would be a good project to get my name out there :p Selfish I know but hay I got to get a job. Feel free to start on a demo. I'll keep reading up on it and C.

---

### Post by HunterThomson on 2010-01-31
Maybe start with some command line stuff to learn how to talk to the device.

Then build the finished application with a Python frame and write C modules to talk to the AlienFX. Then write a GUI with GTKpy.

Ya, like if anyone reading this is a good C programmer. If you could just write all the C stuff to talk to the AlienFX. Like you don't have to write the a whole program just write all the modules. I can then write the program in Python and just call all your C to do all the real work.

---

### Post by Wattos on 2010-02-06
Hi,

I have started working on a hopefully cross platform AlienFX tool. The front end is being done in java with 3 required JNI calls. Right now I can change the lights in Java on windows but am still working on the low level implementation on linux. I have tried libusb both 0.1 and 1.0 and I keep getting timeouts when trying to communicate with the device. 

If there are people interested in this, I appreciate any help ^^

---

### Post by Wattos on 2010-02-08
I can finally talk to the device on linux. Thanks to Ingrater ([http://3d.benjamin-thaut.de/](http://3d.benjamin-thaut.de/)) I also have the protocol on how to reset and set lights. Since I have done all the hard research now, expect a linux alienFX setting program for the M15x soon. (I hope its this week)

---

### Post by HunterThomson on 2010-02-09
Dude That Is Super Cool ! I just got my M15x and am installing linux on it right now.

I don't know Java vary well at all but once you release a version I'll read the code and see if I can pick it up a little and start doing some little work.

Would be super cool if you could get out a little program just to do some simple light changing and turn on/off.

Keep up the good work. I'll donate some money to you :)

---

### Post by Wattos on 2010-02-10
> **HunterThomson said:**
> Dude That Is Super Cool ! I just got my M15x and am installing linux on it right now.

I don't know Java vary well at all but once you release a version I'll read the code and see if I can pick it up a little and start doing some little work.

Would be super cool if you could get out a little program just to do some simple light changing and turn on/off.

Keep up the good work. I'll donate some money to you :)

Check out [http://ubuntuforums.org/showthread.php?t=1403399](http://ubuntuforums.org/showthread.php?t=1403399) 

No donations needed ^^

---

### Post by moondy on 2010-02-12
just wanted to post to let you know that your work on the AlienFX Lite is much appreciated.

I was about to order this laptop and realised 'hang on, i might not be able to use the fx on ubuntu'...you saved me. :D

i'll order mine this weekend, so i'll let you know when i get mine in 2-3 weeks.

---

### Post by Wattos on 2010-02-12
> **moondy said:**
> just wanted to post to let you know that your work on the AlienFX Lite is much appreciated.

I was about to order this laptop and realised 'hang on, i might not be able to use the fx on ubuntu'...you saved me. :D

i'll order mine this weekend, so i'll let you know when i get mine in 2-3 weeks.

youre welcome. Just released version 0.2

---

### Post by HunterThomson on 2010-02-13
Amazing That was fast ! I posted about it on your thread...
[http://ubuntuforums.org/showthread.php?p=8819707#post8819707](http://ubuntuforums.org/showthread.php?p=8819707#post8819707)

-----

Just want to post about how well this laptop works with Linux.

Totaly Linux compatable. Everything is Plug & Play.

DVD-rom
eSATA <use  scsiadd -s  to HotSwap a eSATA drive>
BlueTooth
Media-Keys
AlienFX
SD card reader
Audio < After running alsaconf everything works no problems with headphones or anything>
Intel WiFi 5300 <Don't get the dell it is Broadcom but they do have and Open Source driver now but no monitor mode with it>


Well the whole thing works with out a problem I don't know what more to say about that.

As for the laptop itself. WOW THIS IT THE BEST LAPTOP I HAVE EVER USED !!!
Go Get one ! It is All medal. NO Plastic.... Well the interior is plastic by the keyboard but the whole rest of it is medal. The back of the LCD panel is all one 1/8" thick sheet of Medal. Vary, vary good build quality.

---

### Post by tstrike on 2010-02-27
> **HunterThomson said:**
> Amazing That was fast ! I posted about it on your thread...
[http://ubuntuforums.org/showthread.php?p=8819707#post8819707](http://ubuntuforums.org/showthread.php?p=8819707#post8819707)

-----

Just want to post about how well this laptop works with Linux.

Totaly Linux compatable. Everything is Plug & Play.

DVD-rom
eSATA <use  scsiadd -s  to HotSwap a eSATA drive>
BlueTooth
Media-Keys
AlienFX
SD card reader
Audio < After running alsaconf everything works no problems with headphones or anything>
Intel WiFi 5300 <Don't get the dell it is Broadcom but they do have and Open Source driver now but no monitor mode with it>


Well the whole thing works with out a problem I don't know what more to say about that.

As for the laptop itself. WOW THIS IT THE BEST LAPTOP I HAVE EVER USED !!!
Go Get one ! It is All medal. NO Plastic.... Well the interior is plastic by the keyboard but the whole rest of it is medal. The back of the LCD panel is all one 1/8&quot; thick sheet of Medal. Vary, vary good build quality.

I agree FIRMLY... GO GET ONE its ... Ubuntu RUNS this Laptop like a WAR MACHINE... full metal jacket... I have a problem with my microphone... the only thing wrong...  I run VMware Server (3 VMs) and it didnt even blink at 90% CPU utilization... Make sure to get 8GB  of RAM... This is a darling machine..

---

### Post by aosmith on 2010-02-28
> **uncon said:**
> I'm not familiar with the issues with the touch pad on the Inspirons.  The Windows driver that is preinstalled on the M15x is very crappy.  I'm not even sure how they managed past QA like that, but it doesn't matter.  In Windows you can just remove the driver and use the MS one.  In Linux this isn't an issue at all.  My touch pad behaves about as good as any other I've used.


I avoid them on my m17x... they seem to cause kernel panics for me.

---

### Post by AndersAA on 2010-02-28
I just found a rather interesting bios issue...

Boot the system, run glxgears, the driver I run I get around 3700fps.
I turn stealth mode on with the button, it drops to 3600fps.
I turn stealth mode off again.... and look and behold, 8200fps.


Stealth mode for me doesn't seem to affect cpu scaling at all, but the gpu is defenatly affected.

---

### Post by HunterThomson on 2010-03-31
I would like to add that the built in microphone works Out-Of-The-Box with Skype. Just leave it all set to defaults.It is vary sensitive though. I found it works a whole lot better if I turn off one mic.

I go into ALSAmixer and set the "Front Mic" to it's lowest setting of "33"
Then I found that turnning off the "Left" Mic and leaving the "Right one on was the best. However, maybe you will have a better "Left" Mic then "Right" Mic so play around.

I have always found true with all laptop Mic's. The manufactures are crazy for putting 2 Mic's in the laptop. It sounds like crap with 2 Mic's. There is far to much ambient sound picked up. Maybe Windows drivers like so some special filtering or something but they sound 10x better with one Mic turned off.

----------------

Wow AndersAA, I didn't think that Stealth Mode bottom did anything in Linux. However, I just tried it out with glxgears and it certainly is throttling the GPU. I don't get the strange boost like you do afterwards but when it is on it is slower. One thing that could have messed up your test was because glxgears only uses ONE Logical CPU Core... It's only one thread (not really a benchmark but it "can" give a general idea if the GPU is being throttled) So, maybe when you ran glxgears the first two times it was on a Physical Core that was running 2 Threads "Hyper Threading" and the time you ran it after you turned the Stealth Mode off it was the only Thread being processed by the Physical Core it was on.

GLXgears Stealth Mode Touch Button "Test"
( Every time glxgears was run it was the only thread being processed by the Physical CPU Core it was running on )

Screen - 1920x1080p
Mem - 4GB 1333 DDR3 RAM 
CPU - Intel Core i7-720QM
Graphics - Nvidia GTX 240M 1GB VRAM


 - First run -
glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
24437 frames in 5.0 seconds = 4887.236 FPS
24438 frames in 5.0 seconds = 4887.575 FPS
24458 frames in 5.0 seconds = 4891.407 FPS
^C

 Touch Sensitive "Stealth Mode" Button Pressed

 - Second Run -
glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
15259 frames in 5.0 seconds = 3051.613 FPS
15281 frames in 5.0 seconds = 3056.137 FPS
15275 frames in 5.0 seconds = 3054.833 FPS
15277 frames in 5.0 seconds = 3055.339 FPS
15271 frames in 5.0 seconds = 3054.005 FPS
^C

 Touch Sensitive "Stealth Mode" Button Pressed

 - Third Run -
glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
24473 frames in 5.0 seconds = 4894.415 FPS
24498 frames in 5.0 seconds = 4899.592 FPS
24503 frames in 5.0 seconds = 4900.448 FPS
24511 frames in 5.0 seconds = 4902.031 FPS
24499 frames in 5.0 seconds = 4899.697 FPS
24507 frames in 5.0 seconds = 4901.320 FPS
^C

---

### Post by stmiller on 2010-04-03
Guys and gals - be advised turboboost is only in the 2.6.33 and later kernel. 

So you'll need to roll your own 2.6.33+ kernel.

---

### Post by AndersAA on 2010-04-03
> **stmiller said:**
> Guys and gals - be advised turboboost is only in the 2.6.33 and later kernel. 

So you'll need to roll your own 2.6.33+ kernel.

It's backported to the 2.6.32 lucid kernel as well.

---

### Post by HunterThomson on 2010-04-10
> **stmiller said:**
> Guys and gals - be advised turboboost is only in the 2.6.33 and later kernel. 

So you'll need to roll your own 2.6.33+ kernel.

What kernel is Ubuntu on now? I am running Archlinux on it with kernel 2.6.32 and it has TurboBoost working.

Use the tool i7z to monitor the CPU Core freq's. 
I also had to install and run cpufreq with all defaults and the Performance governor.

For more information on the read my the last post in a thread about it...
[quote=hunterthomson]
Intel Core i7-720QM
Rated speed 1.6GHz - Max Turbo Speed 2.8GHz

Bus clock frequency 133MHz

Lowest CPU Multiplier (7x) // Rated CPU multiplier (12x) // Max Turbo multiplier (21x)
   7x 133 = (931Mhz)       //   12x 133 = (1596MHz)      //   21x 133 = (2793MHz)


# (The folowing seems to be true.)
#
# MAX Multiplier that Turbo Boost can add = 9x
#
# 7x + 9x = 16x
#
# 12x + 9x = 21x
#
-----------------------------------------
I really don't know all that much ether. Just what I have read and observed from my Mobile i7-720QM Quad Core CPU

It seems not to be optimized for Nehalem in the sens of getting the most use out of the CPU. It seems to just truncate each thread as it comes in. Like the first thread go's to core 0 the second thread go's to core 1 the thread thread go's to core 2...... But doesn't try to get them on the Logical cores in any sort of optimized way. Like it doesn't try to put 4 threads on 4 Physical cores to make the most use of the L1,L2 cache nor dose it try to consolidate threads on the least # of cores to gain the highest frequency.

By default the CPU will sit at it's LOWEST clock multiplier,

7x for the i7-720QM   i.e. 7 x 133MHz = (931Mhz)

Then when a Pysical Core is put under load the Turbo Boost will only add it's multiplier boost to that lowest possible multiplier of 7x. So it results in the CPU running BELOW Rated Clocks speed under load i.e. Under 12x 1.6Ghz

That SUCKS !.... However,

I run cpufreq with the default "Performance" governor. The "Performance" governor is suppose to run the CPU at Max reported clock speed all the time. That would be 1.6Ghz or 12x multiplier. However, It Dose Not Do That. When a core is unused the clock speed will drop all the way down to 7x 931Mhz. BUT if the core gets the slightest load at all, the clock speed for the physical core will jump up fast to 8x -> 21x.

What seems to be happening is that the cpufreq "Performance" governor will tell the CPU to run at Max reported clock speed of 12x 1.6Ghz. BUT then "Intel Speed Step" will Under clock the core if it is not in use back down to 7x. Then if the core is used "Intel Speed Step" will stop under clocking and set it to 12x. Then Turbo Boost will add it's multiplier to 12x. This results it the expected behavior of Clock Multipliers Higher then 12x on cores that are under load. HOWEVER, I still see clock multipliers between 7x and 12x like 8x,9x,10x, and 11x. So, there must be more to the story.[/quote]

---

### Post by stuart_d_buchanan on 2010-09-28
> **HunterThomson said:**
> 
GLXgears Stealth Mode Touch Button "Test"
( Every time glxgears was run it was the only thread being processed by the Physical CPU Core it was running on )

Screen - 1920x1080p
Mem - 4GB 1333 DDR3 RAM 
CPU - Intel Core i7-720QM
Graphics - Nvidia GTX 240M 1GB VRAM


 - First run -
glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
24437 frames in 5.0 seconds = 4887.236 FPS
24438 frames in 5.0 seconds = 4887.575 FPS


Hi there,

I've  got the M15X with the GTX 260M card, run 10.04 LTS (Lucid Lynx) and  have been having real difficulty getting the expected levels of  performance out of it for FlightGear. I've been assuming that the  problem is related to PowerMizer, which sits at  Perf Level 1 (275MHz),  and never runs at the full 950MHz.

When I run glxgears, I'm  getting just under 20686 frames in 5.0 seconds, slightly lower than you  are reporting with the GTX 240M. So, I've got a couple of questions:

1)  Is there still an issue with PowerMizer over-throttling the GPU, and is  there a valid workaround for the 260M (I've tried many of the generic  suggestions on the forums here without success).

2) Have I missed something really obvious to get better GPU performance?

Thanks very much for your help,

-Stuart

---

### Post by AndersAA on 2010-09-29
> **stuart_d_buchanan said:**
> Hi there,

1)  Is there still an issue with PowerMizer over-throttling the GPU, and is  there a valid workaround for the 260M (I've tried many of the generic  suggestions on the forums here without success).

2) Have I missed something really obvious to get better GPU performance?

Thanks very much for your help,

-Stuart

1 : Yes, on the m15x. No there are no workarounds. I've talked to dell, they talked to nvidia. Nvidia pretends it's not an issue and won't pay for it.
2 : I just ordered a 5850 card from dell less than 5 minutes ago.


instability with m15x + 260M (stealth mode trixing makes it better, but does not solve it):
[http://www.nvnews.net/vbulletin/showthread.php?t=142946](http://www.nvnews.net/vbulletin/showthread.php?t=142946)
powermizer still broken:
[http://www.nvnews.net/vbulletin/showthread.php?t=141116](http://www.nvnews.net/vbulletin/showthread.php?t=141116)

---

### Post by heron7 on 2010-10-28
DO NOT remove windows if you are thinking of installing any linux OS's on the Alienware, if you still Need to have linux than do it on a separate partition on the drive ,not even along side windows. and that is if you've asked for a large enough disk drive. 
You'll get yourself in such a **** storm or trouble my friend that you're head will spin faster than the wheels on that twin bike ... ;) 
I have the Alienware M15x ,It was Nice all powerful all eye candy etc ,till a glitch occurred & that was less than two months after I had him ,to no action of my own he just didn't boot one SAD morning ,four mnts ago ,guess what I was doing this weekend. :)
Another thing ,When One buys such a machine it is not to do Edubuntu or any other thing but play games & EVEN UBUNTU Will Advice you against installing & removing widows.. Dell will tell you that TOO on the site for drivers etc linked with Alienware ..
Good luck 
& to all the rest that drool over the Alien ,well there are tons of other machines out there who are by far more stable & fun to play games too. All the alienware has diff is looks ,which in time will ware off ,even annoy you ones they  decide to go for a holiday on you & send you to the psych ward .

---

### Post by AndersAA on 2010-10-29
> **heron7 said:**
> DO NOT remove windows if you are thinking of installing any linux OS's on the Alienware, if you still Need to have linux than do it on a separate partition on the drive ,not even along side windows. and that is if you've asked for a large enough disk drive. 
You'll get yourself in such a **** storm or trouble my friend that you're head will spin faster than the wheels on that twin bike ... ;) 
I have the Alienware M15x ,It was Nice all powerful all eye candy etc ,till a glitch occurred & that was less than two months after I had him ,to no action of my own he just didn't boot one SAD morning ,four mnts ago ,guess what I was doing this weekend. :)
Another thing ,When One buys such a machine it is not to do Edubuntu or any other thing but play games & EVEN UBUNTU Will Advice you against installing & removing widows.. Dell will tell you that TOO on the site for drivers etc linked with Alienware ..
Good luck 
& to all the rest that drool over the Alien ,well there are tons of other machines out there who are by far more stable & fun to play games too. All the alienware has diff is looks ,which in time will ware off ,even annoy you ones they  decide to go for a holiday on you & send you to the psych ward .

That's.. rubish. Dell advices against doing anything to the stock setup. Ubuntu does not advice against removing windows (unless your very new to linux I suppose). And the alienware is not a tool to play games, it's a computer. And more importantly for me, it's a quiet powerhouse. I actually do use it for civilization 5 and starcraft2, but both of those I play on linux.

Of course if you get a tech in house and it's not immidiatly obvious to him it's a hardware problem you might get a problem, as they most likely are too clueless to do debugging from a linux system. Then again I've met dell tech's with linux bootable cd's for debugging... And I've had hardware replaced by warranty in this 3 times, there was never any problem with me running linux.

---

### Post by heron7 on 2010-11-10
I totally agree with you,that is rubbish. 
I would never say that Linux can't run on Alienware.Linux can run anything if you Know How.ANYTHING! 
I came here or rather was redirected back here via google because I was asking it 'Linux on Alienware',again. Not because it can't but hopefully it would land somewhere where it will tell me How,in lame words only for a fool like me :(
Sure PlayOnLinux & Wine etc.and apparently Fedora 14 has something going along the lines of 'mending' these incompatibilities,if I understood the article correctly.
I am not much with that,unless I get really acquainted with them well enough to install the missing dll's ,drivers,functions,etc.
I have just installed Kubuntu 10.10 on It & i'm typing this on Ubuntu 10.04.I bought a third machine where i swore i would not put another OS cd next to it,because I can't do a Setup the way it should be.
I buy monthly 3 Linux mags & have recently bought the Official Ubuntu Book & Mark G. Sobell's 1000pgs of Linux's Guide. 
Maybe i should be there immersed in the books instead,but time,patience & concentration are not my virtues.
I could not & would not diss Linux,or any other OS.

As for the Alienware ,sure it's a Powerhouse & then some.It weighs more than my first Mac Desktop. The cpu is insane etc ,but there are NO buttuns. nada. all sensors & when the lights go & you need to reinstall at some point after failling to bring him back to the original factory settings,becuase of jumping to fast on that recovery disk.
If You need to start from scratch.That includes all the function keys too. There is'nt an eject button.I have stickers to point out where the wifi,sound & eject 'which does'nt work anymore' etc .I paid close to 1800Euros for it.
There's nothing to fall back on to if anything goes wrong,& I've even read that apperantly Dell supplied a damaging recovery disk,that potentially messes up the motherboard.
I had asked where there the firmware was baiest from windows to linux ,if the same firmware cd i burned could be run on boot and i did'nt get an answer for that.I did'nt check back anymore after a week,& anyways it's all written somewhere in the 2000pgs of A Practical Guide,i'm sure,but not that it's the same as for a laptop like Alienware m15x,because of all the sensors.let alone Command Center.I could live without the lights no problem but not half a machine.The bluetooth or Intel's graphic card ,well run lsusb. & then ..  
It's me, i am the one to blame not Alienware NOR Linux.I fell for the looks on a webpage& sent that money without me even seeing it .Probably i would'av still bought it,because i did'nt understand the drawback of it not having actuall buttons.
Lenovo's think pad, Dell's Inspiron,The MacBook..all cheeper

---

### Post by oggie on 2011-03-07
Does anyone know if the cooling fan is working correctly on this machine and 10.10? I have a new m15x and I never hear the fan come on, even when I'm compiling code.

X has restarted on me before as well while in the middle of a build. 

I am able to monitor the CPU temps and I see them go up to 53 degrees celsius and still no fan activity at all. 

Is there a tool you can use to turn the fans on/off and adjust the thresholds of the fans?

---

### Post by AndersAA on 2011-03-08
It's working perfectly fine for me, and always has.

Note that 53c isn't all that much when we're talking cpu temperatures. If I remember correctly the max temperature for an i7 is 100c.

---

### Post by oggie on 2011-03-08
I've rebooted and now the fans seem to be running even though they weren't before. 

I do wish there was some way to monitor the fan speed though.

---

