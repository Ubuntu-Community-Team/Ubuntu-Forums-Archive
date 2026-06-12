---
title: "Maxtor SATA Drive Not Recognised"
date: 2006-06-29
forum: Desktop Environments
---

### Post by dravidham on 2006-06-29
Hi,

I'm relatively new to this so please bear with me.

Ok it's like this - PC was working perfectly last night was running all the latest updates and Norton Internet Security 2006 - and then I messed it up big time.

If I must own up to it I stupidly downloaded a version of Norton System Works 2006 with the intention of upgrading my existing NIS 2006.

I had a quick look at the 'read me first' notepad file and the/activation method looked pretty simple so I proceeded with the .exe install. 

About 20 seconds in to the initial intstall I glanced at the bottom of the above 'read me first' and it stated 'important - if NIS 2006 is already installed on your machine, please remove it first prior to installing systemworks'. I immediately terminated the System Works install.

I rebooted the machine and thats exactly when the problem started. I get a black screen with a cursor for around about 30 seconds. Then I get a message reading 'setup inspecting hardware config'

After that, the screen reads 'Roboot & select Proper device or insert media in selected device & press any key'

The PC is a Mesh, therfore I only have a basic XP Home disk which bizarly does not have a repair function. The original recovery disk that they initially supplied conveniently destroyed all my data when I had to use it last year so that is not an option.

I rebooted again and went into Bios Utility and I have noticed that the primary IDE master drive and also secondry IDE master both come up with 'not selected' (I guess they are not recognised.

My PC is a AMD Athlon 64 running at 3200mhz through an Asus K8v Deluxe socket 754 motherboard and I just have one unpartitioned HD which is a Maxtor SATA 160GB.

My initial thoughts were that the SATA driver has been deleated s I went on the Asus site here at work to try to get a driver on to floppy disk but I am not sure where the SATA drivers are on their support downloads section. The closest they seem to have is a new Bios driver. Would that contain the SATA driver?

Any of you PC gurus have any ideas how I can sort this nigfhtmare out - I can not afford to lose all the data on the HD, which rules out formating the drive and I'd like to avoid buying a second HD if I can, although if it comes to it then I will.  

Edit:- spoke with a pc shop who suggested that it might just be a BIOS menu setting that has been knocked out. But it was hard to understand him given that I was not in front of the machine him self. Do any of you have any bios setting pointers as to what he meant?

Hope the above makes sense and if some of you could post back then I would be really grateful.

Thanks,

David.

---

### Post by twigboy on 2006-06-29
Have you tried doing a repair on the windows partition?  Heres a good link
[http://www.michaelstevenstech.com/XPrepairinstall.htm#RI](http://www.michaelstevenstech.com/XPrepairinstall.htm#RI)
This basically just recopies your system files to your drive. 
I think even with your sata driver being deleted I think you would still be able to use the drive because xp can also use the ide driver.
For the bios I would just load the default setting or even better if you have a load optimal defaults.
Also what kinda of motherboard chipset are you running? nforce?

---

### Post by dravidham on 2006-06-29
Have you tried doing a repair on the windows partition?  Heres a good link
[http://www.michaelstevenstech.com/XPrepairinstall.htm#RI](http://www.michaelstevenstech.com/XPrepairinstall.htm#RI)
This basically just recopies your system files to your drive. 
I think even with your sata driver being deleted I think you would still be able to use the drive because xp can also use the ide driver.
For the bios I would just load the default setting or even better if you have a load optimal defaults.
Also what kinda of motherboard chipset are you running? nforce?[/QUOTE]

Hi,

Thanks for the very quick reply.:D 

I only have the one partition on the HD, and just one HD and my reg is not backed up - yes, I have been stupid, I know!

I bought the machine from Mesh Computers therefore the XP Home disk was OEM. I has issues 18 months ago when I tried to do a repair with the Master Recovery OEM version of XP that they shipped out with my machine when it was new, so they eventually replaced it with a 'burnt' copy of a stand-alone version of XP home. Problem with the replacement is that it does not have a repair function - it's a complete install or nothing.

My mothereboard is an Asus K8V Deluxe and the chip set is Via K8T800.

A guy in a shop suggested that maybe some settings in the bios menu might have gone astray, but he was a little vague. Before I tried the Systemworks programme installation everything was working perfectly.

Thanks,

David.

---

### Post by dravidham on 2006-06-29
Oh sorry - forgot to ask - how do I get my BIOS settings back to default. I am very worried that I will lose all the data on this drive If I am not careful.

---

### Post by easyease on 2006-06-29
is your maxtor hd one of those that has an ide interface as well as a sata?
ive got a maxtor hd myself, i use it through the ide connection.

---

### Post by easyease on 2006-06-29
"I only have the one partition on the HD, and just one HD" have you tried installing ubuntu on the maxtor alongside xp and making it dual boot? the ubuntu  install cd should be able to read exactly what your hardware set up is and you can take things from there.....forget all that norton antivirus nonsense, use a linux partition and distro for internet. all windows is good for is games compatibility......

---

