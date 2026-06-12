---
title: "Will Wine eventually be incorporated into Linux?"
date: 2005-12-31
forum: General Help
---

### Post by handy on 2005-12-31
Does anyone know, or have any worthwhile thoughts on the future possibility of Wine developing to a level where the free & legal replacement windoze API's will be incorporated into Linux?

Cheers,

handy

---

### Post by zoiks on 2005-12-31
It pretty much "is" in Linux already.  It's an available package for most of the x86-based distros.  There might be some patent threats and things of that nature that keep it from being a default package.  If you are thinking making it part of the kernel I seriously doubt that.

---

### Post by briancurtin on 2005-12-31
i hope it goes away, but thats just me. i dont think it will become any more integrated.

---

### Post by Omnios on 2005-12-31
When they get it stable it may prove an important part for people who dual boot and possibly result in a lot more pure Linux installs. It will probably be available with all Linux distros. Thants my own oppinion though. Its just one of those things associated with wanting certain win programs.

---

### Post by az on 2005-12-31
[QUOTE=handy]or have any worthwhile thoughts on the future possibility of Wine developing to a level where the free & legal replacement windoze API's will be incorporated into Linux?
[/QUOTE]


I doubt that any framework is in the works beyond the work done on wine itself.   I heard that the latest release of wine was now considered beta, as opposed to whatever they called it before (not even considered alpha software)

That is significant.  I think it means that what it can do, it does properly.

What other replacement windows APIs are there?

---

### Post by ATAQ on 2005-12-31
Its already fully integrated into Mandriva, SuSE & Fedora (as I know of).
But personally I hope that Wine never becomes any more than it is. Sure It may be handy and all, but supporting Linux Native programs is also pretty important.
And Linux applications are very fast, no need to slow down time with wine.

---

### Post by jdong on 2005-12-31
Well, there's no such thing as "Linux" (the entity) except the kernel, and Wine is unlikely to go into the kernel -- it doesn't need to.

Most distributions of Linux integrate WINE to some degree, but right now it simply isn't useful enough (try installing recent commercial Windows software using WINE, and you'll understand what I mean) to be adopted on such a wide scale.

Hopefully that will change in the future. It'd be cool to have the WINE layer to be fully functional and feature-rich. Not only is it a binary "emulation" layer for running Windows apps on *nix, but it is also a **porting tool** that makes it EXTREMELY easy for Windows application writers to port their source code over to Linux.

I'd also like to see closer GUI integration with WINE and QT/GTK/KDE/GNOME, so that WINE apps don't look so out of place.

---

### Post by briancurtin on 2005-12-31
wine wasnt "fully integrated" into SuSE last i checked. its just installed off the discs.

i dont exactly call that fully integrated

---

### Post by jdong on 2005-12-31
You mean "installed by default"?

As I said, unless WINE becomes more useful in its default state (i.e. able to do much more out of the box), most distributions will not bother to advertise WINE any more than they need to.


Don't get me wrong -- I'm a WINE user too; if it wasn't for WINE, I couldn't do my robotics programming work under Linux. However, at this point offering WINE more readily will bring nothing but disappointed and confused Linux newcomers wondering why their Windows programs won't install under Linux. False hope is evil.

---

### Post by ATAQ on 2005-12-31
Well thats what I meant, its still pretty much integrated, checking a box aint exactly a heavy work load of effort to install it, so I call that integration.
I would not class wine as very usefull anyways. only very basic windows applications run under it anyway.
So it isnt exactly essential.

---

### Post by jdong on 2005-12-31
Also, it's a relatively huge app, so when default install or medium size is a concern (almost always the case), WINE is easily considered for omission.

---

### Post by az on 2005-12-31
If I remember correctly, if you add universe to your repositories and install wine, clicking on an .exe in nautilus runs it in wine without you having to set a default run action or anything.

---

