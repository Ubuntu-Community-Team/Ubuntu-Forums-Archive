---
title: "Can Ubuntu 7.04 Run Windows Software?"
date: 2007-09-12
forum: Education &amp; Science
---

### Post by srobot on 2007-09-12
Hi all,
Sorry if I'm posting in the wrong place, and if this has been asked before...

I have some software for Windows 95, 98, XP, and Vista that I want to run. Can I run it on Linux?

Thanks,
--Scotty

---

### Post by tgm4883 on 2007-09-12
[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by reckless2k2 on 2007-09-12
wine does work but not very well. hahaha. i don't think you will get the vista stuff to work. wine is kinda buggy. have you looked for linux alternatives that are freely available?

like ms office > open office

yadda

---

### Post by edoviak on 2007-09-12
> **srobot said:**
> Hi all,
Sorry if I'm posting in the wrong place, and if this has been asked before...

I have some software for Windows 95, 98, XP, and Vista that I want to run. Can I run it on Linux?

Thanks,
--Scotty
Yes, this question is asked far too often. In the future, please do a site search before posting. That having been said ... Let me give you a slightly more detailed answer. After all, I too was once new to GNU/Linux.

Wine emulates the Windows API (Application Program Interface, or something like that). It works really well with old versions of MS Office (ie. Office 97 and Office 2000). Some bright spark even used Wine to authenticate his version of Ubuntu on Microsoft's Genuine Advantage server. Other programs are hit or miss. I've seen successful reports of people using Wine to run Mathematica, EViews and (Heaven help them!) SPSS. On the other hand, Adobe Acrobat is a notorious failure.

Like Reckless, I would suggest that you look at [GNU/Linux software equivalents]("http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software") for two reasons. One, it expands your horizons. It teaches you that there is more than one way to do something. Two, it exposes you to the Free Software movement. 

If you stick around, you'll see that GNU Free Software is better precisely because it's "free as in freedom, not as in free beer."

Welcome aboard,
- Eric

---

### Post by UbuWu on 2007-09-13
Another option is to run vmware or virtualbox or a similar program which allows you to run a complete windows operating system under linux in which you can run your programs.

---

### Post by rolnics on 2007-09-13
> **reckless2k2 said:**
>  have you looked for linux alternatives that are freely available?

like ms office > open office

yadda

As reckless said, have a look for alternatives, do a google search. Here's a site to get you going :-[linux alternatives]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html")

---

### Post by karellen on 2007-09-14
> **srobot said:**
> Hi all,
Sorry if I'm posting in the wrong place, and if this has been asked before...

I have some software for Windows 95, 98, XP, and Vista that I want to run. Can I run it on Linux?

Thanks,
--Scotty

the short answer is: No  (not properly at least)

---

### Post by carusoswi on 2007-09-15
> **srobot said:**
> Hi all,
Sorry if I'm posting in the wrong place, and if this has been asked before...

I have some software for Windows 95, 98, XP, and Vista that I want to run. Can I run it on Linux?

Thanks,
--Scotty

I have Crossover (paid version of Wine).  I run Office 2000.  Word works ok, excel, too.  The program I really need, Acess, is sketchy.  

I find some of the responses here overly simplistic, and a couple downright snippy.  FWIW, I find it irritating for someone to tell you to please do this or that in the future, as if the board belongs to them.

Anyhow, running a virtual copy of XP from within Ubuntu can work, except, you will find that accessing certain parts of your computer is not possible.  I use a program called Wavelab from Steinberg.  I can install it on a virtual machine, and it will run within that machine, but the program will not communicate with my CDRW or DVD drives - Wavelab is one of only a handful of professional audio editors - and being unable to write to a CD/DVD drive renders it useless.  So, for playing with certain programs from within Ubuntu, a virtual machine may be ok.  For working with some programs, forget that solution.

Crossover/Wine supports Photoshop version 7, not beyond.  Unfortunately, I find that all the features of PS7 do not function under Crossover.  Moreover, there is no fully functional driver available for my Canon i960 printer.

Some here will criticize me because I should have purchased a printer compatible with Ubuntu.  Unfortunately, I owned my i series printers long before discovering Ubuntu.  Long story short, even if I avoid using the PS7 features that will cause that program to lock up under Ubuntu/crossover, I have no way to print my masterpieces except to boot back into XP.  Because of that, it just makes more sense for me to boot into XP and manipulate my photos in the vastly improved version 9 of Photoshop and have all its features and a fully functional means by which to print my photos when I have finished editing them.

I find no equivalent to PS in Linux.  I'm still looking.  Gimp has bit depth limitations or I would use it.  There is a nifty RAW viewer/editor available in Linux (UfoRaw), but, again, I have no way of printing pics from Ubuntu, so why bother editing pics from this platform?

Skype won't work for me in Ubuntu (no sound input).  If you search, you will see others with this issue.

I'm not knocking Ubuntu.  If you read and agree with the principles of open source (and I do), you understand that ranting about unsolved problems is not proper etiquette.  But, I feel it equally rude for folks to berate posters such as you because they have tired of answering questions (make that defending Ubuntu) over and over.  You could search to find your answer, you could search and not find it, also, so, I urge you to keep on asking questions in addition to searching.  Sometimes the fresh answer can prove to be more helpful.

Folks who advise you to familiarize yourself with Open Office should also explain that the database application in that suite has a bug that prevents you from completing the design of a form.  In Access, I create forms that contain subforms, complex relationships, etc.  Can't do that in the buggy version of Open Office that comes with the official version of Ubuntu 7.04.  So, for me, Open Office is useless.  Sure, you can write letters and such, but, if you are looking for something in Ubuntu/Linux that takes the place of MS Office that is working 100%, I don't believe you'll find it.  Perhaps OO is working properly within other Linux distros, but not yet in Ubuntu.

But reports have been posted for a long time concerning this OO problem, but those bug fixes have not been completed (to my knowledge).

If you really depend upon the features of MS Office, I'd do a dual boot so that you have XP around to do your work.  Use Ubuntu for worry free internet browsing and for the pleasure you will derive from learning about an alternative OS.  

Ubuntu is refreshingly different than XP.  I prefer the simple clean look, it seems to run more efficiently on my 3.0 gHz machine.  You can browse the 'net free of virus concerns (and anti-virus programs).

And, no doubt, one day, better software for things like multimedia and an MS Office like database that works will be developed.

For me, that day hasn't arrived, but, seeing as how I so enjoy working in Ubuntu, I know that I need to continue to be patient until someone or group has the time to address the issues.

Good luck.

Caruso

---

### Post by jfdill_2 on 2007-09-15
Lately, I've been running Windows XP under VirtualBox on a Dell Optiplex GX260, 2.4 GHz P4 (non-HT) with 1 GB memory, this has mainly been for testing.  I have to say, I have been surprized how fast it is even with only 192 MB memory allocated to the VM, it runs much faster than XP ran natively on the same box, but of course this is for basic 2D graphics, business type apps, no 3D or gaming.

For computer games and graphics-oriented apps, take a look at [TransGaming]("http://www.transgaming.com/"), it's able to run quite a few, but by no means all.

---

### Post by UbuWu on 2007-09-15
> **carusoswi said:**
> 
I find no equivalent to PS in Linux.  I'm still looking.  Gimp has bit depth limitations or I would use it.  There is a nifty RAW viewer/editor available in Linux (UfoRaw), but, again, I have no way of printing pics from Ubuntu, so why bother editing pics from this platform?


You might want to tray krita, it does 8 bit/channel RGB, CMYK, grayscale and wet watercolors, 16 bit/channel RGB, CMYK, grayscale and L*a*b*, “half” RGB, and 32 bit float RGB (HDR) and LMS. It doesn't have all features that PS has yet but it is quite good. Also for raw files, rawstudio is also very nice.

---

### Post by jfdill_2 on 2007-09-15
Xara Xtreme seems impressive to me, but I have to admit I'm not really a graphics person.

[http://www.xaraxtreme.org/](http://www.xaraxtreme.org/)

---

### Post by carusoswi on 2007-09-22
> **UbuWu said:**
> You might want to tray krita, it does 8 bit/channel RGB, CMYK, grayscale and wet watercolors, 16 bit/channel RGB, CMYK, grayscale and L*a*b*, “half” RGB, and 32 bit float RGB (HDR) and LMS. It doesn't have all features that PS has yet but it is quite good. Also for raw files, rawstudio is also very nice.

Thanks, UbuWu.  I'll give those aps a try.

Caruso

---

### Post by srobot on 2007-09-28
Okay, so I'm feeling very dumb right now, but is the Dell Latitude D520 (with Core 2 Duo), 32 bit or 64 bit?

---

### Post by tech9 on 2007-09-28
> **srobot said:**
> Hi all,
Sorry if I'm posting in the wrong place, and if this has been asked before...

I have some software for Windows 95, 98, XP, and Vista that I want to run. Can I run it on Linux?

Thanks,
--Scotty

yes... virtual box

---

### Post by srobot on 2007-09-28
Also, can I use McAfee on both sides of a split HDD without paying for two copys (XP and Vista, Ubuntu would not need any)?

Second, would a dual or tri boot slow down the computer at all?

2 GB of Ram.

--Scotty

---

### Post by Coyote21 on 2007-10-01
> **srobot said:**
> Hi all,
Sorry if I'm posting in the wrong place, and if this has been asked before...

I have some software for Windows 95, 98, XP, and Vista that I want to run. Can I run it on Linux?

Thanks,
--Scotty

I've always have used vmware player together with [http://www.easyvmx.com/](http://www.easyvmx.com/) tools, to run windows, and i've currently have an virtual machine with windows XP professional x64 installed, and it works seamless (the sound isn't good, and it is still an bit slow (since the virtual machine, maximum memory, will be taken from your main memory, but 1,5 gb, will suffice, if you consider to use an windows with 512MB or even more), and also an fedora installation, with an custom designed yum, that compiles packages by source using srpm's rather than using pre-compiled packages, like some ubuntu deb's, but don't talk to much about it :-$ (were in an ubuntu forum), and at last an virtual machine that has freeBSD on it. But, when the processors, and if their will support multiple os's running at the same time, them I would not need vmware anymore (maybe using an Ctrl+F# scheme), until them...

---

### Post by geoffBEAM on 2007-10-03
> **carusoswi said:**
> I have Crossover (paid version of Wine).  
Anyhow, running a virtual copy of XP from within Ubuntu can work, except, you will find that accessing certain parts of your computer is not possible.  I use a program called Wavelab from Steinberg.  I can install it on a virtual machine, and it will run within that machine, but the program will not communicate with my CDRW or DVD drives - Wavelab is one of only a handful of professional audio editors - and being unable to write to a CD/DVD drive renders it useless. 

Caruso are you using Virtualbox?  I ask because Virtualbox sees my DVD/CD drives if I ask it to! It also sees my MIDI hardware through USB and Serial Ports!! 

 I am a musician and I see NO reason Wavelab is "rendered useless" by a virtual machine! If you make "waves" with Wavelab you should be able to export them to linux OS and burn them to disk there.

I have yet to run into any functionality issues with VirtualBox.

---

### Post by carusoswi on 2007-11-25
> **geoffBEAM said:**
> Caruso are you using Virtualbox?  I ask because Virtualbox sees my DVD/CD drives if I ask it to! It also sees my MIDI hardware through USB and Serial Ports!! 

 I am a musician and I see NO reason Wavelab is "rendered useless" by a virtual machine! If you make "waves" with Wavelab you should be able to export them to linux OS and burn them to disk there.

I have yet to run into any functionality issues with VirtualBox.

Thanks for the reply, Goeff.  It seem every route I take to overcome my problems takes me to a dead end.  I've tried VMware and Virtual Box, have successfully installed XP virtually on both.  But could never get Wavelab to recognize my burner from either.

What sound editing aps do you use?

I suppose I could work on my waves and export them for burning with some other ap.  I could probably export montages and just dual boot back into XP for the actual burning, too.

I am very comfortable with WL's disc burning application (the Montage), and don't really want to give up that functionality.

I think I'll play with a montage and see if I can export that for burning.

That would be half the battle.  The other is recording . . . doesn't work with WL/Ubuntu.

In fact, I have been unable to get any ap to record in Ubuntu (Ardor, Audacity, WL under wine and CrossOver).  So, until I figure it out, I'll have to keep using XP - it isn't the end of the world - I just wonder how so many folks are meeting success in this area, and, it seems, no matter how much time I put into troubleshooting, I cannot seem to figure out the answer.

FWIW, my machine is a Shuttle XPC running XP/Ubuntu 7.04.  I have two sound cards, one onboard, one PCI.

I've tried running with the onboard disabled.  The system reacts as expected and sees the PCI card.  I can play back, but cannot record.

In Audacity, if I set my onboard audio to record, I can get static, but only a steady machine type noise, no response to external line/mic inputs.

The PCI card (Audigy 2 LS) doesn't respond to signal inputs at all.

Further suggestions welcome.

Caruso

---

