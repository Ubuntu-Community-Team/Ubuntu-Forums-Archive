---
title: "Problem with HD after install"
date: 2005-01-23
forum: Desktop Environments
---

### Post by mmr_85 on 2005-01-23
First of all let me introduce to the forums, im new to ubuntu, i tried some linux distributions before but i never used them due to hardware uncompatibility.

I have a laptop with a 3CRSHPW196 wireless card that is really problematic to install, and i was told that ubuntu could detect it with not much trouble, so I decided to give it a try. I downloaded the iso, burnt it at 48x and had some issues, reburned at 4x in a cdrw and it worked now....

The problem was present when during the install my hard disk started to make some noises like clogging, i cant really describe it, it was constant noise and with a constant frecuency. Tnk Tnk Tnk Tnk and it kept doing it.... and with hope it kinda got stuck there and then continue copying/installing the files...

If i understood what installation did, was to detect the HD and use some "generic linux ide controller" or something like that...  I ignore if it is related somehow to the ubuntu installation... Since my computer was running windows xp pro FINE with NO hardware problems.... Im afraid this HD error is related to the installation...

One thing i had to do is to run the installation with "noapic nolapic" and in expert mode to avoid some problems, since it would freeze at first in "ACPI revision bla blabla" and later would exit installation with a return 1 message...

Ok, this kinda scares me... since the HD seems to be damaged....Ubuntu failed once to install since it got stuck with the clogging at 70% or something near there. Later installed it, but during the module loading in the bootup in the first run, it got stucked twice... once got it to bootup, but i restarted to connect it to the network, and got some messages later about unable to read something and some "panic " errors in kernel... this kinda scared me more, and tried to install windows xp back, and now my HD makes this noise... and it stucks in the copying files so im unable to install it now..... since it warns me about somep roblems copying files, and ubuntu bootup warned me about some reading errors

Ok, so the facts...

My laptop is old, 3 years old, but was running QUITE FINE regarding the hardware and HD, no problems related in the last 3 years.

This started once i tried install ubuntu

Worked fine with xp before i tried ubuntu


So im scared, might it be realated to some error/misconfiguration in the ubuntu installtion. Now supposing that it is the HD in the best of the cases and not other part, the part here is kinda expensive... 100usd~ for a HD disk for my laptop, i dont have the money right now to fix it, i have other priorities, and i dont want my laptop to get permantly damaged and being not functional.

Can anyone tell me if it is related to Ubuntu installation? and what might i do to know if HD is the one causing the trouble.... it is formatted back to NTFS and still makes this noise at some point.. i cant tell it makes it at a specific time, like 10 minutes after being on, it makes it randomly and sometimes it wont affect as it "fixes" back,but makes the same thing after another few minutes...

Any help would be appreciated.
Thanks

---

### Post by J. S. Jackson on 2005-01-23
That doesn't sound good.  It's a very good idea to make sure you have all important data backed up.  (I don't think you need to be told this hehe).

Of course, installing an operating system requires writing quite a lot of data to the drive, so it may be only coincidence that installing Ubuntu pushed the disk to it's last leg, or wrote data to bad sectors that XP was not using before, therefore exposing a defect.  I've had two disks fail in my years of computing, and both times it started with the disk making unusual "grinding" sounds.

Since you are back to XP now, have you tried running the FULL chkdsk on the drive, to check for bad sectors?

Open "My Computer"
Right click on the disk/partition in question and select "Properties"
Go to the "Tools" tab
In the section called "Error-checking" select the "Check Now" button.
Make a check mark in BOTH boxes and hit "Start".
Windows will inform you that it needs full access to all files, and ask if you want to perform the check on next boot.
Say Yes, of course, and reboot.
This will take quite a long time.

You might also check the website for your drive manufacturer.  Sometimes they have a tool to confirm that a disk is faulty when requesting an RMA.  That may also help you to decide if the disk is, in fact, dying.

---

### Post by gheorghe_pop on 2005-01-23
That sound it's not good at all.The first time that i heard that sound was long time ago when i did a format on a old 2 GB disc.From that time that's the only thing that i could get from that drive.
So here is what you should do:
If you can still acces your data bakupit right now.
Try to repair your HDD.I know that there ar some good HDD utilities that can repair pshicaly bad sectors.Try a google for it.
If that doesen't  work change your HDD.

---

### Post by mmr_85 on 2005-01-23
Thanks for the replies... Well im unable to install XP now either, since the HD will start making its noise and wont allow me to install it... Im gonna look for a tool that i might run in dos or boot into to check for damaged sectors....

All the data was lost, i had nothing important on it, since it is a secondary computer that i only use in school in some rare occasions, but i dont want it to get damaged permanently.

Thanks for the answer, ill try finding such tool and let you know if i get to something.

---

### Post by mmr_85 on 2005-01-23
I think im in trouble... I cant even run such tests cause they will halt when the HD makes its strange noises...

Also i noted that if i accessed the bios setup, it sometimes detects and sometimes it doesnt the hard disk, i think this is not lookin good... What are the chances that a bad IDE driver damaged the disk? :cry:

---

### Post by mmr_85 on 2005-01-24
Might there be something else i could do? I kinda doubt that the IDE controller might damaged my disk, but it was in that moment, after formatting the HD to ext3, and when it was copying the files it started to make the noise. I thought that the noise was from a cd read failure or something, but this seems to go worst...

Bios wont sometimes recognize the disc, and i cant run the diagnostic tools since they crash when they loose contact with the HD.

---

