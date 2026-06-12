---
title: "RAM help"
date: 2010-10-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by milton0523 on 2010-10-13
Hi. I use a Dell Inspiron e1505 laptop with Ubuntu 10.04. It has 2 gigs of ram, and Ubuntu recognizes only 488.2 megs. It runs ok, but I know it could run faster, especially with videos. Can anyone help? F.Y.I. it came with 2 gigs, I didn't add more on after I got it.

---

### Post by mikewhatever on 2010-10-13
Why do you think Ubuntu doesn't recognize all of your RAM? Ca you show some evidence. Can you also post the output of **free -m** from a terminal window.

---

### Post by hlpguru on 2010-10-13
The current 32 bit editions of Ubuntu can only take advantage of 3GB of its physical memory.

---

### Post by milton0523 on 2010-10-14
free -m gives


             total       used       free     shared    buffers     cached
Mem:           488        472         15          0         25        184
-/+ buffers/cache:        261        226
Swap:         1426          0       1426

As for WHY, I don't know, am a noob, only had Ubuntu for a few months.

---

### Post by pricetech on 2010-10-14
Check and make sure your BIOS is seeing all your RAM.

---

### Post by milton0523 on 2010-10-14
> **pricetech said:**
> Check and make sure your BIOS is seeing all your RAM.

Hmm, it's not. any idea how to fix THAT?

---

### Post by pricetech on 2010-10-15
Incompatible or failing RAM both come to mind as possibilities.

Reset the BIOS to defaults, then see if it sees it all.

You might also check Dell's website to make sure you're running the latest BIOS.  Use your service tag to be sure you get the right BIOS.

---

### Post by milton0523 on 2010-10-16
I don't have the latest BIOS, how could I install the latest in Ubuntu? Also, I don't have a battery, could that affect the BIOS update?

---

### Post by gibbylinks on 2010-10-17
Sometimes the RAM isn't seated properly. If your confident enough, open up the case take the RAM out and put it back in, maybe swap the banks over if you have more than one bank of RAM in there.

If your happy doing this it might be worth booting with one bank at a time to make sure there both working OK.

Good luck

---

### Post by mörgæs on 2010-10-17
Agree with the post above, but beware of static electricity.

---

### Post by milton0523 on 2010-10-19
I don't think i'll open the case. I wouldn't even know what the ram looks like. Anyway, the hinges for the screen are busted, i'd have to keep the screen open. I also still want to know how to update the BIOS.

---

### Post by mörgæs on 2010-10-20
It is a minor operation to open to the memory. It is not about opening the entire box; there is usually a small cover below (the size of 1-2 credit cards) which gives access to the RAM.

---

### Post by cascade9 on 2010-10-20
> **milton0523 said:**
> I don't think i'll open the case. I wouldn't even know what the ram looks like. Anyway, the hinges for the screen are busted, i'd have to keep the screen open. I also still want to know how to update the BIOS.

I'd really, realy doubt that updating the BIOS will fix your problem. I would guess that you've got a serious issue....you should have 2GB (2 x 1GB) but you are only getting 488MB (which is probably 512MB minus video shared RAM). Which means that one stick is just not working at all...but more worrying, one stick is at half the size it should be. 

Anyway, as for how to update the BIOS, you'll have to install it fromwithin windows or do the old way- flash the BIOS from a flopppy drive. 

> _**Run the BIOS update utility from Windows environment**_


[LIST=1]
[*]Double click the Icon on your desktop labeled MM061A17.exe.
The **Dell BIOS Flash** window appears
[*] Click the **Continue** button.
The message **Pressing OK will close all applications, shut down Windows, Flash the BIOS, then reboot.** appears.
[*]Click the **OK** button.
The system will restart and the BIOS Flash will be completed.
[/LIST]


_**Run the BIOS update utility from  DOS environment (Non-Windows users)**_


**NOTE:** You will need to provide a bootable DOS diskette. This executable file does not create the  DOS system files. 

[LIST=1]
[*]Copy the file MM061A17.exe to a bootable floppy.
[*]Boot from the floppy to the  DOS prompt.
[*]Run the file by typing **Y:\MM061A17.exe **(where y is the drive letter where the executable is located).
[/LIST]
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R158849&SystemID=InspironI6400/E1505&servicetag=CXQCRB1&os=UBLN&osl=en&deviceid=10430&devlib=0&typecnt=0&vercnt=9&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=212350](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R158849&SystemID=InspironI6400/E1505&servicetag=CXQCRB1&os=UBLN&osl=en&deviceid=10430&devlib=0&typecnt=0&vercnt=9&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=212350)

---

