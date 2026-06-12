---
title: "Xsession error."
date: 2009-01-03
forum: General Help
---

### Post by Infamshxr on 2009-01-03
I was looking online and couldn't find anything... What I did was uninstalled everything I could find for openoffice2 so that I could install openoffice 3, but must have uninstalled a bunch of other stuff I need in the process cuz I found out I uninstalled Gedit and firefox, which I already reinstalled. Everything was working great until I turned the computer off and back on again and now it won't boot. I just get a black screen if I boot into Gnome (default), and if I boot into KDE I get an error saying Xsession: Failed to launch.... Can't remember the exactness. I figured I accidently uninstalled Xwindow manager, but not sure... Any help? PLEASE! I really don't wanna reinstall and lose everything.

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
Boot into the terminal and type xfix. See if you can type startx and get the GUI.

---

### Post by Infamshxr on 2009-01-03
So, will that fix it permanently then? I didn't think it was that easy to what I did. Also, do I need to be connected to the internet? Cuz I'm  not right now...

EDIT:
nvm, tried it, not connected. fixx command wasn't found. and when I did startx it said that it was already running.

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
No and no... it will give xorg the default settings and hopefully start gnome. You will have to figure out what happened exactly and reinstall everything or find out what caused the problem but at least you, hopefully, won't have to reinstall.

---

### Post by Infamshxr on 2009-01-03
Sorry to repost, but I edited my post, it didn't work...

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
What does happen when you boot? try to see if you can see any errors along the boot process (aside from the fore-mentioned). Were you just going through synaptic checking boxes?? Just kidding... Do you know what packages you removed though?

---

### Post by Infamshxr on 2009-01-03
Boots up normally until I go to login. Doing a disk  check by itself right now. Once I login:

Gnome - black screen. no icons no taskbar. I can see my mouse though. If I hit the print screen button on the keyboard, I get the "generic looking" window for it, my themes aren't activated.

KDE - First tells me that Run Xclient script is my default session (Gnome isn't listed on the session list) Then once I click Just for this session it tells me:
"Xsession: unable to launch "/usr/lib/kde4/bin/ startkde" X session --- "/usr/lib/kde4/bin/startkde" not found; falling back to default session."

Sadly, yes I was unchecking boxes in Synaptic to remove anything that had to do with openoffice...

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
I don't see how openoffice and gnome/KDE could be related but hey... I'm not a developer. Regardless... I guess reinstall gnome and KDE. ```
sudo apt-get install --reinstall ubuntu-desktop
``` I don't know if that will give you kde but when you get gnome back then ```
sudo apt-get autoremove kde
``` then ```
sudo apt-get install kde
```  Can't think of any other solution. You should backup before hand just in case.

Don't know if this means anything but I found this command ```
sudo apt-get install --reinstall kubuntu-desktop
```

Perhaps try both...

---

### Post by Infamshxr on 2009-01-03
Sounds logical. Not sure either...

I would need to be connected to the internet for that one though I would assume though... How would I go about backing up everything prior? I have no idea how with out a GUI... :-/

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
That would take some research. I've never had to use the DVD drives from the terminal. Try googling "DVD backups from terminal" or "cd backups from terminal" or if you just want to put it on another partition you can use ```
sudo cp /location of files you want to back up /where you want the files backed up
``` About the apt-get commands... yes the internet is needed. I think you can probably get the packages from the install disk too. Google "install ubuntu-desktop from live cd"

if you need help with file locations don't hesitate to ask.

---

### Post by Infamshxr on 2009-01-03
What about a flash drive?
Do you know how to back things up that way? Basically just my home folder and one document on my desktop is all I need.

I guess what I need to know is how to view the files in a folder from the command line and how to copy files and folders to something, flash drive sounds like it would be the easiest way.

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
Yeah... plug your flash drive in and boot up into the terminal. I can't remember the command for finding the hardware (my brain loses thing quite often) but you can type ```
cd /media
``` the type ls. ls will list all files in the /media folder. Look for the name of your flash drive. You might also want to compare the file sizes of the things in your /home/username directory to see if they'll fit on the flash drive. Use ```
du -sm /home/username
``` (username being replaced with your actual username) That command will show file sizes in MB and then you should know the size of the flash drive. Copy whatever you need from your home folder by typing ```
sudo cp /home/username/files /media/usbdrivename
```

---

### Post by Infamshxr on 2009-01-03
what about copying folders? is that just cp too? like:

cp /home/username/music /media    ? (without the ?, of course)

I know how to look for the hardware. fdisk -l :)

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
Exactly... either files or folders should work with cp. You could even use mv for moving them instead of copying them. It's up to you. I find that sometimes cp gives me trouble so mv is a good alternative but it will delete the one in the home folder.

---

### Post by Infamshxr on 2009-01-03
Well I went to mount my flash drive and it told me it couldn't find it in the fstab. Although its listed in the fdisk...

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
hmm... add it to fstab? That's beyond me. I've never run into such a problem.

---

### Post by Infamshxr on 2009-01-03
Nvm, brain fart. Didn't specify a mount point lol

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
Haha... do it all the time when mounting iso files.

---

### Post by Infamshxr on 2009-01-03
Can I copy multiple folders or files at a time? If not its ok. Just figurd it would be quicker. Lol

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
Not sure... try cp --help and/or man cp and check out what it says about it. man cp is going to give you a lot of info but if you're a fast reader you can skim through and find out. Press q to get out of the man page.

Might take less time to just copy them one at a time than to find out though... I run into that a lot.

---

### Post by Infamshxr on 2009-01-03
Also how do I view hidden files and folders?

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
```
ls -a
``` Should do it for ya. If you want a long list it's ```
ls -la
``` You can get all info for a command by typing ```
'command' -h or man 'command'
``` There's a lot of options that you might find useful in there like ```
ls -latr
``` is a cool one. Check them out.

---

### Post by Infamshxr on 2009-01-03
Hey! I just thought of something. Since I suck at this command line stuff, couldn't I use my live CD to boot the computer and mount the hard drive and flash drive to do the backup stuff? Or will I run into permission problems?

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
Hahahahaha.... now why didn't I think of that? I've been on vacation for 3 weeks now so I'm not truly inclined to think straight. Sorry I made it more difficult for you. You shouldn't see any permission problems. Off to bed... let me know how it goes.

---

### Post by Infamshxr on 2009-01-03
Lol not a problem thanks for all the help. Ill be sure to let you know how it goes. Thanks again for all your help!

---

### Post by Infamshxr on 2009-01-05
Well the update is I had to doa fresh install :( Everything is back to normal, good news is a few small problems that I had prior to the reinstallation are now fixed. lol

---