### Post by jdong on 2005-12-31
I believe you also need the recommended binfmt-misc package (unless it's a required package now) in order for that to work.

---

### Post by az on 2005-12-31
No, I am not talking about the command line thing.  I am talking about the gnome thing.

I am quite certain (but not in front of an ubuntu computer right now) that I only ever installed the wine package and not binfmt-support and nautilus knew to use wine.

Binfmt-support is a recommends, and not a dependancy of wine in Hoary.  It is not even a suggested package in breezy.

---

### Post by jdong on 2005-12-31
Hmm, most likely that's a default MIME association. I know I've configured my KDE's back in the days (KDE 3.1.2 on Knoppix) to use "wine %f" when dealing with the EXE mime-type.

But if a file is marked executable and binfmt-misc is installed, then wine will be automatically called as the executable format handler whenever the command is executed. That's how I've been coding my robotics scripts that wrap around a set of Windows command line compilers.

---

### Post by handy on 2005-12-31
Wine is a pain in the neck for 64 bit users.  Unless you really need it, it seems not worth the trouble of setting up a 32 bit system in parallel before you even start down the Wine path...

handy

---

### Post by jdong on 2005-12-31
Well, yeah.... by design, running 32-bit binaries in a 64-bit emulator designed for 32-bit programs in a 64-bit host operating system will be a bit weird....

You can emulate win64 binaries (the non WoW64 binaries, though) using 64-bit wine, and 32-bit wine will not do those at all. Or you can use gcc -m32 to compile 32-bit binaries of WINE under 64-bit Linux. Or you can set up a 32-bit chroot, which will also allow you to use other native Linux stuff that doesn't work in 64-bit mode.

---

### Post by Canuckelhead on 2006-01-01
I would hope to see less wine.  I would like to see more linux ports.  Seriously in alot of ways wine is a workaround.  I dont like adding levels of complexity.

---

### Post by cvcaelen on 2006-01-01
> Will Wine eventually be incorporated into Linux?

I hate wine,
it's acting up on me and nobody seems to know why

that said,
I hope we don't need wine in the future
that there come linux-programs that do the same as their windows-equivalents(like the Gimp, or open-office and such)

so, for me ,there should be no need to incorporate wine into linux

Christiaan

---

### Post by handy on 2006-01-01
Unfortunately, WINE seems to be a  stop-gap measure, that some very dedicated developers have been working on for years to help fill the community need where windoze software is desired/required.

It seems that WINE can make a mess of Ubuntu, & if you happen to be running 64bit hardware, & you then need to chroot32, you have turned the beautifuly elegant Ubuntu OS, into something that it is not...

So, it looks like patience & having to boot into xp, from time to time is the order of the day, for me atleast...  :razz: 

Thanks for your input,

handy

---

### Post by az on 2006-01-01
[QUOTE=handy]where windoze software is desired/required.
[/QUOTE]

For most people, that zone is nonexistant.

---

### Post by jdong on 2006-01-02
[QUOTE=Canuckelhead]I would hope to see less wine.  I would like to see more linux ports.  Seriously in alot of ways wine is a workaround.  I dont like adding levels of complexity.[/QUOTE]

Wine is also a porting tool (wine-gcc) for creating native Linux binaries from Windows sources.... That's how Borland ported its Delphi suite to Linux.

---

### Post by briancurtin on 2006-01-02
[QUOTE=azz]For most people, that zone is nonexistant.[/QUOTE]
hopefully that zone becomes extinct for all users

---

### Post by jdong on 2006-01-02
[QUOTE=azz]For most people, that zone is nonexistant.[/QUOTE]

But for others, there are some special pieces of commercial software for which an OSS replacement isn't possible or convenient... and for those cases WINE really does help out until either:

(a) Manufacturers start noticing the Linux market
(b) WINE becomes so advanced that it has nearly 100% success in running Windows apps with seamless desktop integration.


Both seem kind of in the future right now, and it's pretty hard to figure out which'll come first!

---

### Post by handy on 2006-01-02
& for some of the noobs like me, it is just a matter of growing more accustomed to Ubuntu (in this case), developing our skills, so we can take advantage of the many tools & app's available.  This in itself can be all it takes to kick the windoze dependency.

Personally, I can't totally kick-IT, while ever I have customers running  windoze.  IT just highlights the difference between work & pleasure...  :D

Cheers,

handy

---

