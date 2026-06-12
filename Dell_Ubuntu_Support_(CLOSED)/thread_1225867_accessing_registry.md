---
title: "accessing registry"
date: 2009-07-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hello2007 on 2009-07-29
how can i access vistas registry from ubuntu like how i can access vista program files from ubuntu?

---

### Post by mtbsoft on 2009-08-03
The Windows registry is a set of data files which are accessed through a specific API which has been wrapped up into the Windows program regedit, it is therefore not data which is readily available, unlike the file structure which is.

The only easy way to access the Windows registry is to run regedit while running Windows.  It is theoretically possible that you could write a program to access it from Linux but that's really going at it the hard way and begs the question... why do it?

Your only other alternative might be to run Windows and export the segment of the registry you require to a text file which you could then access from Linux through a simple editor.

---

### Post by hello2007 on 2009-08-03
im interested in accessing the registry from ubuntu because my vista os wont boot up because i put 2 anti viruses on my computer so I need to delete them so i can get my vista os back running and there is no way to delete beleieve me i tried everything so i would like to access the registry from ubuntu so by then i can search the antiviruses and delete the registry i already deleted there files through ubuntu. So if its possible let me know

---

### Post by gbrainin on 2009-08-03
There are registry editors under linux (google: linux windows registry editor), or you can run regedit under WINE.  The tricky part may be the windows file structure itself, since you're running Vista.  Last time I checked, linux support for NTFS was still a bit shaky.

---

### Post by hello2007 on 2009-08-03
i ran regedit under wine and it just showed ubuntu stuff it didnt show anything from the vista side

---

### Post by gbrainin on 2009-08-03
Yes, you'd have to make regedit look at the other drive, not the fake windows drive that WINE sets up.  I have no idea how you would do that with regedit; according to the internet, somewhere in the file menu should be an option to "load hive."  Perhaps that will get you started.

---

### Post by mtbsoft on 2009-08-03
> **hello2007 said:**
> im interested in accessing the registry from ubuntu because my vista os wont boot up because i put 2 anti viruses on my computer so I need to delete them so i can get my vista os back running and there is no way to delete beleieve me i tried everything so i would like to access the registry from ubuntu so by then i can search the antiviruses and delete the registry i already deleted there files through ubuntu. So if its possible let me know

Sounds to me like the problem goes deeper than the two A/V programs then.  If you have deleted all the program files for the two programs (and I mean all, including those in the windows systems areas) you should be able to start wondows, at least in safe mode, without the A/V software interfering.  If you cannot, it's likely that some of the system files of windows itself have been corrupted.

As gbrainin says, regedit under Wine will not look at the alternate drive, it looks at its own wine install for the registry files and, frankly, I'd be very cautious about running regedit through wine->linux->ntfs-3g->Vista, there are just too many variables and too many options to go wrong.  You might be safer to put the drive in another Vista machine and use that to patch the registry, but I still think the problem doesn't sound like the A/V.

Can I ask why you put two A/V on in the first place (I've done it with XP before with no difficulties)?  Was there an infection already before you put them on?  Which A/V did you use?

---

### Post by hello2007 on 2009-08-04
no i just deleted the a/v files in program files and on desktop i didnt find any others where would i look to find others if you can assist? I installed avast and then avira months later with no problems at all then i decided stupid me to try kaspersky and boom as soon as that dam program got onto my computer nothing worked again, it was my fault i should i completely uninstalled avira and avast first but thought whats really that big of a deal if there is any problems ill just go into safe mode but the worst of the worst happened i cant access anything windows related

---

### Post by kayvortex on 2009-08-04
Yeah, I tried running two AV programs at the same time (inquisitive nature, I guess), which resulted in the whole computer running slower than I've ever seen anything move at all (except Windows '98, that is).

I'd also recommend not editing the registry through wine: just too risky, especially when you can just mount the Windows partition and simply rename the Program Files folder of one of the AV programs. Then, just start your system up, uninstall the other AV program and rename the Program Files folder back again. That'd probably be the simplest thing to do.

---

### Post by hello2007 on 2009-08-04
i cant even find the a/v files anywhere anymore since i deleted the files through ubuntu. thats why im so fixed on getting into the registry, really guys its my only shot next to reformatting the c drive. If anyone can help me out that'll be great

---

