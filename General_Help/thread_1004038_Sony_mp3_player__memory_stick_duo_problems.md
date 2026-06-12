---
title: "Sony mp3 player / memory stick duo problems"
date: 2008-12-06
forum: General Help
---

### Post by DLF44 on 2008-12-06
i have the sony walkman NZW-B105f.
im not sure how to go about mounting it. or get it to work. 

And also, 

If anyone knows,   i have a laptop and when i put in my memory stick duo, nothing pops up, or appears in the computer  folder.

---

### Post by eBoxNet on 2008-12-06
check the computer folder after you plugin your sony walkman NZW-B105f,if you can c it there then right click on it and mount.

copy your files in it and then right click on it and unmount.

---

### Post by DLF44 on 2008-12-06
when i try that it says, 

unable to mount location
cant mount file

---

### Post by eBoxNet on 2008-12-06
have you used it on your windows and then improperly dismounted it?if not you have to add it (i think) to your fstab

---

### Post by DLF44 on 2008-12-06
i used to use it on windows, and it might have been removed imporperly by accident a couple times but more of the time i would remove it correctly


I dont have windows anymore though, just ubuntu. and im not sure what FSTAB is or how to ad it to it

---

### Post by eBoxNet on 2008-12-06
if you didn't remove it safely the "last" time then maybe thats y you r getting the error.

---

### Post by DLF44 on 2008-12-06
ok, i put i into another computer with windows to try and properly unmount it. But Now, when its plugged in, theres no option to safely remove it. either when i right click it, or from the little icon in the bottom right corner.

---

### Post by eBoxNet on 2008-12-06
double click this icon (bottom right) and safely remove your hardware

---

### Post by DLF44 on 2008-12-06
that little icon that normally appears, 
isnt there for the mp3 player now.

---

### Post by eBoxNet on 2008-12-06
do you have any option to remove it from your mp3 menu?

---

### Post by DLF44 on 2008-12-06
no i couldnt find any option to remove it anywhere. 
theres no program with this one either. jsut drag and drop 

i tried it on 3 different computers with windows, and all of them had nowhere to remove it from in any of the normal ways

---

### Post by eBoxNet on 2008-12-06
try to mount from terminal :

1st option : mount -t ntfs /dev/sda1 /mnt/exhdd 
2nd : mount /dev/sda1 /mnt/exhdd

---

### Post by DLF44 on 2008-12-06
this is what i got,
thanx for the quick help by the way

```

dlf@dlf-laptop:~$ mount -t ntfs /dev/sda1 /mnt/exhdd 
mount: only root can do that
dlf@dlf-laptop:~$ mount /dev/sda1 /mnt/exhdd
mount: only root can do that


```

---

### Post by eBoxNet on 2008-12-06
yes..
add sudo before the commands.

sudo mount ....

---

### Post by DLF44 on 2008-12-06
sorry i dont know much about code

this is what i got:

```

dlf@dlf-laptop:~$ sudo mount -t ntfs /dev/sda1 /mnt/exhdd 
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
dlf@dlf-laptop:~$ sudo mount /dev/sda1 /mnt/exhdd
mount: mount point /mnt/exhdd does not exist


```

---

### Post by eBoxNet on 2008-12-06
nah maybe i am just saying craps :p

did the second command return the same? (the one without ntfs)

i think you have to work on your fstab

i am not so sure,never deal with that again ,sorry.

---

### Post by DLF44 on 2008-12-06
yeah, that code was after i tried both of your suggestions. 
im not sure what fstab is?

---

### Post by eBoxNet on 2008-12-06
check this : [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by DLF44 on 2008-12-06
thanx for the help, but  i dont really understand much of that. i dont really know much about code or what many terms mean

---

### Post by eBoxNet on 2008-12-06
check this 2 it may help you.
[http://ubuntuforums.org/showthread.php?t=787041&highlight=Sony+mp3+linux](http://ubuntuforums.org/showthread.php?t=787041&highlight=Sony+mp3+linux)

---

### Post by DLF44 on 2008-12-06
ok, im gonna try with amorak, and see if it  can be mounted with that.

---

### Post by DLF44 on 2008-12-07
alright i got the banshee program and nothing has changed, it shows up in places  but i cant mount it.

---

### Post by eBoxNet on 2008-12-07
[http://ubuntuforums.org/showthread.php?t=1004144](http://ubuntuforums.org/showthread.php?t=1004144)

---

### Post by PocketDog on 2008-12-07
I've got a Sony NWZ. Tried for hours to mount it, it never did work. Then I found that I'd been wasting all that time because Rhythmbox could copy to and from the Sony with no fiddling or plugins. It just worked(tm)

---

### Post by DLF44 on 2008-12-07
how did you do that in rythym box? i dont see my player in it?

---

### Post by PocketDog on 2008-12-07
Sorry this isn't going to be much help but I just plugged it in. It appears on the left menu where the music/radio/podcast entries are if I scroll to the bottom. It's because the NWZ doesn't act as a flash drive but an MTP (whatever that is). Rhythmbox supports them by default

---

### Post by DLF44 on 2008-12-07
yeah, mine just doesnt show up

---

