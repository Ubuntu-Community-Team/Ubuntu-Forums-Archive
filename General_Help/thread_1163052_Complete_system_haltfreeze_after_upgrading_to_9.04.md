---
title: "Complete system halt/freeze after upgrading to 9.04"
date: 2009-05-18
forum: General Help
---

### Post by AlexsAntidote on 2009-05-18
OK so I upgraded from 8.04 to 8.10 then to 9.04 and ever since then I have been having problems with the system halting. 

It seems to happen more often when I am using flash through Firefox (like playing flash games or watching stuff on youtube). It doesn't always freeze when I'm using flash, but it does always seem to happen when Firefox is running (probably because I always have it running).

I seem to recall there was an issue with the flash player I had installed for 8.04 where it was replaced by a different player during the update. I am not so sure that is the problem.

When I say the system halts / freezes I mean simply that. I can't do anything, no mouse movement, no keyboard interaction, all programs stop. The only thing I can seem to do is turn the power off and reboot.

I have done all the updates and even tried doing the diagnostic boot and repairing any broken packages (which it didn't find).

Any ideas why this is happening or where I should look to troubleshoot?

Thanks in advance!

---

### Post by ghostborg on 2009-05-18
I too have noticed problems with slow down , freezing, system halt.
I agree it seems to be related to Firefox flash.
My version is Jaunty 9.04 AMD64.
Gigabyte MA78GM-S2H
AMD Phenom II x4 920
6 gig Gskill DDR2 800
Nvidia 8400 GS
Nvidia Driver 180.44
Kernel 2.6.28-11-generic
Firefox version 3.0.10

I also noticed a problem with Clamav. It was not working, hanging and then causing system instability. I un-installed it and reinstalled  KlamAV the KDE GUI version, seems to work- so far.

I ran memtest86+ from the Grub menu and everything passed.

---

### Post by sandy8925 on 2009-05-18
What are you using to play Flash media in Firefox ?  Look at the sticky on multimedia problems in the Sound and Multimedia forum. I'm pretty sure you can get your problem solved.

---

### Post by ghostborg on 2009-05-18
Well-tried it, hope it works. I thought I did this before but maybe I missed something or something got removed.
Thanks for the Tip.

---

### Post by AlexsAntidote on 2009-05-18
> **ghostborg said:**
> I too have noticed problems with slow down , freezing, system halt.
I agree it seems to be related to Firefox flash.
My version is Jaunty 9.04 AMD64.
Gigabyte MA78GM-S2H
AMD Phenom II x4 920
6 gig Gskill DDR2 800
Nvidia 8400 GS
Nvidia Driver 180.44
Kernel 2.6.28-11-generic
Firefox version 3.0.10

I also noticed a problem with Clamav. It was not working, hanging and then causing system instability. I un-installed it and reinstalled  KlamAV the KDE GUI version, seems to work- so far.

I ran memtest86+ from the Grub menu and everything passed.

That is interesting. I too have ClamAV installed (though haven't used it since updating).

I guess I forgot my specs. 
Acer Aspire 9300-5005
Jaunty 9.04 (32bit edition)
AMD Turion 64 X2 mobile technology TL-50 / 1.6 GHz
NVIDIA GeForce Go 7300
3 GB Gskill DDR2 533
Kernel 2.6.28-11-generic
Firefox version 3.0.10

---

### Post by AlexsAntidote on 2009-05-18
> **sandy8925 said:**
> What are you using to play Flash media in Firefox ?  Look at the sticky on multimedia problems in the Sound and Multimedia forum. I'm pretty sure you can get your problem solved.

I am at work right now so I can't double check, but I believe it is flashplayer-nonfree. I will check out the sticky you mentioned and report back afterwords. Thanks for the suggestion, I hope it works!

I'm sure the problem will be solved (I never worried) it's just a matter of figuring it out ;)

---

### Post by AlexsAntidote on 2009-05-19
OK so I did a whole lot more searching and it looks like there are a lot of people experiencing halts/freezes with various reasons.

(see the following thread for examples: [http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055))

It looks like the problem seems to be with the kernel and several people have had success fixing this problem by simply upgrading the kernel. I saw 2.6.30 mentioned, but as far as I can tell that's still only at RC4. I may try upgrading to 2.6.29 but I don't have time to compile a new kernel tonight...

Has anyone else experienced this freeze/halt problem and fixed it with a kernel upgrade? or am I way off?

---

