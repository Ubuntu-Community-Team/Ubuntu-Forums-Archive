---
title: "Burning the iso?"
date: 2009-03-04
forum: General Help
---

### Post by tonguefucal on 2009-03-04
OK so I have an iso burner but when I open the download from ubuntu, I don't see an .iso file ANYWHERE.

So I got the iso burner, selected create iso image, and selected the entire ubuntu folder and burned it. Put that into the computer i'm trying to recover and got an error that there was no detectable bootable media.

Please help.

---

### Post by mb_webguy on 2009-03-04
I'm not sure what you're asking.  Are you saying that you downloaded the Ubuntu LiveCD iso, and now want to burn it?  If so, you shouldn't be trying to "open" it at all.  Any decent disc burning application will allow you burn a disc image directly.

If you downloaded something and it isn't an iso, then I have no idea what you *did* download, but it wasn't a LiveCD disc image.

---

### Post by tonguefucal on 2009-03-04
Oh what the heck. I see, my vista was showing the ISO from ubuntu as a friggin RAR file with the RAR icon and I was opening it thinking it'd be IN there.

thx

---

### Post by tonguefucal on 2009-03-04
OK so I DID have an ISO this time but the computer says there's no bootable device. When I put the windows installation CD in it does work but when i go to repair windows, neither of the two sata drives shows up, no version of windows is apparently present, etc.

Why can't I load this iso, regardless of the hard disc status if the windows vista iso loads ok/

---

### Post by winding.roadie on 2009-03-04
Are you trying to burn the ISO like you would a normal CD or DVD?  'Cuz that doesn't work.

You need some sort of ISO Writer.  Since you are still running Windoze, [this should help you out.]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm")

---

### Post by lindsay7 on 2009-03-04
I can't tell what you are doing, but, this is what you need to do.

1. Download Ubuntu, it will be a file that ends with .iso.

2. Burn that file to a cd or dvd using cd burning program that will burn an .iso file.  Not all programs will do that. There should be a choice of what type of fiel you want to burn, audio, data, data iso, etc.

3. Put the cd or dvd into the computer so that the computer start up from being off with the Ubuntu cd or dvd in the drive.  It should start up and give you the choice to start the live Ubuntu program or install. It also will let you check the cd to see if it is good.  You can install Ubuntu from the live session too.

---

### Post by tonguefucal on 2009-03-05
> **lindsay7 said:**
> I can't tell what you are doing, but, this is what you need to do.

1. Download Ubuntu, it will be a file that ends with .iso.

2. Burn that file to a cd or dvd using cd burning program that will burn an .iso file.  Not all programs will do that. There should be a choice of what type of fiel you want to burn, audio, data, data iso, etc.

3. Put the cd or dvd into the computer so that the computer start up from being off with the Ubuntu cd or dvd in the drive.  It should start up and give you the choice to start the live Ubuntu program or install. It also will let you check the cd to see if it is good.  You can install Ubuntu from the live session too.

Did just that. I think that because it's burned to a DVD, that's why the computer isn't loading it on boot. I even went into bios and turned off the HD.

---

### Post by lindsay7 on 2009-03-05
I there is an ubuntu iso file on the disk the computer should start if the bios is set to start form a cd or dvd drive. Just to be sure, did you burn the file to a cd or a dvd. Does the drive you are trying to start from read a dvd if you burned it to one?  If you put the disk that you burned into your computer when windows is running what does it show is on the disk?

---

### Post by tonguefucal on 2009-03-05
Burned an iso disc onto a dvd inserted to a dvd player. when its in my computer, it says that i have to choose a type of dvd (write, rewritable, etc) to format it or something similar. it wont run

---

### Post by mister_p_1998 on 2009-03-05
If its an Ubuntu Cd iso, you have to burn it to a *[COLOR="Red"][SIZE="5"]CD[/SIZE][/COLOR]*

There are Ubuntu DVD Iso's but the standard image has to be burned to a CD..

Steve

---

### Post by houcem on 2009-03-05
What a mess.OK your .ISO ubuntu image looks like a .RAR archive because when you installed WinRAR it associated .ISO Files to...WinRAR! this is done by default when you install using the nextnextnext method. Well now I will tell you a secret : you can burn cd ISO on DVD but it's a waste of free space and money. Now you need to burn the ISO using a software like this one : [http://www.filehippo.com/download_imgburn/download/41bddbf02c6551641f056c4a4d514433/](http://www.filehippo.com/download_imgburn/download/41bddbf02c6551641f056c4a4d514433/) launch that software, select your .ISO file, insert a newly purchased CD or DVD and burn it! After that restart your computer with the created media in the drive and the boot from it then the installation should start! if you don't succeed to boot from the media then let me know me.

---

### Post by avtolle on 2009-03-05
A CD image may be burned to DVD without causing any problems related to that. 

I'm still not clear on what the OP did, after downloading the iso file. Thus, the questions that follow:

1) Was the md5sum of the iso checked before burning?

2) Was the iso file burned *as an image* to disk at a slow speed (4x has always worked for me?

3) Was the computer restarted to boot from the DVD (as this is what the OP used)?

