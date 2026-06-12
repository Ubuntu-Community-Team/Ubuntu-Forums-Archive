---
title: "Cant boot ubuntu"
date: 2009-04-18
forum: General Help
---

### Post by errormessage on 2009-04-18
I just restarted my laptop after installing new video drivers...It came up with a black screen and lots of commands. I have no idea what to do. It looks like the CMD command in windows, I was somehow able to login into it (login is the command I think) and it says this programs included with the ubuntu system are free software along with alot of other stuff.

Please help me! 

Newb learning here, getting to like ubuntu more and more

---

### Post by aaronp on 2009-04-18
> **errormessage said:**
> I just restarted my laptop after installing new video drivers...It came up with a black screen and lots of commands. I have no idea what to do. It looks like the CMD command in windows, I was somehow able to login into it (login is the command I think) and it says this programs included with the ubuntu system are free software along with alot of other stuff.

Please help me! 

Newb learning here, getting to like ubuntu more and more

Don't worry, happened to me a few times when I first started with Ubuntu.
I'm assuming you can login to the terminal? (recorvery mode?) 
If so, run this and see if you can restore the settings:
```

sudo dpkg-reconfigure xserver-xorg
```

Or, if you backed up your xorg.conf before changing settings then just copy it back into place.

e.g. 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak2

