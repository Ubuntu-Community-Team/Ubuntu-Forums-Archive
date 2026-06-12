---
title: "Error 18 on Bootup"
date: 2006-08-11
forum: Desktop Environments
---

### Post by Jou Moer on 2006-08-11
I'm at wits end.  I have a new (unformatted) HDD that I want to install Edubuntu on.  It booted up fine with the LiveCD and I went through the motions of installing.  At the formatting section, I sellected to wipe/format the whole drive for a clean install.  Once the setup was complete, the machine rebooted and I removed the CD.  The BIOS loaded up detecting my dvd drives and all other PCI device listings. Then it shows the following:

*Verifying DMI Pool Data......*
*GRUB Loading stage1.5.*

*GRUB loading, please wait...*
*Error 18*
_ (flashing cursor)

I have reinstalled everything again but the same happens.  Boot order in the BIOS is CD, A, C and the HDD jumpers are set to Cable Detect

Any ideas or suggestions?  Can (Ed)ubuntu install on a clean, unformatted HDD or,  should I install Windows first of all and using Microsoft's formatting tools and then wipe it afterwards by reinstalling (Ed)ubuntu?  What does Error 18 mean?  :(

---

### Post by ferebee on 2006-08-11
> **Jou Moer said:**
> I'm at wits end.  I have a new (unformatted) HDD that I want to install Edubuntu on.  It booted up fine with the LiveCD and I went through the motions of installing.  At the formatting section, I sellected to wipe/format the whole drive for a clean install.  Once the setup was complete, the machine rebooted and I removed the CD.  The BIOS loaded up detecting my dvd drives and all other PCI device listings. Then it shows the following:

*Verifying DMI Pool Data......*
*GRUB Loading stage1.5.*

*GRUB loading, please wait...*
*Error 18*
_ (flashing cursor)

I have reinstalled everything again but the same happens.  Boot order in the BIOS is CD, A, C and the HDD jumpers are set to Cable Detect

Any ideas or suggestions?  Can (Ed)ubuntu install on a clean, unformatted HDD or,  should I install Windows first of all and using Microsoft's formatting tools and then wipe it afterwards by reinstalling (Ed)ubuntu?  What does Error 18 mean?  :(

[This]("http://www.gentoo.org/doc/en/grub-error-guide.xml") Gentoo page has a nice listing of Grub errors and what they mean.

Since your drive is new, you might want to check with your motherboard manufacturer to see if the current BIOS can support a hdd of that size. There might be updates available for your BIOs that allow it to recognize a larger drive. According to the Gentoo page this might be the problem.

*Edited to add:*Is your Bios seeing the new HDD? Is it set up to recognize it? You wouldn't want to flash the bios if you didn't really need to.

Hermanzone's [Grub Page]("http://users.bigpond.net.au/hermanzone/p15.htm") is a good reference for Grub with Ubuntu too.

---

### Post by Jou Moer on 2006-08-11
Thanks for that ferebee.  Google did not find me a BIOS and the manufacturer wants someting like USD30 for an upgrade, so screw them.

Seeing as I don't know how to move my boot partition I'll reinstall again, but this time only format a small partition of about 10 gig.  Once I've installed and the machine can boot up I'll resize and create a second partition and use it as a storage place. ...or so he says confidently... ;)

---

### Post by pneaveill on 2006-08-11
Not sure which MOBO you have, but **[COLOR=DarkGreen]*** if ***[/COLOR]** you really need to flash the beast, then there are some legitimate places that have some of them. I concur that unless you absolutely have to, then don't. [COLOR=DarkGreen]**Google is your friend**[/COLOR].  Dumb quexstion time: was there any other info besides the grub 18 error or anything that might help us analyze the problem further?

Meanwhile, agree with the previous few posts about verifying that your MOBO/BIOS will even see the HDD. If the MOBO/ BIOS refuses to see a larger HDD, then may wish to make friends with someone with a smaller drive or something. 

Another option (this may require a bit of patience on your part) is to play around with the various setup stuff on ubuntu. There have been several times I have done this and found one to work on this machine, but not that one. 

*** Disclaimer *** PLEASE -- before you start playing around with it, please read up on this.

---

### Post by Jou Moer on 2006-08-11
> **pneaveill said:**
> Not sure which MOBO you have, but **[COLOR=DarkGreen]*** if ***[/COLOR]** you really need to flash the beast, then there are some legitimate places that have some of them. I concur that unless you absolutely have to, then don't. [COLOR=DarkGreen]**Google is your friend**[/COLOR].  Dumb quexstion time: was there any other info besides the grub 18 error or anything that might help us analyze the problem further?

Meanwhile, agree with the previous few posts about verifying that your MOBO/BIOS will even see the HDD. If the MOBO/ BIOS refuses to see a larger HDD, then may wish to make friends with someone with a smaller drive or something. 

Another option (this may require a bit of patience on your part) is to play around with the various setup stuff on ubuntu. There have been several times I have done this and found one to work on this machine, but not that one. 

*** Disclaimer *** PLEASE -- before you start playing around with it, please read up on this.


LOL! Your comment about Google reminded me of [this]("http://www.justfuckinggoogleit.com/") link! In any case, not to worry about the disclaimer as it does not matter if I break the box or not, after all, its only software and it can be reinstalled again. 

Anyway, what I done was as follows:  I removed my second cdrw as I already had a dvdrw and in its place I returned my original HDD (13GB)  I was then able to reformat the whole drive and install Edubuntu successfully.  As I'm typing this, I'm busy collecting 168 updates.

This is a very old box; it was my first pc and I build it myself - that was about September-ish 1999.  It has an AMD K6-2 500mHz Proc, 448 meg ram and a 13 gig HDD and a cdrw.  I "upgraded" it by wacking in a 200 gig HDD, a dvdrw, usb 2.0 card and a new graphics card.  Unfortunately I could only have either an additional HDD or an extra dvd drive as I was short with one power connector from the psu.  When the cash flows again I want to upgrade the mobo and the proc as well.

This old pc of mine was not used for the past 4 years; in fact I took it out of the loft in the beginning of the week after I ventured into the world of linux with my one laptop. (i've got 2 laptops (WinXP and Ubuntu), this pc(Edubuntu) and my work-issued laptop).  I set up a little home network and I build this Edubuntu box for my son to play on and do his school stuff.  I have to admit that it is much safer to let young kids loose on a linux box compared to a windows box as they cannot do any accidental system changes/damage without the admin password.

I originally wanted just the one HDD and the two cd/dvd drives, but after my problems of this evening I removed the old cdrw and put in the original HDD. Just as I was puting on the box covers, I realised that I forgot to correct the jumpers on the 2 hard drives, so I had to correct it again.  My plan is now to reformat the large drive, do the Samba thing and use it as a file store. - more searching for me in the HowTo forums!!

To get back to the original question.  I cannot find the make of the mobo, but the model number is GA-5AX.  Unfortunately there was no other error messages apart from what I posted on the original post.  The BIOS did detect both hard drives.  Once the updates have completed I'll reboot the machine and have a look what the HDD detect has to say for itself in the bios about the capacities.

Thanks for all the advice, links and comments sofar.

---

### Post by pneaveill on 2006-08-12
Master Google say GA-5AX is a gigabyte MOBO [http://www.fujitsu-siemens.co.uk/rl/servicesupport/techsupport/boards/Motherboards/GigaByte/GA5AX/GA-5AX.html](http://www.fujitsu-siemens.co.uk/rl/servicesupport/techsupport/boards/Motherboards/GigaByte/GA5AX/GA-5AX.html)

---

