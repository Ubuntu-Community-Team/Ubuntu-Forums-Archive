---
title: "Please, please help..."
date: 2006-09-23
forum: Desktop Environments
---

### Post by PoisonedV on 2006-09-23
I just installed the latest release of Ubuntu. I was trying to get my WUA 1340 D-Link wirelass adapter to work, but it was only for windows, so I spent a long while asking for help on IRC and I got a few things, well it was a tutorial, but the tutorial made no sense, (it was also for suse) Later, I was looking on a page and found this: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) And it had my card on it, but when I downloaded it and looked at it, the thing was a bin file not an inf file! Please please please help!

---

### Post by wildseven on 2006-09-23
you can install ndiswrapper by
```
sudo aptitude install ndiswrapper
```

that should work
get back to us if it doesnt

good luck

---

### Post by PoisonedV on 2006-09-23
Ok, but after that what do I do?

---

### Post by peabody on 2006-09-23
> **wildseven said:**
> you can install ndiswrapper by
```
sudo aptitude install ndiswrapper
```

that should work
get back to us if it doesnt

good luck


I take it you meant well by this post but I'm sure the user could use a little more boost than that :) .

Follow his instructions on installing ndiswrapper but add "ndisgtk" to the end of that.  That should provide you with a GUI which will be located under the administration menu, called "windows wireless drivers".  You should be able to install the windows driver using that gui.  You'll need a copy of the windows driver for your card (unzipped).  Ndiswrapper uses the inf file in combination with the rest of the driver files to install the driver.

If that still doesn't work, make sure you've identified your wireless card correctly (many manufacturers seem to have ver. 1, 2, 3 etc and many of these sometime don't even have the same hardware between versions!) and try other versions of the windows drivers.  If worse comes to worse, you may need to blacklist certain modules that are preventing ndiswrapper from working with your card (this is relatively rare, I had to do it for my WG111 however...).

---

### Post by PoisonedV on 2006-09-23
It didnt come with an inf file...

EDIT: Oh, and also how do I open up that GUI after I already did the command he said?

---

### Post by peabody on 2006-09-23
> **PoisonedV said:**
> It didnt come with an inf file...

EDIT: Oh, and also how do I open up that GUI after I already did the command he said?

sudo aptitude install ndisgtk

Then use the Ubuntu menu and go to Administration -> Windows Wireless Drivers.

Where did you download the windows driver from?

---

### Post by PoisonedV on 2006-09-23
I got it from the disk that came with it.

---

### Post by Sef on 2006-09-23
```
sudo aptitude install ndisgtk
```

```
sudo aptitude install ndiswrapper
```

Before you doing either one of the commands, it is best update your computer:

```
sudo aptitude update
```

then do the other commands.

---

### Post by PoisonedV on 2006-09-23
Well, if that uses the internet then I can do that. But now that ive got ndiswrapper what do I do now?!

---

### Post by peabody on 2006-09-26
If you don't have internet in your ubuntu desktop, you could download the debian packages on another computer and copy them over and double click to install them.  The two you are looking for are located here:

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils_1.8-0ubuntu2_i386.deb&md5sum=15bf250f0a1114686655232175339cc2&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils_1.8-0ubuntu2_i386.deb&md5sum=15bf250f0a1114686655232175339cc2&arch=i386&type=main)

and here:

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu1_all.deb&md5sum=820f3a749abd2cb2d097c362103cd07e&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu1_all.deb&md5sum=820f3a749abd2cb2d097c362103cd07e&arch=all&type=main)

The dependencies for ndisgtk include python-glade2 and pygtk which have numerous other dependencies, so you may have trouble installing ndisgtk.  That's okay, but it means you'll have to resort to the command line to setup ndiswrapper.  I don't have the instructions for ndiswrapper off the top of my head, but I believe it was as simple as typing "ndiswrapper -i <inf file>" within the unzipped driver folder.  The command "man ndiswrapper" will give you a page of instructions.  press q to quit that page.

Do you have an ethernet card or modem in your computer?  Is there anyway you could use those to temporarily hook up to the Internet just so you could install ndisgtk to get your wireless card working?

---

### Post by PoisonedV on 2006-09-26
Well, hmmm, I think i'm going to get some freebie dial-up service in the meantime. But after I asked that, I later found the .sys and .inf files... I just don't know which is which.

---

### Post by peabody on 2006-09-26
> **PoisonedV said:**
> Well, hmmm, I think i'm going to get some freebie dial-up service in the meantime. But after I asked that, I later found the .sys and .inf files... I just don't know which is which.

Are those still around?  I guess I'm a little surprised...you have no way of connecting ethernet to your computer?

---

### Post by PoisonedV on 2006-09-27
well, it turns out i found the .inf file but it says i dont have the hardware. :\

---

### Post by midia on 2006-12-24
Hello,

To install your drivers for the wua-1340, maybe my post located here:

[http://ubuntuforums.org/showthread.php?t=270756&highlight=wua+1340]("http://ubuntuforums.org/showthread.php?t=270756&highlight=wua+1340")

will help you.

To get your Ubuntu CD to work with Synaptic as a source of programs like ndiswrapper, you have to add the CD to Software sources, then run Synaptic and search for ndiswrapper:

System > Adminstration > Software Sources,
Click tab:  Third Part
Click button:  Add CDROM with your Ubuntu CD in the drive
Click close

Start Synaptic (  System >  Administration > Synaptic )
and search for ndiswrapper.

Hope this helps.

---

