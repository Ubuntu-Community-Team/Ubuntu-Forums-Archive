---
title: "Uninstall ubuntu?"
date: 2009-06-09
forum: General Help
---

### Post by n0c2urnal on 2009-06-09
i need help uninstalling ubuntu.
trying to get windows back on my laptop.
tried cd drive, usb, disk drive and nothing worked.
i dont have an ubuntu cd.
can anyone help me with this?

---

### Post by lisati on 2009-06-09
Do you have a (legal) Windows CD or a recovery partition?

Any particular problem with Ubuntu that you'd like to ask about first?

---

### Post by n0c2urnal on 2009-06-09
thanks for the quick reply but i have burned windows xp cds.
gave ubuntu a try and didnt really like it. just tryin to go back to xp

---

### Post by n0c2urnal on 2009-06-09
thanks for the quick reply but i have burned windows xp cds.
gave ubuntu a try and didnt really like it. just tryin to go back to xp

---

### Post by H2SO_four on 2009-06-09
then put windows cd in the cd drive and follow instructions to install.

---

### Post by toppervergara on 2009-06-09
do you have your files backed-up? I suggest you do. and ive heard you can always do a dual boot system in that way to can have the best of both worlds. Ubuntu just takes some time to get used w/o having to pay for the operating system.):P

---

### Post by n0c2urnal on 2009-06-09
> **H2SO_four said:**
> then put windows cd in the cd drive and follow instructions to install.

if it were that simple i wouldnt be asking for help.
i think its cause the cds are burned and arent the real thing.

---

### Post by lisati on 2009-06-09
> **n0c2urnal said:**
> if it were that simple i wouldnt be asking for help.
i think its cause the cds are burned and arent the real thing.

It can depend on how you burned them (and sometimes where the data came from). My current laptop and desktop both came with software that let me burn bootable CDs/DVDs that let me restore my machines to an out-of-the-box state. I've seen Windows disk images downloaded from ["don't-ask-too-many-questions"]("http://I-told-you-not-to-ask!") that were riddled with malware....

---

### Post by n0c2urnal on 2009-06-09
hmm... is there a way to delete ubuntu if i had the ubuntu cd?

---

### Post by lisati on 2009-06-09
> **n0c2urnal said:**
> hmm... is there a way to delete ubuntu if i had the ubuntu cd?

Yes.

If you installed Ubuntu "within" Windows using Wubi, all you need to to is to start Windows, go to the control panel, and uninstall it using the Add/Remove programs option.

Otherwise: from the Live CD, open up the partiton manager/editor on the System->Administration menu, and delete the Ubuntu partition. You can then resize the Windows partition (if there is one) to suit your needs. You'll then need a working Windows installation disk and put in "fixmbr" from command prompt. Note: this will not restore windows if it isn't there!

---

### Post by sendblink23 on 2009-06-09
Let me help you out and its truly really EASY

but yes you need the LIVE CD to do it

First boot into Ubuntu with the Live CD

Choose: Appplications > Accesories > Terminal

Enter this command: 
sudo lilo -M /dev/sda mbr

This will RECOVER windows BOOT MBR

Now Removing & Deleting Ubuntu
in the Top Menu choose: System > Administration > Partition Editor

Once in it.. look at the Partitions, look for Swap <--  Right Click on it.. and choose Swap Off (or something like that)  

Then Delete BOTH of linux partitions (Swap & ext/3 wte its called) & Choose on the   Menu APPLY

Afterwards Select your Windows Partition & Expand it Entirely and Select Apply

That is it REBOOT you are done.. back with Windows XP
*note windows will execute a Check Disk, that is normal.. let it finish and you restart as you used to in Windows

---

### Post by n0c2urnal on 2009-06-09
i dont have windows installed, its just ubuntu

---

### Post by lisati on 2009-06-09
Sounds like you might have to get a "new" Windows cd/dvd if the ones you have aren't working for some reason. Booting from a Windows installation or recovery disk usually does the trick. If Windows came preinstalled on your computer, you might have to contact your computer manufacturer.

---

### Post by sendblink23 on 2009-06-09
Well IF you dont have WINDOWS installed SIMPLE

Insert the Windows CD and that is it it will REMOVE Ubuntu (Delete the Partitions, when Prompted inside the Windows Installation) and Reinstall Fresh ONLY Windows in your Hard Drive

You don't need the Ubuntu Live CD for that

Now if you don't have a working Windows CD, sorry for that info its considered illegal here

---

### Post by n0c2urnal on 2009-06-09
alright so when i have my windows disc in while my computer is setting up, everything is fine, it goes to the setup/ repair screen.
then when i press enter to install windows, it says that there are no hard disk drives found. or something like that.
also when i try to execute the setup.exe off of the cd while ubuntu is running, this message appears [COLOR="Red"]**"You will need to rerun setup in order to install Windows. Choosing Dynamic Update during setup will possibly remedy this error."**[/COLOR]
im sorry im noob with all this stuff but what the hell.......

---

### Post by n0c2urnal on 2009-06-09
anyone have this problem or something similar to it?
by the way ill let everyone know a little bit about my laptop.
its a hp dv5000, had a harddrive failure so switched it. when my laptop was fixed and given back to me, it had ubuntu on it.. gave ubuntu a try after a couple of months but just dont like it. i tried everything except for an external cd drive because i lost my power supply.
any tips or solutions will help TREMENDOUSLY

---

### Post by sendblink23 on 2009-06-09
if it says you have no hard drive... then you probably have a faulty *hard Drive


