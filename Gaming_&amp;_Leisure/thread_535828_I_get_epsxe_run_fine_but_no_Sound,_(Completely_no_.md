---
title: "I get epsxe run fine but no Sound, (Completely no sound)"
date: 2007-08-27
forum: Gaming &amp; Leisure
---

### Post by Ioky on 2007-08-27
After many hours research and working, finally get epsxe running, very happy, however, no matter what I do, i still can't get the sound working. gaming with no sound at all. really bad....haha. None of the plugin seem to work this problem out. P.E.Op.S. OSS Audio Driver 1.9 and Pete's Null Audio Driver 1.1 don't give me any sound, and I can't get Etemal1.41_linux run at all. once I put it into the plugin fold. I can't confg my epsxe it will close right away. I am hoping some one here have face this problem before, and get it work out. I believe my sound is using OSS but I am not sure is this the problem.

Thanks.........

---

### Post by acoustibop on 2007-08-27
Try removing the Eternal plugin from your plugins folder, Ioky.  I discovered that, as long as it's in there, ePSXe will always crash when you attempt to select Sound configuration.

However, I'd advise you not to bother with ePSXe.  It's getting a bit long in the tooth now (4 years since the last update) and is even worse to get working satisfactorily in Linux than it is in Windows.

I'd recommend [pSX Emulator]("http://psxemulator.gazaxian.com/").  It's the only Playstation emulator that's still in active development with regular updates (one or two others get very rare updates), and is the only one that seems to have Linux version that works well with almost no hassle - all you need is to tar the package to a folder, install libgtkglext1 (in the repositories), add a Playstation BIOS and a game or two, and you're good to go.

It's pluginless and emulates entirely in software, which has a great deal to do with why it's so easy to use and works so well.  Unlike most other Playstation emulators, it's aimed at accuracy of emulation rather than enhancement, and it's suprising what a revelation this can be.

There's also an excellent frontend for it, produced by one of the [pSX forum]("http://psxemulator.proboards54.com/")'s admins, [Ultima's pSX Frontend]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263").

---

### Post by Ioky on 2007-08-27
Thanks for the recommendation of pSX. In fact I do use this emu for some 2D game. it simply simpler to work with. not a problem, However, for some 3D games. the 3D are kind of not so good. which mean epsxe are the one who work better with 3D. not super great, but a lot of better, because it's plugin. So I still work to get epsxe working on my system. anyway, get epsxe work is not a problem, but the sound seem like the only thing that is bothering me. haha. and again thanks for your recommendation.

---

### Post by acoustibop on 2007-08-27
Did my suggestion for getting the sound working fix it, Loky?

---

### Post by Ioky on 2007-08-27
Well I never USE Etemal1.41. In fact, I can't . As you say it will shut down epsxe as long as it is in the plugin fold. so i never put it there. 

and it is ioky haha but that is ok But thanks for the attention thought

---

### Post by acoustibop on 2007-08-27
> **Ioky said:**
> ... and I can't get Etemal1.41_linux run at all. once I put it into the plugin fold... 

I got the impression from your first post that you might have the Eternal plugin in your plugins folder, Ioky.

Sorry about the name - funny, because I usually just copy & paste names anyway. ;)

---

### Post by Ioky on 2007-09-06
haha that is ok, Nice to meet you thought

---

### Post by fotakou on 2008-07-11
I am having a small problem here
Even though i installed pSX its folder is a root folder.I managed to move the SCPH1001.BIN into the bios folder but i cant seem to run the pSX.Does anyone has an idea? :roll:

---

### Post by acoustibop on 2008-07-11
What do you mean by a root folder, fotakou?  If you've actually installed pSX to / you may well have permissions problems.  Try decompressing the file to your home folder.

Then cd into the pSX folder and do ./pSX

However, if you're running a 32bit OS, you'll probably need to install libgtkglext1 - you can do this with```
sudo apt-get install libgtkglext1
```or just install it in Synaptic.  If you're running a 64bit OS, it gets a bit more complicated.

---

### Post by fotakou on 2008-07-13
Thanks a lot!It worked!But i have one other small question.The pSX is installed in the /home/fotis/pSX folder.I want to open some iso files from my hard disk,that are not into the cdimages folder and pSX simply does not show them!I can find the folders in which the iso files are located but i cannot browse them :confused: Also the pSX folder seems to be "locked" and i cannot paste files into it.How can i fix that?

---