sudo mv /etc/X11/xorg.conf.bak /etx/X11/xorg.conf
```

This assumes you have a backup copy of your original xorg.conf saved as xorg.conf.bak in the same directory. First command backs up your current xorg.conf just in case.

---

### Post by mikewhatever on 2009-04-18
Since you are logged in, try uninstalling the newer driver. It would've been nice of you to mention which driver that is, and where you got it from. Then run the following commands:
sudo dpkg-reconfigure xserver-xorg
sudo reboot

---

### Post by errormessage on 2009-04-18
Uhh I typed in the first command and a blue screen came up so I kept on clicking okay and it worked until "keyboard options". I cant do anything because the bottom is in the cmd thing and I cant hit OK or w/e. Please help

EDIT: I think I remember what happened, I was trying to do the fire effect and forgot the hotkey so I started guessing. I winded up hitting ctrl+alot+f1-9 (cant remember which one) and then the problem started.
Already done chkdsk in windows XP (in using dual-boot btw) and that dident help!

---

### Post by aaronp on 2009-04-18
> **errormessage said:**
> Uhh I typed in the first command and a blue screen came up so I kept on clicking okay and it worked until "keyboard options". I cant do anything because the bottom is in the cmd thing and I cant hit OK or w/e. Please help

That is a bit confusing. If I recall you need to press Tab or a right/left arrow to get to the right place then move back to OK and continue.

---

### Post by errormessage on 2009-04-18
> **aaronp said:**
> That is a bit confusing. If I recall you need to press Tab or a right/left arrow to get to the right place then move back to OK and continue.
Nope still dident work. I tried everything, but still couldent get it to work. If I recall, I think I hit ctrl+alt+f6 and the problem started

EDIT: Rebooted pc, selected ubuntu in dual-boot. Loaded then it went to the CMD-like place. Plz help I really like ubuntu and dont want to re-install.

---

### Post by aaronp on 2009-04-19
ok from the terminal can you try this:

```
locate xorg
```

and see if there happens to be a backup of your xorg.conf file somewhere. if so, try doing the copy/move commands i wrote in the first response

---

### Post by errormessage on 2009-04-19
> **aaronp said:**
> ok from the terminal can you try this:

```
locate xorg
```

and see if there happens to be a backup of your xorg.conf file somewhere. if so, try doing the copy/move commands i wrote in the first response

That worked with no error, But I still cant boot. It started after I hit ctrl+alt+f6 when trying to find the hotkey for a special effect in compiz =/

---

### Post by aaronp on 2009-04-19
> **errormessage said:**
> That worked with no error, But I still cant boot. It started after I hit ctrl+alt+f6 when trying to find the hotkey for a special effect in compiz =/

I'm not 100% but Ctrl-Alt-F6 should just take you to a terminal.
I'm not really sure what else you can do sorry, hopefully someonem ore expert than me can assist.

There is definitely a way to get through the xorg-reconfigure step with the right keys and that is likely to be the answer to your issues because you can put the settings back to a safer configuration. I'd keep trying that and do as much as you can to get the 'cursor' to move in the keyboard setup screen.

---

### Post by errormessage on 2009-04-19
> **aaronp said:**
> I'm not 100% but Ctrl-Alt-F6 should just take you to a terminal.
I'm not really sure what else you can do sorry, hopefully someonem ore expert than me can assist.

There is definitely a way to get through the xorg-reconfigure step with the right keys and that is likely to be the answer to your issues because you can put the settings back to a safer configuration. I'd keep trying that and do as much as you can to get the 'cursor' to move in the keyboard setup screen.

Thx for the help, been about 30 mins and still cant get the cursor thing to hit "OK"
 Guess ill haft to stay in winXP longer...crap

---

### Post by mikewhatever on 2009-04-19
> **errormessage said:**
> 
EDIT: I think I remember what happened, I was trying to do the fire effect and forgot the hotkey so I started guessing. I winded up hitting ctrl+alot+f1-9 (cant remember which one) and then the problem started.
Already done chkdsk in windows XP (in using dual-boot btw) and that dident help!

So the newer driver worked before that key combination? What does Windows XP has to do with it?

---

### Post by errormessage on 2009-04-19
> **mikewhatever said:**
> So the newer driver worked before that key combination? hat does Windows XP has to do with it?

yep, new drivers stopped it.
Windows XP I done a scan to fix erros on HDD

---

### Post by aaronp on 2009-04-19
Maybe your chkdsk utility decided to play some games with your ext2 or ext3 linux root partition? Could be a reason why the problems are persisting. not sure though...

I wouldn't say you need to stay with WinXP...at the very worst you can boot up with a LiveCD, wipe your existing Ubuntu install and start fresh. If you have any data to retrieve, assuming the existing partition is still ok you can use the LiveCD to access it before you re-partition.

---

### Post by errormessage on 2009-04-19
> **aaronp said:**
> Maybe your chkdsk utility decided to play some games with your ext2 or ext3 linux root partition? Could be a reason why the problems are persisting. not sure though...

I wouldn't say you need to stay with WinXP...at the very worst you can boot up with a LiveCD, wipe your existing Ubuntu install and start fresh. If you have any data to retrieve, assuming the existing partition is still ok you can use the LiveCD to access it before you re-partition.

Umm I used wubi to install ubuntu and have important stuff on there like my music so I need to get it. I cant find the folder to acess it on winxp and I copyed and pasted all my windows xp stuff to linux and then deleated it in Xp to free hard drive and just kept it on ubuntu so yea I need to acess it badly it has my important data like passwords also =( and emails I need!

---

### Post by aaronp on 2009-04-19
OK, not such a good thing.
I still think the xorg-reconfigure thing is your best option, you will have to figure out how to get through the keyboard bit.

But, for getting your data I found this on the wubi wiki site ([https://wiki.ubuntu.com/WubiGuide):](https://wiki.ubuntu.com/WubiGuide):)

How can I access the Wubi files from Windows?

There are a few Windows applications that can mount ext2-based file systems. See for instance:

    *

      [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
    *

      [http://www.fs-driver.org/](http://www.fs-driver.org/) 

The relevant Wubi files you need to access are located under C:\ubuntu\disks\

---

### Post by aaronp on 2009-04-19
Sorry, found this there as well, might help you to repair it:

How can I access my Wubi install and repair my install if it won't boot?

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.

To check the filesystem you can use:

sudo fsck /win/ubuntu/disks/root.disk

---

### Post by errormessage on 2009-04-19
> **aaronp said:**
> Sorry, found this there as well, might help you to repair it:

How can I access my Wubi install and repair my install if it won't boot?

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.

To check the filesystem you can use:

sudo fsck /win/ubuntu/disks/root.disk

Okay, Im known as a "geek" like person but I have no idea about what your talking. I DO have a live CD, and have mounted .ISO files like games and all that stuff but how do you mount that stuff? Sorry Im a newb when it comes to ubuntu/unix coding

---

### Post by Torgas Prim on 2009-04-19
If you run out of options, reinstall. 30 minutes of your time is all it takes

---

### Post by aaronp on 2009-04-19
> **Torgas Prim said:**
> If you run out of options, reinstall. 30 minutes of your time is all it takes

Agreed but he loses all of his data.

OP - check out the wiki site link I posted and see if that can guide you through.

---

### Post by errormessage on 2009-04-19
Thanks for all your help I gotta go now its 3AM but Ill try tommorrow thx again!

---

### Post by Torgas Prim on 2009-04-19
Sorry, I assumed he could get to his data by a live cd and copy it over to another drive.

My bad

---