4) Is there a hardware problem with the drive? I ask this due to the comments made in post #4 above. 

5) Is the drive being used a DVD/CD drive, or is it a CD drive only?

---

### Post by abhilashm86 on 2009-03-05
best option is burning a easy way of ISO,
download infrarecorder[http://infrarecorder.org/]("http://infrarecorder.org/"), then just browse iso file and burn.

---

### Post by lindsay7 on 2009-03-05
It may be the best thing for you to do is go to the ubuntu site and get a disk shipped to you. That way you will have one you know is good,

---

### Post by winding.roadie on 2009-03-05
> **lindsay7 said:**
> It may be the best thing for you to do is go to the ubuntu site and get a disk shipped to you. That way you will have one you know is good,

+1, that seems like the simplest solution.  You can either request a free CD, or buy a DVD that will work just fine.

---

### Post by tonguefucal on 2009-03-06
Burned "ubuntu-8.10-desktop-i386.iso" to a CD-R and I get the same problem. When I put it back in my own desktop where I burned it, and click on it, I get a prompt "Prepare this blank CD" with a box below to enter a new name....EVEN THOUGH i just burned it (using CD BURNER XP). When i try to do anything like explore it I get teh same message.

---

### Post by tonguefucal on 2009-03-06
This is TOO weird. I got IMGBURN and followed your directions, burned an image to the disc (CD-R) and when it was completed (as the prompt said) the DVD Drive's window opened to show the completed file and theres NOTHING IN THE DISC, although when I remove it, you can clearly see it was burned. It must be my burner?

---

### Post by Jimmynemo2 on 2009-03-06
I might try an alternative burning program- I know and like CDBXP, but if you're not getting a burn done with it, try something like infra recorder, or ISO-Recorder- these will help you to burn it properly. (particularly ISO-recorder.

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

Thats the page for it, and its a very helpful program if you're getting any grief burning the ISO as an ISO not as a single data file on the disc or somehow not burning at all.

Good luck!

---

### Post by Jimmynemo2 on 2009-03-06
Sorry just saw your reply, and now mine is no longer helpful. I might think it would indeed be your media or your burning drive. Have you tried burning anything else to see if you can burn either a regular data disc or a different ISO file if you have one? 

It seems either the drive is bad, or we're having a learning curve burning ISO files. It'd be worth trying to burn a different type of disc to find out- as its very unlikely to be a bad drive that can only not burn iso files (nearly impossible)

hope this helps.

EDIT: also on that burn that looks like there is something on it, look for any box that says "close session" or Disc-at-once and check them. It might be leaving it open for future burns, but with ISO's that'd be useless

---

### Post by tonguefucal on 2009-03-06
Put another CD/DVD burner into my tower and tried again, no luck. Rebooted from CD drive and got a "BOOT DISK FAILURE" message, the CD is useless. 

Tried to burn some pix to a CD, that worked fine and everything was great. But these iso's are just a huge fuggen pain in the asp!

---

### Post by tonguefucal on 2009-03-06
checked the MD5sum and it didn't match, downloading desktop-i386.iso from ubuntu again

---

### Post by entr3p on 2009-03-06
***_Burning a ISO image_***
In Windows:
What you will first have to do in Windows is download the free/open source burning program called [InfraRecorder]("http://infrarecorder.org/?page_id=5") and install it. Once you've installed it you will need to open it up and on the top go to "Actions --> Burn Image..." and choose the ISO image you downloaded.
[IMG]http://i42.tinypic.com/2a8hveu.png[/IMG]
Now change the "Write speed" to 4x or a similar speed. Every other setting is alright but the reason for slowing down the write speed is to ensure the ISO image gets burned correctly onto the disc.
[IMG]http://i42.tinypic.com/2crqe1l.png[/IMG]
Now press "Ok" and wait until InfraRecorder changes the status to "Operation completed." and ejects your disk out. If everything went correctly you have now successfully burned the ISO image to the disc and it's ready to use.

In Ubuntu:
In Ubuntu this process is much easier for the fact that you don't have to install any extra programs. Simply right click on the ISO image and click "Write to Disc..." and a new window will appear.
[IMG]http://i43.tinypic.com/dyxeys.png[/IMG]
In the new window change the "Write speed" to a slow speed around 4x and press "Write". Once the burning process is done your disk tray will open. If everything went smoothly then you have successfully burned the ISO image to the disc correctly.

---

### Post by tonguefucal on 2009-03-06
got the iso to burn (the md5sum has was wrong) and now when I load it onto the laptop i select load w/o changed and it just processes for a minute or two then goes to a white screen with a cursor. nothing else?

---

### Post by sgosnell on 2009-03-06
Even with a good .iso, it's very possible to burn a defective CD.  Try burning it one more time with ImgBurn, at a slow speed.

---

### Post by entr3p on 2009-03-06
> **sgosnell said:**
> Even with a good .iso, it's very possible to burn a defective CD.  Try burning it one more time with ImgBurn, at a slow speed.

I recommend using InfaRecorder. It's open source and free. I just wrote the guide a couple of posts back :P.

---

