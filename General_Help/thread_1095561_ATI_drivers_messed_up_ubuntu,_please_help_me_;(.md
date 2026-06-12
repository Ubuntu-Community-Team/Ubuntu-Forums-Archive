---
title: "ATI drivers messed up ubuntu, please help me ;("
date: 2009-03-13
forum: General Help
---

### Post by crazydiam0nd on 2009-03-13
Hi, I am new to Ubuntu 8.10 and after  installing it and getting used to it I was very happy.

I had some problems with my video drivers so I read somewhere on here to try the offial drivers from ATI.

I downloaded the .run file and followed instructions on converting to a deb and instaiiling with various commands in dos ;) sorry, terminal.

I rebooted and the ubuntu loading screen appears and after that I get 2 ubuntu logo's in pink and green with messed up graphics :(
There is nothing I can do to fix this as I cannot get to the desktop.

I tried the safe mode and tried fixing X, dpkg etc etc
also tried commands like

sudo dpkg-reconfiurexserver-xorg

none of the commands has fixed the problem and I am at a loose end now and really do not want to go back to windows.

is there a safe mode for ubuntu or a way to set the graphics to default?

really appreciate your time in helping me as I am a newb to linux.

pulling me hair out lol

---

### Post by rbmorse on 2009-03-14
There is a "safe mode."   Next time you boot the computer, select the "recovery mode" option from the boot menu. 

That should start the machine but not the GUI.  At the prompt, log in with your normal credentials and then:

sudo aticonfig --initial -f<enter>

where <enter> means press the enter key.  This will make the ATI installer write a new configuration file.  When that's done, assuming there were no errors, type

sudo restart now

at the prompt to reboot the machine.

---

### Post by crazydiam0nd on 2009-03-14
Hi, thanks for fast responce.

Unfortuanatly this has not worked.
I dont get the 2 ubuntu logo's anymore but  just get 3 screeens which do checks, the last one being Battery test    OK.

Then after this its just a messed up screen with some lines and pixels at the top of the screen.

Any thoughts or do I have to reinstall?

Thanks

---

