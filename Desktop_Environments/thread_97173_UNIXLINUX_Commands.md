---
title: "UNIX/LINUX Commands ?"
date: 2005-11-30
forum: Desktop Environments
---

### Post by politicaldog on 2005-11-30
If you have DOS on your computer and it is free of any other OS then can you access either UNIX or LINUX? if you type sysroot at a a:/ prompt will your computer boot into that enviroment next time?

Hope I asked this in a manner you can understand!

Rick

---

### Post by tomwell on 2005-11-30
[QUOTE=politicaldog]If you have DOS on your computer and it is free of any other OS then can you access either UNIX or LINUX? if you type sysroot at a a:/ prompt will your computer boot into that enviroment next time?

Hope I asked this in a manner you can understand!

Rick[/QUOTE]

Hey Political dog,

My thoughts on this are not 100% sure but...

If you are using DOS wich is a Disk Operating System, hence the name without any OS Operating System installed then you can not use linux or unix since these are actually OS...

Thats what  i think anyways if am wrong please teach me the way!! LOL

Peace

Tom

---

### Post by tomwell on 2005-11-30
Double post sorry...
Is there a way to remove a double post??

Once again Sorry...

Peace

Tom

---

### Post by politicaldog on 2005-11-30
Thanks

My orginal problem is that I cannot get the Unbuntu Cd to load on my PC. I have tried making a boot disk to try an load it with little success. I have heard others talking about root commands and such so my thinking was that if I could get into this root directory of UNIX then I might be able to get the thing to recognize the CD and start to load. I was hoping that there would be a command to use. :confused: 

I've tried about everything that my limited knowlege can muster. ](*,) 


Rick

---

### Post by taurus on 2005-11-30
Are you trying to install Ubuntu but your computer won't boot from the CD???  Is that the problem?

---

### Post by tomwell on 2005-11-30
[QUOTE=politicaldog]My orginal problem is that I cannot get the Unbuntu Cd to load on my PC. I have tried making a boot disk to try an load it with little success[/QUOTE]

Do you mean the Boot diskc doesnt load up on start up???

If so you neeed to press F2 or there will be a key to press and choose boot from CD....

let me know if its not that...

Peace

Tom

---

### Post by politicaldog on 2005-11-30
Yes, It will not even start to load. The PC runs throught the boot up process and then goes to NO OPERATING SYSTEM FOUND.

I have changed the BIOS to boot from CD Rom but it still does do anything different.

Rick

---

### Post by taurus on 2005-11-30
It means there is something wrong with your CD then!!!  How did you burn it?  Make sure you run checksum after you download it and burn the iso as an image file, not a data file.  Sometimes, it would be good to burn it at a slower speed like 4x...

---

