---
title: "Wine .9 and Warcraft III"
date: 2006-03-31
forum: Gaming &amp; Leisure
---

### Post by LinuxLove on 2006-03-31
Here's what happened:
[LIST=5]
[*]Put WC3 cd in.
[*]Mounted with: "mount /dev/cdrom"
[*]Then I installed with "wine install.exe"
[*]Installation Completed with no errors.
[*]Click play game, and a blank window appears with "Launching Warcraft 3" as title.
[/LIST]

I'm guessing this is not going to work no matter what I do, and that I'll absolutely have to get Cedega, which I really rather not.

Thanks for your help.

---

### Post by holomorph on 2006-04-02
you don't,  I was just playing today under wine.  I forget exactly how I installed it though, but it wasn't hard.  Needed a CD crack (easy to find at megagames) because the CD detection is screwed up.  Where did you get wine from?  It looks like the one I am using is 20050725, which is the current version in the Universe repository.

---

### Post by LordRaiden on 2006-04-09
I have this problem to but I found a cheap way of getting around it. It never used to happen before but in any case I don't know how to post it as a bug, since there are no real error messages.

Basically, once you click on the War3/Frozen Throne icon, hit CTRL+ESC immediately. Scroll down to wine-preloader. You should see 3 of them (in any case more than 1). Kill the first 2 wine-preloaders (the last one is the game) as fast as you can (I use Kubuntu so i right-click>>kill>>ok). Wait a few moments, and you should be in.

---

### Post by rorschach on 2006-04-09
huh - I'm gonna have to give that a try LordRaiden, as I get the blank screen titled launching warcraft 3 every time I try to launch with the -opengl option.
However, if I leave that tag off, it launches... but is slooooooooooooow.

---

### Post by rorschach on 2006-04-10
Aaughhh!
ok, many hours of fiddling later:

I still cannot force Warcraft 3 to launch with opengl. I am using the command
wine War3.exe -opengl
and it hangs with a black screen. If, however, I attempt to launch without the -opengl tag, I get a very choppy, slow, version of Warcraft to launch.

I got frustrated enough earlier to download the cedega trial. The results were no better - though it is nice to have it validate that my system has the *capability* to run Warcraft. It passed all of its little tests with no problems. However, when I attempt to launch Warcraft, it hangs after the splash screen comes up and I have an orc's mug plastered across my screen. The main, black screen comes up behind it and goes no further. I lose all control of my system through the gui. Luckily, I rememberedthat you can grab a command line login via ctrl-alt-F1 and killed the wine processes then switched back to my GUI (ctrl-alt-f7).

There has *got* to be a way to get Warcraft 3 up on my system - it's working for other people. From what I can tell - my configuration is the same software-wise, so, perhaps its hardware?

I'm on an hp nc6220 laptop.
Intel Pentium M 1.6 GHz CPU
500MB ram
Mesa DRI Intel 915GM Video chip
Intel ICH6  with AD19818 at 0xd0981000, irq 2 Sound Card, running ALSA 1.0.9a
wine version is 0.9.11
winecfg shows CDROM being recognized
Windows version is set to 2000
Enable desktop double buffering, and Allow the window manager to control the windows are selected
ALSA driver is the default sound driver, and it is set to full harware acceleration with driver emulation.

Suggestions?

---

### Post by sorcererx84 on 2006-04-10
I play Warcraft 3 with TFT on a similiar laptop with Wine 0.9.7 and everything works fine. Do you have dri i915 drivers installed?

---

### Post by rorschach on 2006-04-10
I haven't specifically installed any video odrivers - just what is default from the install.
How can I check that?

---

### Post by macmasterxiv on 2006-04-10
Just so you know, I have frozen throne working flawlessly under 0.9.9 in dapper repo; **wine 0.9.11 breaks many opengl games.** if you are even going to attempt to use frozen throne, use 0.9.10 or earlier,

---

### Post by rorschach on 2006-04-10
Hmmm - ok, will try taking out 0.9.11 and installing the breeazy build (wine_0.0.20050725).

