---
title: "Safer alternative to Dual boot"
date: 2006-06-13
forum: Desktop Environments
---

### Post by DirtyJay on 2006-06-13
Would enjoy anyone's opinion on this.

I have been using Ubuntu for about 3 months, and I like it a lot.  But it's not perfect, but definitely better than Windows.  The biggest problem for me installing Ubuntu was, will it do what I need it to, and can I still get back into Windows IF I have to. I need a guarantee for this, because I do so much work on the computer for my business.  So...I set everything up with a dual boot system, works for a couple of boots and.....then I lose Windows all together.  Next I PAID a technition to come out and fix my Ubuntu and Windows.  By the way, he likes Ubuntu as well and he is good friend of mine who didnt' charge me very much.   The cheapest easiest fix, reload both systems from scratch(I have two hard drives, one for Windows and one for Ubuntu).  Of course I was smart and previously copied all my important files to wife's computer(which I don't "F" around with).  So I wasn't too "Ps"'ed off.

Anyways, my alternative "dual boot":
What I have done now is turn off the computer power, disconnect the power plug from the 2nd hard drive, install Windows as independant sytem.  Next I shut down Windows, turn the power off to the computer, disconnect the power from the 1st hard drive, connect power to the 2nd drive, install Ubuntu as independant system. Then I shut down Ubuntu, turn power off, and make sure power is hooked up to both hard drives.

Here's the trick:
So when I want to switch back and forth, what I do is reset my computer and edit the bios boot up sequence.  If I want Windows, then boot from HD 1 first.  If I want Ubunt, then boot from HD 2 first.

The benefit:
Because I need Windows 1 out of a hundred times, this works out really great for me.  Only when I REALLY need to, I edit the BIOS.  Also because each system is really installed as if it were the only system on the machine, it eliminates any traditional dual boot problems.  One never affects the other.  Basically there is no dual boot, just a matter of selecting the boot sequence in the BIOS.  If I totally hate Ubuntu(I might, because I never used it before), I just reformat my Ubuntu drive and Windows is completely unaffected.  It starts like it always did.

What do y'er figure?

---

### Post by white_tiger_daniel on 2006-06-13
Brains and skill- a true linux user.  Speaking of power cables I was playing around with Worms World Party and my CD drive wasn't working.  I took it out and put my good one in.  I couldn't find Worms after that - I had left it in my bad drive!  Plugged power into bad drive and yoink - I had got my CD back.

:p 

Dan

---

### Post by keke21 on 2006-06-13
I admit I'm not too fond of GRUB's slightly complicated nature, but how'd you lose Windows altogether?

Anyway, that's an interesting way to do it. I can't say it's necessarily a good one, though. Most people, experienced or otherwise, don't often want to go into their computers like that even if it's one out of a hundred times. If I absolutely had to do that, I'd rig a couple new switches that connect one hard drive each and then boot the machine. If you're happy, though, no need to bother with the work to do it.

---

### Post by DirtyJay on 2006-06-13
I said I lost my Windows entirely, that's not true.  I lost the abiliy to load Windows.  This technition tried to fix the Master Boot Record and that did not bring back Windows.  Personally I would rather play around with a few cables and editing of the BIOS instead of tring to figure out why GRUB won't load my operating systems properly.

---

### Post by underdog on 2006-06-13
I've heard of problems with hibernation in windows causing corruption of the boot loader....is this possible?

---

### Post by imhdd on 2006-06-13
[QUOTE=keke21]I admit I'm not too fond of GRUB's slightly complicated nature, but how'd you lose Windows altogether?

Anyway, that's an interesting way to do it. I can't say it's necessarily a good one, though. Most people, experienced or otherwise, don't often want to go into their computers like that even if it's one out of a hundred times. If I absolutely had to do that, I'd rig a couple new switches that connect one hard drive each and then boot the machine. If you're happy, though, no need to bother with the work to do it.[/QUOTE]


I never thought of this before. You could take one Double Pole, Double Throw Switch (about $4.00) and use it to feed the 5 & 12 volt (yellow and red) lines to each hard drive. Hummmmm. I might try that some time when I'm more adventurous. (I haven't tried - try at your own risk!)

