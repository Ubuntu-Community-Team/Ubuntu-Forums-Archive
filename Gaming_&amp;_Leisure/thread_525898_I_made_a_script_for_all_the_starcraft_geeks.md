---
title: "I made a script for all the starcraft geeks"
date: 2007-08-14
forum: Gaming &amp; Leisure
---

### Post by Squee22 on 2007-08-14
I made you guys some fun little scripts, in ubuntu (but should work in other distro's too)

the first one mounts both startcraft and broodwar cd's then launches starcraft the second unmounts both cd's


just install wine
then install starcraft, and broodwar.
make sure they work

copy the two disks and put them in /home/squee/Documents/CDimages
squee should be replaiced with your own user name

make two scripts as follows but replace "squee" with your own user name

--------------------------------------------------------------

#!/bin/bash
#
foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`
sudo mkdir /media/BROODWAR
sudo mkdir /media/STARCRAFT
sudo mount -o loop -t iso9660 "/home/squee/Documents/CDimages/BROODWAR" /media/BROODWAR
sudo mount -o loop -t iso9660 "/home/squee/Documents/CDimages/STARCRAFT" /media/STARCRAFT
wine "/home/squee/.wine/drive_c/Program Files/Starcraft/StarCraft.exe"
done
done
exit0
----------------------------------------------------------------
#!/bin/bash
#
foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`
sudo umount "/home/squee/Documents/CDimages/BROODWAR"
sudo umount "/home/squee/Documents/CDimages/STARCRAFT"
sudo rmdir "/media/BROODWAR/"
sudo rmdir "/media/STARCRAFT/"
done
done
exit0
--------------------------------------------------------------------

launch the first one to mount your cd images and play the game. launch the second script to unmount the cd images

---

### Post by Nkari on 2007-08-15
sounds sweet, need to dig up my CDs.

---

### Post by buttons on 2007-08-15
```
nice -20 wine
```

:-?

Oops, wine thread runs away.  Reboot.

-10 or better yet, -5 is tons safer.  Plus this will only really help if you have other things taking cpu time.  If you do, maybe it would be simpler not to run them.

I would even consider another kernel (ck-based) if you absolutely *need* this level of interactivity.

---

### Post by Squee22 on 2007-08-16
honestly I don't know what nice -20 does. I just added it in there cause it was under the suggestions for starcraft in wine.


it doesn't seem to do much of anything for me

---

### Post by buttons on 2007-08-16
> **Squee22 said:**
> honestly I don't know what nice -20 does. I just added it in there cause it was under the suggestions for starcraft in wine.


it doesn't seem to do much of anything for me

Well, it's not supposed to do *anything*; that is, if you aren't root.  That might mean your nice program has the suid bit set, or it might mean you're running your script as root.

Both are bad.

What nice does is it changes the cpu priority of the program.  The values range from -20 (highest priority) to +19 (lowest priority).  Basically, a program running at -20 gets cpu whenever it wants.  If it runs away with your cpu for any reason, your computer will be absolutely unresponsive.  Not good.

Only root can lower nice priority below 0, to prevent malicious user-level programs from consuming all of your resources.

A not-so-unreasonable way around this is to get the PID of your program, and renice it using sudo.  Something like ```
sudo nice -n -10 `pidof StarCraft.exe`
``` tacked on the end of your script there would probably work.

---

### Post by Squee22 on 2007-08-23
so I did some experimenting and I find it wourks best without the "nice" addition. like "nice does make it run faster, but starcraft also crashes more often, so I've deleted "nice 20,10, 5" from the script

---

### Post by helbuns on 2007-08-27
alright you guys seem to know what your doing, so i just installed the most recent Ubuntu fiest fiery or something, i don't know linux at all i seem to have wine installed and my Nvidia drivers on but trying to mount my cd image in wine i get this

helbuns@helbuns-desktop:/media/cdrom$ mount /mnt/cdrom
[mntent]: warning: no final newline at the end of /etc/fstab
mount: can't find /mnt/cdrom in /etc/fstab or /etc/mtab
helbuns@helbuns-desktop:/media/cdrom$ wine /mnt/cdrom/Setup.exe
wine: cannot find '/mnt/cdrom/Setup.exe'
helbuns@helbuns-desktop:/media/cdrom$ 

the cd is definatly in there, it's my copy from windows, i have no idea what i'm doing so if someone could help me do all this super easy and i can get on starcraft and broodwar i'll love Ubuntu, and i guess wine as well

---

### Post by z987k on 2007-08-27
what would be better is if you could get the online play to work under wine.  Mine always crashes there.

---

### Post by loudnlownoma on 2007-08-31
> **helbuns said:**
> alright you guys seem to know what your doing, so i just installed the most recent Ubuntu fiest fiery or something, i don't know linux at all i seem to have wine installed and my Nvidia drivers on but trying to mount my cd image in wine i get this

helbuns@helbuns-desktop:/media/cdrom$ mount /mnt/cdrom
[mntent]: warning: no final newline at the end of /etc/fstab
mount: can't find /mnt/cdrom in /etc/fstab or /etc/mtab
helbuns@helbuns-desktop:/media/cdrom$ wine /mnt/cdrom/Setup.exe
wine: cannot find '/mnt/cdrom/Setup.exe'
helbuns@helbuns-desktop:/media/cdrom$ 

the cd is definatly in there, it's my copy from windows, i have no idea what i'm doing so if someone could help me do all this super easy and i can get on starcraft and broodwar i'll love Ubuntu, and i guess wine as well

Are you trying to use the actual SC or BW cd, or are you using .iso images and trying to mount them?  If you are using the actual game cd's in the cd drive, they should mount when inserted.  In that case, you shouldn't have to mount anything manually.  The OP's scripts above are only for running the game from a copied image(.iso) saved on the hard drive, which is why they need to be mounted.

---

### Post by helbuns on 2007-09-09
alright sorry it took so long for me to post back, yea i was using an actual cd and just trying to do it the wrong way. i can't remember what i did.. but i got starcraft installed but was unable to do b.net also i don't really know how to install the b.net update once i download from the main site. anyway i just finished migrating all my data and finally i'm a ubuntu only kinda guy.. i'm gonna  come back and try to use these iso files so i can be a real starcraft man. but i have an unrelated question but u gentlemen just seem to know your stuff so i wanna ask u. when i boot i have to select ubuntu to boot everytime instead of it doing it auto, i only have ubuntu on this drive, is there someway i can do it so it always just boots ubuntu quickly, or should i just leave ubuntu running 24/7 anyway and then it won't be an issue, anyway that's my question, and i'll be posting soon when my data finishes and my focus is again STARCRAFT!!! YAY!!!!

---