any pointers for testing or installing that i915 driver while I'm at it?

---

### Post by sorcererx84 on 2006-04-11
I am using i915. I installed 20060107 snapshots from dri.freedesktop.org. Works perfectly. Just make sure you have kernel headers and build-essentials installed.

---

### Post by Toxicity999 on 2006-04-11
run wine "path/to/war3.exe" -window -opengl now once in change thesetting to 32 depth if you want to run without the window option... and you should be good. The launcher has issues but the actual exucutable lanches okay. If you have the frozen throne and want to play classic add the -classic flag otherwise it'll start with TFT. Good luck PM me if you need more help I probably wont find this thread again... IT was all good for me this way... ( you may also want to disable all sounds, In my case I disabled all but unit responses... otherwise to me It's just not very fun.)

---

### Post by Toxicity999 on 2006-04-11
OH OH OH
and as far as CD detection goes... run in win2000 compat mode...or 98 well whatever happens to work. And under your Drive settigns in winecfg make sure the CD drive is pointing to /dev/cdrom0 and that under the advanced settings its ticked as CD-ROM dRive and not automatic or local. Detection should go fine.... and if not then just use a noCD crack

---

### Post by rorschach on 2006-04-15
Hey, sorcererx84 -
How did you go through installing the snapshot?
Everytime I try, glxinfo stops seeing my driver.

---

### Post by moon_dog on 2006-04-26
how do you get an earlier version of wine?  all i see in the repos is the latest version 0.9.12

---

### Post by holomorph on 2006-04-26
which repos?
breezy is 0.0.20050725-0ubuntu1.1: i386 
dapper is 0.9.9-0ubuntu1: i386

---

### Post by Rizado on 2006-04-27
The newest CVS works perfect, but you might have to start it with war3.exe and not Warcraft III.exe
And don't forget about "-opengl"

---

### Post by Technoviking on 2006-04-30
Warcraft III keeps crashing on me with Wine 0.9.12

dbasinge@monolith:~$ wine .wine/drive_c/Program\ Files/Warcraft\ III/war3.exe
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbbf64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbbf67c,0x00000000), stub!
fixme:wave:DSD_CreateSecondaryBuffer (0x7fd72e68,0x159d3144,180e0,0,0x7fdab434,0x7fdab524,0x7fdab410): stub
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:win:EnumDisplayDevicesW ((null),0,0x7fbbbc00,0x00000000), stub!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  471
  Current serial number in output stream:  471


Any ideas?

---

### Post by Rizado on 2006-05-02
[QUOTE=Mike Basinger]Warcraft III keeps crashing on me with Wine 0.9.12

dbasinge@monolith:~$ wine .wine/drive_c/Program\ Files/Warcraft\ III/war3.exe
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbbf64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbbf67c,0x00000000), stub!
fixme:wave:DSD_CreateSecondaryBuffer (0x7fd72e68,0x159d3144,180e0,0,0x7fdab434,0x7fdab524,0x7fdab410): stub
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:win:EnumDisplayDevicesW ((null),0,0x7fbbbc00,0x00000000), stub!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  471
  Current serial number in output stream:  471


Any ideas?[/QUOTE]I got that problem too now, Guess it's something with dapper because I didn't have any problem with breezy. Also wine can't change the resolution anymore :( That might just be the problem...

---

### Post by kookookachooo on 2006-07-09
Hi, I'm having the same problem with the 'retry correct cd-rom' error. Toxicity999 when you are talking about the drivers in winecfg could you be more specific please? :rolleyes: Thank you, and does anyone have a working no-cd crack that they could post? Many thanks.:razz:


Edit: Got WC3:FT to work but it runs SUPERR sloww. I've tried the -opengl thing and it doesn't seem to change it. Is there some other way to quicken the speed or check if I did it correctly or not? One more thing, the graphics seem really weak, and I know they should be better; is there a way to check if I installed my drivers correctly? I have an ATI 9200SE. thanks in advanced

---

