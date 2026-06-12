---
title: "Printing from OpenOffice.org = Generic Printer"
date: 2005-06-25
forum: Desktop Environments
---

### Post by John Jason Jordan on 2005-06-25
Today is my day to get my printer set up finally. It is a big-ass Laserjet 5SiMx network printer. This is a PostScript Level 2 printer, has four paper trays that hold 3000 sheets, including up to tabloid (11 x 17) or A3.

Using the New Printer I got it set up. However, the test page insisted on printing from tray 1 (manual feed), even though I had the printer properties set to "automatically select." From Windows "automatically select" means print in priority from trays 1, 2, 3, and then 4, choosing the first one that has the kind of paper in it specified by the application print dialog box. At the time I sent the test page job tray 1 was empty and tray 2 was full. Nevertheless, the job paused until I walked over and manually pushed the buttons on the printer control panel to force printing from tray 2. This is not a good sign. :(

Then I decided to try FireFox. I had a page from Adobe.com open, so I just printed it. This worked great -- pulled from tray 2, duplexed, etc.

And then I tried OpenOffice.org Writer. This is the application I print from the most. And none of the options that this printer is capable of were present -- because the printer was not listed. Instead it listed only "Generic Printer."

I tried everything I could think of (shutting down Writer and restarting it, etc.) to get it to see the printer, but have had no luck.

I hope this isn't a harbinger of things to come. Does anyone know what I have to do to tell OpenOffice.org to look in the printer folder for available printers?

---

### Post by Jarz Corp on 2005-06-26
Hi

This is an already registrered bug in openoffice that won't be solved before openoffice 2, some people have suggestions for solving it but I haven't gotten any of them to work. So I use abiword which is an open-source alternative or when worst comes to worst I publish pdf which is a stupid workaround.

---

### Post by John Jason Jordan on 2005-06-26
Since I posted that I posted the same problem in an OpenOffice.org e-list, and now have way more experiences to relate.

First, the version I have installed by default with Ubuntu-64 is 1.1.3. The current stable version is 1.1.4, so someone suggested I try that. However. I can't find any debian repository for it, nor can I even find a tarball for it.

Someone else suggested just installing the current beta of 2.0, which is getting very close to final release. The reason for going to 2.0 beta is because 2.0 changes the printing system completely and just uses whatever printers are installed in the system. Synaptic lists three 1.9 sources if you enable Universe. So I decided to go ahead and install them Unfortunately, each file crapped out with an error message about a missing file.

So then I downloaded the tarball for the latest beta from Sun. I made a folder for it and untared it. And then I was dismayed to discover that it was all RPMs. No .debs. So I went back to Sun looking for a .deb, but came up empty-handed. However, I did find a link to a page where someone gave instructions for using alien to convert the RPMs to .debs. I followed the instructions, but ended up with a page and a half of error messages and no .debs were created.

Then someone told me that OpenOffice.org 1.1.3 calls the default printer the "Generic Printer." Thus, it really was using my printer. (I have only one installed, so it must be the default.) This person did not offer any explanation for why a print job sent via this "Generic Printer" went into the ether somewhere instead of to the printer. However, he did say that to get the functionality in "Generic Printer" I could use spadmin, a GUI utility that comes with OpenOffice.org.

I found spadmin and launched it. However, as soon as I clicked on a button to do anything in it, it just disappeared from my desktop. I tried all the buttons and never could get it to stay up long enough to use it.

So that's as far as I've gotten. Still can't print from OpenOffice.org to my printer on the ethernet. 

This totally sux.

---

### Post by Jarz Corp on 2005-06-27
More or less the same experience I have had, except I didn't go for oo2 beta, I just went to abiword, which solves my day-to-day writing needs for now.

Forget all the jibberish about oo calling the default printer generic, and forget about using spadmin as it is buggy as heck.

Are U on a 64bit system, because I have installed 4-5 (i386) based systems and none of them had this problem with oo.

I will have a look at the 2.0 beta and see if I get errors as well, if not we can try to cooperate on this one.

---

### Post by John Jason Jordan on 2005-06-27
[QUOTE=Jarz Corp]More or less the same experience I have had, except I didn't go for oo2 beta, I just went to abiword, which solves my day-to-day writing needs for now.

Forget all the jibberish about oo calling the default printer generic, and forget about using spadmin as it is buggy as heck.

Are U on a 64bit system, because I have installed 4-5 (i386) based systems and none of them had this problem with oo.

I will have a look at the 2.0 beta and see if I get errors as well, if not we can try to cooperate on this one.[/QUOTE]

I'd be happy to cooperate, to the extent I ca. My problem is lack of knowledge. But otherwise, count me in!

---

### Post by Jarz Corp on 2005-06-27
No one person has "enough" knowlegde dont worry about it.

I have sent U a private message please read that. I am looking into oo2 beta right about now.

---

### Post by Jarz Corp on 2005-06-27
Okay I landed where U often do with linux on a 64bit system, oo2 doesn't exist in an 64bit version, so there U go yet another app I can't run, this one I can live without though unlike the other stuff 64bit linux is missing.

Yet another reason to use a true open-source solution like abiword.

I feel stupid that I tried fiddling with this, Sun systems are behind oo and they don't do anything microsoft/intel doesnt want them to do, which is why we are missing java 64bit (in an up to date version) and stuff like oo2.

---

### Post by John Jason Jordan on 2005-06-27
[QUOTE=Jarz Corp]Okay I landed where U often do with linux on a 64bit system, oo2 doesn't exist in an 64bit version, so there U go yet another app I can't run, this one I can live without though unlike the other stuff 64bit linux is missing.[/QUOTE]

But I have OOo 1.13 installed and running fine on my Ubuntu-64 system, other than the printing problem. Are you saying that 1.1.3 is 64-bit, but 2.0 is not? That doesn't make any sense.

But then, I have another issue with the 64 bit vs 32 bit thing. I can understand driver issues, because they have to access hardware directly. But don't all 64-bit OSs these days "translate" legacy apps so they will run? Like, Microsoft has had 64-bit Windows (Enterprise) for some time, and will soon release a 64-bit version of XP. Can you imagine the screaming if a user upgrades to 64-bit XP and none of their old apps will run?

Furthermore, is it not true that all the currently available Intel and AMD 64-bit chips will run in 32-bit mode for legacy stuff? I could swear I read that somewhere about the Athlon-64 chip in my Compaq laptop.

I can understand that there might be an occasional problem with one or two 32-bit apps, but surely 64-bit Ubuntu can run 32-bit apps. Right? In fact, I'm sure a lot of the stuff I have installed must be 32-bit, and it runs fine.

So I just don't get what the issue is. OK, I'm a dummy here. Someone please enlighten me!

---

### Post by Jarz Corp on 2005-06-27
No that isn't what I am saying, if U are running 64bit ubuntu then your oo1,3 is also 64 bit and so is 2.0 on the same system, if it would work which I never got it to do.

What I meant was, I have installed openoffice 1,3 on several 32bit based systems where I never saw the print error, so it must be something that has only been introduced in the 64bit version, it wasn't there from the beginning.

Yes the 64 bit kernel can support 32 bit stuff, and no problem with the cpu. But im theory windows xp 64bit has been released, but it isn't 64bit only a few components of it is, all the important stuff is still 32bit.

If U want to run 32bit apps in ubuntu 64bit, or any oder linux, U have to either do the chroot trick, which I couldn't be bothered with or fiddle with linux32 which should make some stuff work, but I haven't gotten that to work yet either.

So in short, if U can find and install an app from synaptic, it is 64bit, if U want to use something else U will have to apply one of the two methods. That is simplifying it quite a bit.

---

### Post by lptr on 2005-06-28
The installation here includes two HP Laserjet network printers.

Found same problems that OO does not print. I had 1.1.3 successfully running under Sarge. After switching over to kubuntu it does not work, anymore.

Tried OO2 beta, too. As in 1.1.3 I _can_ see all CUPS printers and can select them but non of it sends a print job to my printers. 

As it appeares OpenOffice does not even start when GLX is enabled. My conclusion is, that it could be a hardware based problem, too. When GLX is enabled I get a strange memory problem error (when starting from terminal window).

My system: PCIexpress Geforce 6600GT Intel P4 3,2 HT CPU, 2 GB RAM (if anyone is interested I will having to dig for the chipset)

rob*

p.s. I forgot: running 5.04 32 bit

[Update]
OO2b in Kubuntu32 is printing now. Was a problem with CUPS (understanding problem, well...)

The OO starting problem stays :-(

---

### Post by John Jason Jordan on 2005-06-28
I'm still unable to install OpenOffice.org 2.0 beta. There are three packages for it listed in Synaptic, but when I try to install them each one gives me an error message about a missing file. I tried downloading the tarball from Sun, but when I untared it, I found that all the files are RPMs. So I used alien to convert them to .debs, but that gave me about two pages of error messages and no .debs were created.

Someone on a local Linux user group e-list gave me another repository to add to Synaptic, but I must not be getting the syntax right. I have tried adding it numerous times in the Add > Custom box, but all I get is error messages. Either that or Synaptic totally ignores the repository and does not add it.

It's actually two that I was given --

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted deb
[http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Then it occurred to me to troubleshoot it by just browing to those locations to see what was really there. It turns out there are some packages there, but I think I need to direct Synaptic to the /binary-amd64/ folder. (I have amd64 computer with 64-bit Ubuntu 5.04.) I think those lines above take you to a 32-bit folder. Thus, Synaptic on Ubuntu-64 wisely refuses to have anything to do with it.

I wrote down the address per the URL window in Firefox, but no matter how I type it in, Synaptic still either gives me error messages or doesn't install the source at all.

I've spent hours trying to get OpenOffice.org 2.0 beta installed. It would be a big help if someone could go there and tell me exactly what line(s) to type into the Add > Custom box in Synaptic to be able to access that repository.

---

