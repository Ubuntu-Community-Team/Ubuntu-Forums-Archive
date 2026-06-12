---
title: "Installation problem with Diablo 2"
date: 2007-05-19
forum: Gaming &amp; Leisure
---

### Post by psionyk on 2007-05-19
Alright, I'm stumped, as I got this game to install in a prior Linux installation, but now I can't get it to install whatsoever (in four different Linux distros using the exact same wine version) so I have no idea what has changed.

In Ubuntu, the cd drive mounted to its normal location (/media/xxxxxx) and I configured the drive in winecfg to point to it.  I run the install.exe file in wine, and the setup screen loads just fine, I select full installation and input my cd key, followed by the install directory (C:\Program Files\Diablo II) which is pointing to the correct ~/.wine/drive_c directory in Linux.  However, once the window pops up indicating "copying files", absolutely nothing happens.  I've even created an iso image of the install disc, and it still just sits there and does nothing.  I've tried this same procedure in Arch, Ubuntu, openSUSE 10.2 and FC6, and all no dice, exactly the same problem.  CD mounts, initial screen loads, options selected, but files won't copy over.

I'm ready to pull out my hair by the roots, anybody know what the heck is going on here?

TIA for the assist!!

---

### Post by eilu on 2007-05-20
check and see if your .wine or .wine/C:/Program Files (or similar) folders are marked as 'root' if so, do a chmod to change file permissions. Could be the problem; sometimes it happens.

---

### Post by edv on 2007-05-22
It's because the progress bar hides the "change cd" dialog. After inputting the installation directory, move the setup window to some side of your desktop and then click ok. Now you should see the cd changing dialog in the middle. You have to do the same if you install the expansion.

---

### Post by psionyk on 2007-05-23
^^^

OMG... you've gotta be kidding me, that's all the problem was?  Strange that never happened to me before.

Well, I'm not sure whether I should thank you or hide under a table... :redface:

Yep, I've decided.

Thanks very much for the help with this.  Now if you'll excuse me, I have to find a table. :)

---

### Post by yosser on 2007-06-01
Ah hahahaha, I had this exact same problem.

Thanks!

---

### Post by elnur on 2007-06-03
> **edv said:**
> It's because the progress bar hides the "change cd" dialog. After inputting the installation directory, move the setup window to some side of your desktop and then click ok. Now you should see the cd changing dialog in the middle. You have to do the same if you install the expansion.
It helped, thanks!

---

### Post by dsdexterds on 2007-09-08
Hi guys, noob here :P, I am dying to play Diablo 2, and I put in my install CD and click on install.exe, wine takes it and runs with it, but I just get "insert install CD in driver" with ok and cancel, pressing ok does nothing what so ever to help matters, is there something I am doing wrong or something I should be doing, please help

Thanks in advance guys

---

### Post by WIGGMPk on 2007-09-08
Do this for progress bar to not be hidden by install screen...


winecfg

Graphics Tab: Emulate Desktop (xxxXxxx) whichever resolution you want.

Save & Exit

sudo wine /media/cdromX (path to install/setup.exe)

shouldnt have a problem after that.

---

### Post by dsdexterds on 2007-09-08
Nope, it is still saying insert the CD, thanks for trying to help me though, is there anything else I could be doing wrong?

I don't get to start the install, it comes up straight after I open the install.exe

Thanks in advance

---

### Post by WIGGMPk on 2007-09-09
Are you switching cd's for a full install or are you using cdromX mounted as an iso??

In other words..

If your doing a full install and are switching cd's by making "winecfg" emulate a virtual desktop. It should work.

If that doesnt work, try mounting each CD as an ISO in like /mnt/<diablo>..

Once your done with that Cd, put the next one in the drive and mount it with a different ISO name.

Its pretty straight forward. There should be some tutorials around on the web or these forums.. But im way to tired to find them, just an idea if you havent went that route before.

---

### Post by dsdexterds on 2007-09-09
I am not even getting to the part that lets me pick the installation, as soon as I try to run install.exe or setup.exe it somes up with the message bex saying "insert install CD" and I have tried taking the CD out and putting it back in, I have tried mounting it from an ISO, I have tried the other CDs as well, is there anything that I could be doing wrong or anything you think that may help

Thanks in advance

---

### Post by markywmson on 2007-10-05
I know this is a semi-old thread, but I'm also having the same problem.  Did you get an answer?  Or does anyone know why I can't even progress to the 'install screen'?

---