BUT... you may do as I mentioned before.. about using Gparted from the Live CD of Ubuntu

In there you should be able to see the hard drive... all you need to do it... Format it to *Unallocated or Primary NTFS (then in the top menu choose Apply)   which ever of both Windows shall be able to recognize the Hard Drive (so that you can try installing it again Restart & Boot from Windows CD) .. that is only ofcourse that Ubuntu Live CD *recognizes your HD.. if not.. then.. its a faulty HD

sorry I can't hep with anything else.. I just find it extremely weird Windows won't recognize the hard drive

---

### Post by lisati on 2009-06-09
It might not be a faulty hard drive: I've heard of Windows setup disks getting confused when there's a good hard disk that have Ubuntu installed in the places that Windows likes to be.

---

### Post by n0c2urnal on 2009-06-09
ill give it a try as soon as i get a live cd from a friend or something. thanks for you help will update you when i get a chance to try it out.

---

### Post by evermooingcow on 2009-06-10
Are you trying to install XP SP1 or older (can't remember exactly what SP you need) on a SATA drive by any chance? Are you trying to install to a raid?

If either is ture you likely need to load drivers during setup. You will need to go find drivers on the manufacturer's site, put them on a floppy (must be a floppy), have the floppy inserted during install and hit F6 when the prompt to load drivers flashes briefly at the bottom of the screen during the beginning of setup.

If you dont have a floppy you need to have the drivers compiled into the setup disc. The best way is to slipstream SP3 onto it. Or go get Vista/W7

---

### Post by Entropy_Sam on 2009-06-10
> **n0c2urnal said:**
> when i try to execute the setup.exe off of the cd while ubuntu is running
 
That's your problem.
 
Don't boot into Ubuntu. It can't remove itself while it's running.
 
Simply put the Windows CD in the drive and boot the machine. Read the startup messages carefully, as iirc you need to press Enter at startup to boot from the windows CD. If there's no change, then have a look at the boot sequence in BIOS and set it up to try to boot from CD before the hard drive.
 
If your computer's set up correctly, when you have the Windows CD in the drive, it should boot into the setup program. If you want to remove Ubuntu, then simply remove/reformat the Ubuntu partition(s) from the CD before installing Windows (BACK UP ANY DATA YOU WANT TO KEEP FIRST!).
 
The CD WON'T run/function correctly if your attempt to run it on your computer from Ubuntu. It's not designed to work like that. 
 
Hope that clarifies things a little.

---

### Post by Mirge on 2009-06-10
Amazes me that ppl are still replying when he blatantly posted that he pirated the software heh.

---

### Post by lisati on 2009-06-10
> **Mirge said:**
> Amazes me that ppl are still replying when he blatantly posted that he pirated the software heh.

In some situations it seems it's possible to burn Windows setup CDs/DVDs legally... my desktop and current laptop came with software preinstalled that does the job, and my replies were based on that assumption. I'm also aware of where to get pirated CDs (I'm not saying where but am sure that some forum users can guess) and the associated risk of legal hassles and malware, hence the comment in an earlier post to contact the computer manufacturer.

---

### Post by Entropy_Sam on 2009-06-10
Either way, if someone's trying to run setup.exe from a Windows install disk using Wine, to overwrite the Ubuntu installation they are currently running Wine on, then a little explanation/education is in order...

---

### Post by lisati on 2009-06-10
> **Entropy_Sam said:**
> Either way, if someone's trying to run setup.exe from a Windows install disk using Wine, to overwrite the Ubuntu installation they are currently running Wine on, then a little explanation/education is in order...

Running setup from within Wine? I hadn't spotted that one. I suppose I'd better re-read the thread.

---

### Post by Mirge on 2009-06-10
> **n0c2urnal said:**
> if it were that simple i wouldnt be asking for help.
i think its cause the cds are burned and _**arent the real thing**_.

See above.

---

### Post by Mirge on 2009-06-10
To the OP: I would highly recommend you talk to whoever installed ubuntu on your computer, asking him/her politely to put Windows back on your computer. Not to be rude, but you didn't install Ubuntu... so maybe your best bet is to ask that same person to install Windows instead.

---

### Post by lisati on 2009-06-10
> **Mirge said:**
> See above.

Thanks for pointing that out. 

n0c2urnal: Pirated copies are risky (possible legal hassles, possible malware, probably don't have all the drivers needed for your particular machine) - you might be able to get suitable setup disks legally from your computer's manufacturer.

I think I'll adjourn for now.
Goodnight everyone, safe computing to all1

---

### Post by Fluffbugs on 2009-06-10
You can try fdisk.Exe(just need it).
from microsoft to fix ur mbr first. Bcouse i once got the same thing. Use all console(failed).
I got it, from "partition magic"- rescue disk. I burn to 2 disket. If u dont have floppy disk. Burn as bootable disk to cd wid the file inside. And execute it. I've posted it in my personal blog, but not in english. Use translation..Maybe it is right.

---

### Post by n0c2urnal on 2009-06-11
> **Mirge said:**
> To the OP: I would highly recommend you talk to whoever installed ubuntu on your computer, asking him/her politely to put Windows back on your computer. Not to be rude, but you didn't install Ubuntu... so maybe your best bet is to ask that same person to install Windows instead.

heheheh i did talk to my friend about that he said, "i dont support window users." what a jackass huh? lol
but thanks everyone for your input, ill everyones advice once i have time.
much appreciated!

---

