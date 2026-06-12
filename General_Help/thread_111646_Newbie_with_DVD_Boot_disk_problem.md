---
title: "Newbie with DVD Boot disk problem"
date: 2006-01-02
forum: General Help
---

### Post by Sopranosmainman on 2006-01-02
Hey guys, i downloaded, and burned the dvd-iso for the newest kubuntu build. Im brand new to linux. I dont want dual boots, or 2 OS's... just one and i just want it to be soley linux... im going at this hardcore :)...I used kill disk to wipe my HD on my laptop. I burned the dvd image on my other computer... and yes i did it properly, becuase in windows, it opens up and says loading browser, then lets me look at a whole bunch of packages sucha s mozilla firefox etc. Anyways, when i put the disk in my laptop when it boots up, from CD first, like i read to have the settings set... it just reads the dvd, thens ays operating system not found. Is it because u cant boot from a dvd... i dunno, i really wanna try linux out... Help PLEASE! Thanks in advance. 

Oh i have a IBM Thinkpad R40 laptop.

---

### Post by Zelut on 2006-01-02
Hmm.. I have had a few times when burning the .iso didn't actually make the .iso bootable.  Might want to double-check your burn settings & see that you've done that right.  It sounds like it burned the DVD right but didn't set it to boot is all..

---

### Post by byen on 2006-01-02
could be a corrupted iso file.... or a corrupted disc write. the first thing i would suggest is checking the md5sum of the downloaded iso. md5sum is a utility where you will be able to see if the whole download has taken place without errors or not. you could use the program "winMD5sum" from the link here
[http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)

now once that is done.... burn the iso file at a slower speed using the "burn iso" or "burn image" option in your cd burning software. for easy simple use...you could try deepburner cd writing software...it is easy and simple as it gets (free too)[http://www.download.com/DeepBurner/3000-2646_4-10402901.html?tag=lst-0-1](http://www.download.com/DeepBurner/3000-2646_4-10402901.html?tag=lst-0-1)
try these out and let us know.
Now remember.be patient...a lil patience in linux goes a longway. and we are here if yu need help.goodluck.

by the way...since this is your first post....welcome to UBUNTU!
  	
~byen

---

### Post by ATAQ on 2006-01-02
Maybe the DVD drive in the pc you burned the disc was good and the one in which you wish to install may not be ggod enough to read the disc. That happened to me before.

---

### Post by Sopranosmainman on 2006-01-03
Thansk for the help and the welcome guys.... at least i know dvd's are bootable... im gonna try the checksum program and the burning program... i was using alcahol 120%.... but i will try it your way.. i just hate wasting dvd+r's though :) Will let u know how it works out

---

### Post by Sopranosmainman on 2006-01-03
Well... i used that checksum program... didnt give me any errors... gave me the following number :76a11485c3e791a4e6e43c0d8a1f562e:

Then i using your mentioned program, burned it and still the same problem.... now i decided to try it on a different computer... so i put it in my home desktop computer and guess what.... it booted up... so now what do i do? I only want to try this on my laptop, and it doesnt seem to support the booting of dvds? Any suggestions... or maybe a workaround....thanks guys.

---

### Post by byen on 2006-01-03
well.. the simple thing to do would be to burn it onto a regular cd. but tell me..why would your laptop not boot from a DVD but from a cd... now...are you sure you enabled your laptop to boot from CD/DVD rom drive as the primary option? if not....
Go to your bios settings (usually by bressing f2,f6 or esc..depending on the bios and pc make) and change the primary boot option to CD/DVD rom.

i am not sure if this is what you were looking for...but let us know how things go. Goodluck.

PS- and about wasting dvd's. trust me...id rather spend a ton of cds and have a complete customized, stable system than worry about my pc breaking down. trust me..its worth it.

---

### Post by Sopranosmainman on 2006-01-03
**Yeah, i definately made it look for the cd first, and i even press f12, to go to the boot option screen and make it check it first.... i see that it checks the cd... by the blinking light in the cd rom drive... but nothing happens..... can it only read dvd's from windows... or a operating system for that matter? And if that is the case and it cant read dvd's to boot from... then i guess i have to download the cd bootable images???** Let me know guys....

Oh and once i get this to finally work.... whenever i have to update do i need to another bootable image... or does it work from within the OS, and i dont have to worry about anymore bootable images. Thanks again guys. I cant wait to get this thing up and running! Have to wait till after work though :( before i get another crack at it

---

### Post by byen on 2006-01-03
well.. to be really frank with you i am  stumped. All i can say for now is..try it out with a cd. And even then if it does not work...it would have to be a hardware compatibility issue and we can start from there. So let us know.

> whenever i have to update do i need to another bootable image... or does it work from within the OS, and i dont have to worry about anymore .bootable images
Nope. It works just like other OS's like windows..where there is an update manager which takes care of all the updates. This will be the only time you will have to deal with this. To add to this...even in the future when they release new versions. you can simply upgrade your Ubuntu OS without having to format or reinstall from start.
I know this is taking time for you but please be patient. Goodluck.

---

### Post by Sopranosmainman on 2006-01-03
Alright.....im downloading the cd version now..... im sure it will work then... hopefully next time i post it will be on my linux branded laptop ;) And then i will have many mro questions to ask im sure... wheter it be software or hardware related. Thanks again guys... see ya in a few

Oh and just curious... besides the LIVE CD version of the OS what else is on the dvd iso image thats not on the cd iso. thanks

---

### Post by Sopranosmainman on 2006-01-03
Well the cd iso worked... unfortunatly i run into problems :(

After pretty much setting up everything pretty easilly i get to this error when installing the base system

States the following when i get the select the kernel to install:

linux-386
linux-image-386
linux-image-2.6.12-9-386

I have done all three and get the same error:

An error was returned while trying to isntall th kernel into the traget system:

Kernel package: one of the above

---

### Post by iansane on 2007-09-23
this is probably a stupid question but something I would probably do. Is the drive in the laptop a dvd-rom or just a cd-rom. I could see myself trying for a week before realising it if that was the case.

---

### Post by iansane on 2007-09-23
I gotta start looking at the post dates. Don't think anyone is reading my reply since 2006

---