### Post by kayvortex on 2009-08-04
Well, if you've already deleted the files, then Vista should be able to boot. I'm no expert on the Windows registry, but that alone shouldn't stop your system from booting (unless AV software does some very strange things in the registry now). Have you tried booting into safe mode? Does that work?

Instead of wine, you could try [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12"): it's a bootable CD that lets you repair Windows machines. You'll have to [read up]("http://trinityhome.org/Home/index.php?front_id=12&wpid=7#regedit") on what to do though. I suspect that if TRK can't do it, then probably nothing else can.

---

### Post by hello2007 on 2009-08-04
> **kayvortex said:**
> Well, if you've already deleted the files, then Vista should be able to boot. I'm no expert on the Windows registry, but that alone shouldn't stop your system from booting (unless AV software does some very strange things in the registry now). Have you tried booting into safe mode? Does that work?

Instead of wine, you could try [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12"): it's a bootable CD that lets you repair Windows machines. You'll have to [read up]("http://trinityhome.org/Home/index.php?front_id=12&wpid=7#regedit") on what to do though. I suspect that if TRK can't do it, then probably nothing else can.


no boss i heard that the registry's are key to cleaning your program from your computer it can stop your compter from booting up. So i feel very sure if i can just get to those registry's ill be in the clear. Ill give trinity kit a try too why not.


dont mean to be negative but after looking at trinity i dont see how it would help my problem it seem's no different than any other rescue kit. It won't help me get into windows or delete the a/v's it seem's

---

### Post by mtbsoft on 2009-08-04
I'm sorry but you seem to be placing far too much emphasis on editing the registry being the answer to all your ills.

Yes, the registry is key to the correct functioning of Windows but leaving keys in the registry for software which you have deleted should not be able to interfere with Windows running in safe mode, unless it is very shonky software or doing things against all the rules, in which case too much damage has likely already been done.

My guess is that your windows installation has already been badly corrupted and that it is the windows part that is corrupt, not the A/V software.  If that is the case, Windows needs to be fixed, not the A/V software - not something you can do simply by editing/deleting keys in the registry.  The registry is a very complex area of windows and should not be edited by someone inexperienced, you will almost certainly do more damage than good.

It is quite possible that you have not deleted all the files for the A/V software - these things tend to install in low level areas - and you are still getting some parts of the software loading but again this should not be able to interfere with safe mode.

My recommendation would be to copy anything of value off the windows partition, reinstall vista, reload grub to reinstate your dual boot and put your data back.  To try and fix a clearly corrupted windows install as bad as this sounds to be seems to be far too much hard work.

Either that or simply still with Ubuntu and ditch the 'doze.

---

### Post by kayvortex on 2009-08-05
Yes, the registry *can* stop Windows from booting (because it does store important information), but that doesn't mean it *will* (because it also carries fairly mundane information): that's my understanding of the registry (which may be wrong, so I apologize if it is).

Like *mtbsoft* has already said, even if you do delete the registry keys you want, I wouldn't be surprised if you still find your system in a mess. Personally, I use excuses such as this (and a lot less) to do a clean install of Windows. That's my advice: boot into Linux, copy over all the files you want, and then clean install. (Usually the best answer to *all* Windows problems for anyone who's taken the necessary precautions!)

Still, I'll try to help you with finding a registry editor as much as I can (which will be very little, I'm afraid). TRK should work: although I've never tried it myself, it should have the ability to locate your windows installation and repair it. I don't know what you mean when you say "no different than any other rescue kit": rescue kits are designed to locate your installed software and be able to repair them. Why wouldn't TRK work?

---

### Post by hello2007 on 2009-08-05
ok im going to try the cd. In the meantime what other places can i look to find a/v files.

i already would of installed windows but i still need to order cables for my hard drive that i just got so might as well try stuff

---

### Post by kayvortex on 2009-08-05
Well, the executables *should* only be in its Program Files folder, but there *could* be things in the Windows or System32 folders: there's no way to tell how sloppy the program makers have been, or how the AV program works (and so what low-level programs remain, and how they worked); so, these things *could* be anywhere. Also, unless they're named really obviously (which is hardly ever the case), you'll have no practical way to know which program belongs to what. You could check the file's properties and creation dates etc., but that's a job that you couldn't pay me to do!
Windows truly is a mess in more ways than one...

---