Later: 
On Asus A7S266-VM2 this doesn't work no matter what I do. BUT to my surprise it does work on my Biostar M7VKQ. (Tomorrow I'll buy a switch and make it permanent. Why bother? On my main computer I want to keep each operting system separate from the other. On my test computer I simply dual boot one hard drive.  

Here is my test:
Two hard drives, both set at Cable Select and connected to primary channel data cable. Drive 1 is Ubnuntu Breezy; drive 2 is Win98SE. 

Leave data cable plugged in to drives. Disconnect power to drive 2. Connect power to drive 1. It will boot to Ubuntu on drive 1.

Leave data cable plugged in to drives. Disconnect power to drive 1. Connect power to drive 2.  It will boot Win98SE on drive 2.

No input from me was needed in my M7VKQ BIOS.
This means that a remote DPDT (double pole double throw) switch can be used to choose which operating system I want to use with this motherboard, totally independent of the other and no need to change the data cable. I can simply switch hard drives electrically. This will be a lot of work for really nothing, ha. But I've always wanted to try this and now I know it'll work on some motherboards and not on others.

Don't try this if you have no experience with your hardware. It could be costly in $$$$.

---

### Post by ubnoobie on 2006-06-13
[QUOTE=imhdd]I never thought of this before. You could take one Double Pole, Double Throw Switch (about $4.00) and use it to feed the 5 & 12 volt (yellow and red) lines to each hard drive. Hummmmm. I might try that some time when I'm more adventurous. (I haven't tried - try at your own risk!)[/QUOTE]

a few years back, there was a drive bay switching device that did pretty much the same thing. i dunno they're still made or not. [http://www.technoyard.com/hardware/miscellaneous/Trios/page_1.html](http://www.technoyard.com/hardware/miscellaneous/Trios/page_1.html)

see [http://www.dvhardware.net/modules.php?name=Sections&sop=viewarticle&artid=4](http://www.dvhardware.net/modules.php?name=Sections&sop=viewarticle&artid=4) for a home-made variant. note: construct and use at own risk! ;)

---

### Post by IYY on 2006-06-13
That's exactly what I did on one of my systems. I had too much important data on that Windows partition to lose, and have a whole box of spare hard drives, so it was the best solution.

---

### Post by DirtyJay on 2006-06-13
Thanks for all of the replies.  I feel like this is a reasonable move to make after reading all of your posts.  Hmm...I like the switch idea too.  When I pull the power plug out of my hard drives, there are 4 wires in the plug.  I can understand 2, but why four?  Any ideas?

---

### Post by Ramses de Norre on 2006-06-13
Sensor readings and ground ;)

---

### Post by imhdd on 2006-06-13
I placed an edit on #6 above thinking it would automatically update this thread.
I was wrong. Please see results of my test, above. 
Thanks. I'm a noob not only to Linux but also to posting. Sorry.

---

### Post by Fatjoint on 2006-06-13
[QUOTE=DirtyJay]I said I lost my Windows entirely, that's not true.  I lost the abiliy to load Windows.  This technition tried to fix the Master Boot Record and that did not bring back Windows.  Personally I would rather play around with a few cables and editing of the BIOS instead of tring to figure out why GRUB won't load my operating systems properly.[/QUOTE]


Ahhhh... I've had a bit of experience with this.  If you were able to post a directory listing of your root drive in windows, your boot.ini file from your windows root, your grub file, and your fstab - I believe I could make your dual boot work for you.

I installed Dapper last weekend on my home PC and had a fit trying to figure out what I did wrong.  It turned out that Dapper assumed my /winnt directory held my windows, which it did at one time, but not after I upgraded it to Windows XP.  Windows XP uses /windows as it's default directory at install.  My boot.ini file referenced /winnt as the Windows installed directory and after correcting that all was well.

I've also ran into issues after installing Linux when Grub points to the wrong partition for Windows.  Anyways, I've had my fair share on this and consider myself a self-appointed practical guru after all the hair pulling I've done :P

---

