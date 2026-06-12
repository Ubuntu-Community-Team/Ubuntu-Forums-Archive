---
title: "Upgrading from Latitude D620 to E6410"
date: 2010-09-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MSPdwalt on 2010-09-22
Hey guys,

I have a problem and it's a great problem to have.  I currently have a Latitude D620 running Lucid Lynx and I love it, I have everything customized exactly the way I want it.

My D620 is physically beat to hell.  I am a field tech and I take it everywhere, it's been dropped, scratched, dented, and really just flat out abused.  My employer has a new E6410 on the way to finally relieve this poor thing from duty.

I want to know what is the best way to migrate to this new machine.

Is it as easy as taking an image of my hard drive and restoring it to the new machine?

Do I install Ubuntu fresh on the new laptop, somehow dump my list of installed packages/repositories, and just copy my profile from the old machine?

Is it worth it to go to 64-bit? 

Are there any caveats with the E6410 that I should be aware of?

To my knowledge it's got the i7 processor, nvidia graphics, intel wifi card, and bluetooth I'll post more detailed specs when I actually receive the laptop.

Once I decide to start migrating I've got 48-hours (the weekend) to get functional on the new machine.

Any info, feedback, suggestions, or comments would be greatly appreciated.

DW

---

### Post by ptptaylor on 2010-09-23
If you think you need the extra processing power in applications which use the 64bit then yes it is probably worth it. 
In general, you won't notice it in the desktop environment. 

I don't think you'll be able to just copy it over since you'll have different hardware etc. 
As for making a list of packages and repositories I'm not sure what to do for that. 48 hours will be plenty of time to get it back to the way you want it ;)

---

### Post by djwohls on 2010-09-24
FYI: The Alps multitouch touchpad has issues.  There was a patch in one of the kernels that was since removed as it caused other issues.  Right now the touchpad scrolling does not work, also cannot turn of tap-to-click.

See here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625)

---

### Post by MSPdwalt on 2010-10-29
Thanks DJ, the ALPS issue is one of the problems I had during the transition and it's still outstanding.  The worst however was the video card issue.  Apparently the Nvidia card in these things doesn't like the open-source drivers that the installer disk uses and that you're forced to use on first boot/login.

I had to set nomodset at the splash-screen when I installed,  then after install I had to boot to the cd again, chroot into my new install and modify Grub to use nomodset and nosplash.  Then I could login and enable the proprietary Nvidia drivers. 


 What I ended up doing as to make sure I got all my stuff re-installed was dumping my list of installed packages using the command shown here [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366) Then I was able to remember most of my customizations.  It took me about 2 hours to become "functional" again, after solving the video card issue.

I should've ran 64-bit from the beginning.

---