### Post by teaker1s on 2005-11-30
sounds like you have burned the iso to disk (therefore it's a data disk with iso on) you need to burn the image to create an iso boot disk I hope that makes sense

---

### Post by politicaldog on 2005-11-30
OK,

It is an image file.

I can also use a program to open it up and see all the files on it. I think it was called UnDisker. I even burned another cd in that format hoping I could get into it and unload something on Diskette.

Thanks
Rick

---

### Post by tomwell on 2005-11-30
[QUOTE=politicaldog]OK,

It is an image file.

[/QUOTE]

well if you have burned the CD using 3rd party sofware and you are sure you burnt the image and not just the .ISO file, you should try using the F2 key thing or that might be boot into BIOS try F8...  that will force boot it...lol not sure what it will be on your System though ...

Peace

Tom

---

### Post by politicaldog on 2005-11-30
Ok,

I don't know if it made it a data disk. Is there a way to tell?


Rick

---

### Post by tomwell on 2005-11-30
[QUOTE=politicaldog]Ok,

I don't know if it made it a data disk. Is there a way to tell?


Rick[/QUOTE]

Yes when you burn it it warns ou that the file is an .ISO file and it asks you if you want to create  an image..... If you choose yes it creates a cd if you say no it just burns the .ISO file to the cd...

[http://en.wikipedia.org/wiki/.iso](http://en.wikipedia.org/wiki/.iso)

enjoy the read...

Get back to us...

Peace 

Tom

---

### Post by taurus on 2005-11-30
You can view the content of the CD after you burn it.  If you see one big file with an iso extension, then you have burned it wrong!!!  But if you see a bunch of directories, then you burned it as an image file...

---

### Post by politicaldog on 2005-11-30
[QUOTE=tomwell]Yes when you burn it it warns ou that the file is an .ISO file and it asks you if you want to create  an image..... If you choose yes it creates a cd if you say no it just burns the .ISO file to the cd...[/QUOTE]

Good Read. Thanks  :KS 

I don't remember if it asked that question. My options after you click the download site were save or open. I chose save. 

If you look at the CD from My Computer, would that show what is mounted on the CD? I look at it that way and it shows unbuntu-5.10-install-i386.iso

< at work will look when I get home. Will get back to you all on this.

Thanks
Rick

---

### Post by taurus on 2005-11-30
[QUOTE=politicaldog]
If you look at the CD from My Computer, would that show what is mounted on the CD? I look at it that way and it shows unbuntu-5.10-install-i386.iso
Rick[/QUOTE]
Nope!!!  You just waste another blank CD (I hope you are using CD-RW)...  What program do you use to burn it???

---

### Post by politicaldog on 2005-11-30
[QUOTE=taurus]Nope!!!  You just waste another blank CD (I hope you are using CD-RW)...  What program do you use to burn it???[/QUOTE]


Record Now. It came on the PC. I just bought CloneCD. Maybe that will work better. Ok, so if I see it as unbuntu-5.10-install-i386.iso
then thats wrong.

Thanks
Rick

---

### Post by Joeak on 2005-11-30
Dude, you can't take ISO image files and burn them to CD in the exact same way that you do other document files.  With common Windows machines, CD burners come with Nero Burning ROM or Adaptec EZ CD Creator or some such.  You need to locate the option in your burning program that allows you to create a bootable CD from an ISO image file.  

In Nero Express, the bottom option in a list (Data...Music...etc.) is "Disk Image or Saved Project".  Picking that allows you to browse out to pick the single ISO file to use to create the bootable CD, etc.

---

### Post by taurus on 2005-11-30
I suggest you download Nero and use it since most people use it with Windows.   It's real easy to use...  Again, please look at the options from your software for your burner and choose "Burn as image file" or something like that.  Don't just make a copy of it from your harddrive to a CD because you are just wasting your time and the thing will not boot, not in a million years (unless you are trying to install it under VMware)!!!

---

### Post by politicaldog on 2005-11-30
Wow,

I have to say you all are probably right. 

Can I use the file I downloaded already to reburn another disk but USEING THE CORRECT OPTION?..lol or download a new file?

Thanks Everyone........You won't believe how many hours I have into this already...:p 


Rick

---

### Post by taurus on 2005-11-30
Why download it again since you already have it on your computer or on a CD...  Just burn it again and this time, make sure you burn that iso file as an image file.  When it's done, you should see a bunch of directories on that newly burned CD.  

Good luck.

---

### Post by tomwell on 2005-11-30
Man you have it all sorted...

Just burn the image to cd and then boot up...

good luck, let us know how it goes...

Peace

Tom

---

### Post by politicaldog on 2005-11-30
Going on my third atempt at burning this critter.

First two actually are seen by the CD Rom drive because it now hangs there, but never goes beyond that.  The CD says there are 680mb of space used with 63mb free, but you can't see anything on the CD.

Must be me and my burning skills  :D

---

### Post by politicaldog on 2005-12-01
With some help I got it loading now...Thanks Everyone!


Rick

---

### Post by tomwell on 2005-12-01
[QUOTE=politicaldog]With some help I got it loading now...Thanks Everyone!

Rick[/QUOTE]

Glad you got it i the end!!!

Isnt Ubuntu great...? Even if you come into some problems you always get great support from an awesome comunity!!! Am just saying from one noob to another.... 

Peace

Tom

---

### Post by politicaldog on 2005-12-01
I agree. Its a great forum.

I like that even though I'm struggling it doesn't seem like anyone's talking down to me. 

Thanks Again Everyone. I'll get this thing working yet!!!!!!!

Rick

---

