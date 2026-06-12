---
title: "Harddrive Crashed, Trying to Backup"
date: 2009-03-12
forum: General Help
---

### Post by JackisImpact on 2009-03-12
My MacBookPro harddrive crashed. They are going to replace it this evening for me but I want to backup what I can. I put in an 8.04 disk and I can see the files, but they are all locked on permissions. How do I get these permissions off so I can back it up onto my desktop that has space for it? I dont want to lose any pictures of my family or my trip to London.

---

### Post by kmac on 2009-03-12
You can't even copy the files?

Check the permissions of the drive itself in /etc/fstab

---

### Post by JackisImpact on 2009-03-12
> **kmac said:**
> You can't even copy the files?

Check the permissions of the drive itself in /etc/fstab

Its all locked up lol. How would I change it so its just like "WOOHOO LOOK AT ALL MY FILES PLZ"?

And it says /etc/fstab is not a folder. Ive just got the live disk in. Its not installed.

---

### Post by JackisImpact on 2009-03-12
Also I tried to use 'root' in the Ubuntu terminal and change the permissions using chmod 777

Just says such n such is read-only file. lol

I fail hard.

---

### Post by kmac on 2009-03-12
> **JackisImpact said:**
> 

And it says /etc/fstab is not a folder.

fstab isn't a folder, it's a file.

so don't

```

cd /etc/fstab

```
instead...
```

sudo [COLOR="Red"](nano, gedit, vi)[/COLOR] /etc/fstab

```

If possible, post the output.

---

### Post by JackisImpact on 2009-03-12
Sorry. Not much experience doing this.

says

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by Nano_ext3 on 2009-03-12
When you open up the files you need to backup in the File Manager, note the location in the address bar near the top of the screen.  You will have to make sure whatever external drive you are backing the files TO, is formatted as FAT32 or EXT3 etc. so you can copy the files to the drives.  You can copy to an NTFS drive but it will be much easier on your if its FAT32 or a linux partition such as EXT3, such as a large flash drive.

If you want to partition the external hard drive:

[LIST=1]
[*]Open up the partition editor from System > Administration > Partition Editor, or from Terminal Type "sudo gparted"
[*]If you dont have gparted: from termainl type "sudo apt-get gparted"
[*]Located the external device drive you are going to copy the files to
[*]Right click and select "format to:" and choose FAT32 or EXT3 (Preferred is FAT32 for simplicity) 
[*]If the optin to format is greyed out, choose the "unmount" option first then proceed as specified above
[*]Click Apply
[/LIST]

Now, to copy those files , load up gparted via the instructions above, then note the "device" location of your external drive **AND** the location of your MAC OSX drive.  this will look like "/dev/sda1" or something like that.  You should know its the right one because of its Hard Drive size.

**Now:**

[LIST=1]
[*]Open up terminal
[*]Type "cd /dev/location_of_external_drive"
[*]Type "ls -la" and you should see nothing if you formatted it, or files you have on it currently if you did not
[*]Type "sudo mkdir MAC_BACKUP"
[*]We just made a folder for your backup, now open up another terminal window
[*]Type "cd /dev/location_of_mac_hard_drive"  Where like before this is the location of the hard drive you noted in "gparted"
[*]Confirm its yoru drive by typing "ls -la" and note of all the files 
[*]change the group of /dev/your_mac_hard_drive to storage, change permissions to 775 and add users that need to be able to write to disk to the storage group (you need to log out and log in that users before changes are visible).
[*]To do this first log out of the disk by doing "cd /" and then type "chgrp storage /dev/your_mac_hard_drive"
[*]Type "chmod 775 /dev/your_mac_hard_drive"
[*]Now type "gpasswd -a USER_NAME storage" where user name is the current username you have been using in terminal, noted by your prompt name, when you opened up terminal
[*]If you experience issues runnign any command above , place "sudo" in front of the command before hitting enter. (i.e. "sudo command")
[*]To copy from any folder now:  type "cp -Rv FOLDER_PATH /dev/your_external_drive/MAC_BACKUP"
[*]Hopefully this will let you copy what you need, remember, "cd" will change into a new directory, and you do not want to be inside a directory before you copy that directory.  To move "up" a directory level do "cd .." to move up a level.
[/LIST]



Hope this helps and let us know if you have any more issues!


Cheers!

-Nano

---

### Post by JackisImpact on 2009-03-12
Still cant seem to change the permissions.

Ive got 8.04 live disked on my MBP. Trying to change the permissions to then transfer it over the network or on firewire to my Windows XP desktop.

Nothing seems to work.

Incase you were wondering the only OS installed on the MacBookPro that has the harddrive problem, is Mac OS X

and it seems to be the User files for my account that we cant get into. Everything else we can copy or look at. Just not my pictures and music.

---

### Post by Nano_ext3 on 2009-03-12
"sudo chmod 777 /dev/device_name" should have done something.  If now try:

"chown -Rv USERNAME /dev/device_name" and POST the output here.  the v option is verbose, so we can determine what error if at all it tells you.

EDIT:  Could you also , while looking at the folders (as in listing the folders , not being inside the folder yet) could you do a "ls -la" and note what permissions are on the folders in question? (i.e. d_ _ _rwxrwx)  First group is "user", second groups of rwx is "group", and the third group is "all other."  Does doign "sudo chmod 777 MAC_MUSIC" do anything?

Cheers,

-Nano

---

### Post by JackisImpact on 2009-03-14
Used the command "sudo nautilus"

Open up straight away as root and took all permissions off the files. I then copied them onto a friend external harddrive. It was my fault for not even thinking of being logged in as root. Sorry for wasting your time guys! But thanks so much for the help. Be sure to save some of your tips incase I ever need it again!

Have a good weekend!

---

### Post by Nano_ext3 on 2009-03-14
Hey,

NO problem man, it is what I, and others are here for.  If anything It helped me hone my skills more, glad to see you got it working, dont worry I forget the most simple things too sometimes.

Cheers!

-Nano

---

