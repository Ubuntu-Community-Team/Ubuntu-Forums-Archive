---
title: "Lost entire Lubuntu 16.04 Desktop-held broken packages"
date: 2016-06-12
forum: Desktop Environments
---

### Post by roler2 on 2016-06-12
Ok. . .well. . .blew it again somehow. . .not sure what happened. . .

After an update and a reboot I lost my entire Lubuntu Desktop-just a blank screen now with only a mouse and keyboard that do work-I can reboot and get into Recovery Mode etc. So I figured I must have some sort of Desktop still available. Or maybe not.

So I rebooted and went into Recovery Mode and typed in:

sudo apt-get install lubuntu-default-settings 

I believe as I recall that gave me the error messages that I had broken packages and that it was dependent on:

adwaita-icon-theme-full was to be installed but could not be installed and that I held broken packages 

I tried sudo apt-get update --fix-missing and sudo apt-get update -f and sudo apt-get update install -f

Nothing did any good.

Rather than starting over from scratch, I would like to learn what went wrong and to see if the issue can be fixed in Recovery Mode. 

If any of you very brilliant Forum Members can be of help, I would like to learn rather than starting over. Thank you!

---

### Post by CantankRus on 2016-06-12
Have you added any third party ppas?
Is this a Lubuntu install with no other desktop environments.
What is the exact message you get when you run ...
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by grahammechanical on 2016-06-12
> -just a blank screen now with only a mouse and keyboard that do work

Work on what? When users say "a blank screen" it usually means a black screen without any option to use a keyboard or a mouse. Are you getting to a desktop with a background wallpaper but no panels. Or a desktop without a wall paper. You can get to recovery mode but what happens when you select Resume? How far into the loading process does it go?

Regards

---

### Post by roler2 on 2016-06-12
Thank you for the advice and guidance. I have spent a majority of this afternoon trying to fix this. Nothing has worked. Nothing. The only solution appears to be a fresh install. Will Lubuntu 16.04 fit on a CD or do I have to use a DVD?

In regards to the blank screen. . .I get a blank screen with nothing but a functioning mouse and keyboard. The Mouse arrow shows up within the Blank Desktop. No full Desktop, no wallpaper, no panels, no icons, nothing. Just blank. Recovery Mode I can do all the functions. I was able to reinstall the Lubuntu Desktop in Recovery Mode and delete the PPA that may have been causing the issues. However, I do not think the PPA was causing all of the problems. Not sure. I cannot get any type of a Desktop at all.

---

### Post by CantankRus on 2016-06-12
If you think a ppa was causing the problems you should purge the ppa using **ppa-purge** which will revert any packages from a ppa to your releases official packages.
Just deleting the ppa may leave the packages causing the problem on the system.
```
sudo apt install ppa-purge
```

ppa-purge needs the ppa to be enabled to work.
Add the offending ppa again ,update sources and purge...
```
sudo add-apt-repository ppa:[COLOR="#FF0000"]**<user>/<ppa-name>**[/COLOR]
sudo apt update
sudo ppa-purge ppa:[COLOR="#FF0000"]**<user>/<ppa-name>**[/COLOR]
```
A ppa's homepage gives the [COLOR="#FF0000"]**<user>/<ppa-name>**[/COLOR] for adding and purging.
eg look at [**_[COLOR="#B22222"]https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3[/COLOR]_**]("https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3") where the [COLOR="#FF0000"]**<user>/<ppa-name>**[/COLOR] corresponds to **gnome3-team/gnome3**

If you previously added the ppa via terminal you could also check your bash history @ **~/.bash_history** for the correct **<user>/<ppa-name>** to use.
```
history | grep "ppa:"
```

---

### Post by roler2 on 2016-06-13
Yes I did all of that. . .even installed aptitude. . .am able to download in Recovery Mode. . .even reinstalled Lubuntu-Desktop with aptitude. . .still nothing to show for it. . .however what is weird is that when I try to edit anything in the /etc Folder, for example rc.local (a brief message said it was I believe incompatable or something of that nature). I cannot even pull up the file. It doesn't even show the file exists. Even tried remounting command. Still nothing. I cannot even pull up fstab or even grub in /etc/default. Shows it doesn't exist. Grub does exist within the Kernel section and can edit it utilizing the 'e' command. However when I try to open it via the command line utilizing sudo nano. . .nothing. Just comes up with a blank file. Same with rc.local.

---

### Post by CantankRus on 2016-06-13
Oh well, you're the only one that knows what you actually did.
Time to reinstall.

---

### Post by roler2 on 2016-06-14
Actually I don't exactly know what I did to mess things up so bad that they could not be repaired other than a full reinstall.

---

### Post by Omar_Jair on 2016-06-14
try to login using ctrl+alt+F1 and backup your important date to a usb via termial and perform your reinstall.

---

### Post by yoshii on 2016-06-15
You might try installing as a dual boot into a separate partition, but using the exact same username and computer name and password.  That way, you might be able to use the fresh boot / fresh install to mount the old data and copy it into the new area.  Although it's probably just easier to boot into PuppyLinux to copy the files over to flash drive.  PuppyLinux runs as root so you can copy pretty much anything.  You can install PuppyLinux to a bootable flash drive using uNetBootIn.  Or, you can burn it's .ISO to a bootable DVD-ROM or CD-ROM and boot up from that.  Make sure you get one of the PuppyLinux's that has gParted on it.  It's also handy if you ever need to use GRUB4DOS to externally install a working grub bootloader if the Ubuntu one fails.

---

