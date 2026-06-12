---
title: "installing inside Vista Home"
date: 2009-01-15
forum: General Help
---

### Post by Plinybc on 2009-01-15
I attempted several times to install inside Vista(HD0), but continued to receive error msg that setup could not locate installation CD.  Tried using CD and DVD roms.  Only options were to retry or exit.  Ended up installing on HD1, but cannot access due to no dual boot option at startup.  Ubuntu worked after installation.  

Any ideas?  I've looked at a bazillion posts, but couldn't seem to find similar situ.

This is on an HP a6330f w/AMD Athlon64 x2dual core 5600+ w/3G ram running 32bit.
HD0=500g
HD1=250G

---

### Post by svaens on 2009-01-15
So when you did install in the end (on HD1) was that also a 'inside windows' type installation?

If not, and I'm just a newbie guessing for a solution, couldn't you install then the grub boot loader?

After a quick search I found this howto. It tells you how to install the grub boot loader, how to tell it where to find installations. So in this way the problem you mentioned of "but cannot access due to no dual boot option at startup." would be fixed.  Or do I misunderstand?

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by Plinybc on 2009-01-15
> **svaens said:**
> So when you did install in the end (on HD1) was that also a 'inside windows' type installation?

If not, and I'm just a newbie guessing for a solution, couldn't you install then the grub boot loader?

After a quick search I found this howto. It tells you how to install the grub boot loader, how to tell it where to find installations. So in this way the problem you mentioned of "but cannot access due to no dual boot option at startup." would be fixed.  Or do I misunderstand?

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
It was a clean install.  I failed to mention that HD1 is partitioned.  Will this affect the argument >root (hd0, 0)?

---

### Post by Plinybc on 2009-01-16
It was a clean install.  I failed to mention that HD1 is partitioned.  Will this affect the argument >root (hd0, 0)?

---

### Post by svaens on 2009-01-16
Most likely  yes. However, I myself have never configured the grub boot loader, so cannot tell you how at the moment. And have no time right now. 
But i am 99% sure that this is the fix to your problem at the moment, since you've installed ubuntu and it is just waiting to be used. 

Have a go (google it or so) 
and if you haven't got it going by monday (i am away on the weekend) 
i'll have a look. I am curious anyway. 

In the meanwhile, perhaps someone else knows how?

for now. here is some documentation i found on google. The answer to your question is probably inside!

[http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)

---

### Post by HermanAB on 2009-01-16
Note that you need to install Windows FIRST, then install Ubuntu.  Windows doesn't play well in groups and will overwrite the boot loader.  Dual booting is however the 20th century solution and is rather clunky.

If you already have Ubuntu installed and working, then I suggest that you install Virtualbox and install Vista in a virtual machine.  This way, you can run Windows in a window, where it belongs.  A virtual Windows is far more convenient, since it can run simultaneously with Ubuntu so you don't need to reboot.  This is the 21st century solution and works much better.

Cheers,

Herman

---

### Post by Plinybc on 2009-01-16
Vista is already installed on HD0,0.  Ubuntu is on HD1,1.  I tried installing Ubuntu "inside" Windows as was an option on the installation CD.  It would not recognize either CD or DVD rom after initial info gathering, so had no choice.

I tried Svaen's grub fix, but said "cannot mount selected partition" and did not recognize "exit" as a valid command.

I know next to nothing about unix, so am flopping like a fish!  Any help is much appreciated.

---

### Post by svaens on 2009-01-21
I would also recommend what mr 'HermanAB' has suggested. 

But is this an option for you? 

Otherwise, Since you've installed Ubuntu on a whole other disk, when you start your computer normally, it won't even see your already installed 'grub boot loader', and just load windows. 
So, 
As a first step, You have to get grub installed in the boot sector of the disk where windows is. Then, when you start your computer, grub will be run, and you will have 'windows vista' as the ONLY option in the grub boot loader. That is the first step complete. 

Second step, configure the grub boot loader to look for the Ubuntu installation on the other disk. Once that is done, you'll have both OS's listed in the grub boot loader. 

That should fix it. 

Let me know if you've made any progress. Also, if not, let me know if the 'VirtualBox' solution is an option for you. It really is the better way to work. I have this on both my work and home computers, and it is really great since I have two monitors.... and so, when i need windows (for outlook or so at work) I flick VirtualBox up on my second monitor. And I always have linux there working for me. Plus, You have the added benefit of not need to re-install your windows all the time, because you can simply do a snapshot, and when it starts getting bogged down over time (like windows does) simply revert to the snapshot.... and you have a fresh windows once again!

---

### Post by Jammanuser on 2009-01-21
Hello, I believe you can get your current Ubuntu installation easily dual-booting via the Vista bootloader with EasyBCD! ;)

Here's the NeoSmart Technologies documentation on dual-booting Vista with Ubuntu, using EasyBCD: 
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

And the forums if you need any help:
[http://neosmart.net/forums/forumdisplay.php?f=7](http://neosmart.net/forums/forumdisplay.php?f=7) (EasyBCD specific forum)
[http://neosmart.net/forums/](http://neosmart.net/forums/) (NeoSmart Forums index)

GL and let me know how it goes! :)

-Jam man

:guitar:

---

