---
title: "Hardy~Warning! ok i pick up some thing on the net that broke hardy =/"
date: 2008-12-07
forum: General Help
---

### Post by KEE on 2008-12-07
i was looking for limewire and i got some kinda file that took 300g's from my computer?!? its stuck in trash and i cant get rid of it because of permissions. i tried ```
sudo nautilus 
``` but its in trash and i cant seem to get there. i downloaded this file when it was 4.6mb now its grown to 300g's. I get an error now everytime i logon that says i am not able to log on because my hdd is full. Please help!!!

---

### Post by taurus on 2008-12-07
Boot your machine into recovery mode and delete that file from a prompt.

```
rm *filename*
```

---

### Post by KEE on 2008-12-07
> **taurus said:**
> Boot your machine into recovery mode and delete that file from a prompt.

```
rm *filename*
```

how do i do that?

---

### Post by taurus on 2008-12-07
Do you know the name of that file and where it resides?  You have to navigate to where it is and remove it from there.  Otherwise, you need to include the whole path.

---

### Post by frankleeee on 2008-12-07
I saw this post earlier.
[http://ubuntuforums.org/showthread.php?t=1004115&highlight=trash](http://ubuntuforums.org/showthread.php?t=1004115&highlight=trash)

---

### Post by KEE on 2008-12-07
> **taurus said:**
> Do you know the name of that file and where it resides?  You have to navigate to where it is and remove it from there.  Otherwise, you need to include the whole path.

its in trash and its called system32 i already lost all of my Documents/Music/Videos everything that was below trash and its is gone! F***.... 

could you tell me the path set up to trash and what option in recovery do i go ?

---

### Post by KEE on 2008-12-07
> **frankleeee said:**
> I saw this post earlier.
[http://ubuntuforums.org/showthread.php?t=1004115&highlight=trash](http://ubuntuforums.org/showthread.php?t=1004115&highlight=trash)

k i m gona see if i can start it up and try that , but i think i have to do the recovery rm *filename

---

### Post by KEE on 2008-12-07
i really dont know why someone would call it system32 lol. when deleted limewire.exe a window came up about files that cant be deleted from trash. at the time I was like oh thats weird nothing to worry since i got lots memory, not now though haha.

---

### Post by taurus on 2008-12-07
Are you talking about Ubuntu or windows?

---

### Post by KEE on 2008-12-07
> **frankleeee said:**
> I saw this post earlier.
[http://ubuntuforums.org/showthread.php?t=1004115&highlight=trash](http://ubuntuforums.org/showthread.php?t=1004115&highlight=trash)

ha its still there. tough lil bugger

---

### Post by KEE on 2008-12-07
> **taurus said:**
> Are you talking about Ubuntu or windows?

no im on hardy! thats ubuntu i dont use windows =P

---

### Post by taurus on 2008-12-07
Are you running/installing limewire.exe with wine because that thing is windows version.

---

### Post by KEE on 2008-12-07
well ```
sudo rm -rf ~/.local/share/Trash/files/system32
``` does not work at all =(

---

### Post by KEE on 2008-12-07
> **taurus said:**
> Are you running/installing limewire.exe with wine because that thing is windows version.

well i dont have wine any more is its missing along with other things that were there...=( this is an attack...i cant install it either.. i have 0b of free space

---

### Post by KEE on 2008-12-07
> **taurus said:**
> Are you running/installing limewire.exe with wine because that thing is windows version.

taurus what would be that sequence's of the file in trash when i go to recovery and how do i go to recovery?

---

### Post by KEE on 2008-12-07
Please help !!!!!!

---

### Post by SPr on 2008-12-07
How have you booted the PC? From the Ubuntu live CD or by choosing the recovery option from the Grub menu?

From the CD.
open a terminal and enter:
```

mkdir /media/hda
mount /dev/hda1 /media/hda
cd /media/hda/home/USERNAME/.local/share/Trash/files/
ls
rm System32.exe

```
I assumed that Ubuntu would be installed on the first partition of the internal HDD (/dev/hda1) if I'm wrong you'll have use
```

umount /media/hda
mount /dev/hdx /media/hda

```
change /dev/hdx to the correct partition.

From the recovery option in the Grub menu
```

cd /home/USERNAME/.local/share/Trash/files/
ls
rm System32.exe

```
I assumed the name was System32.exe. Change it to the proper name.
[/handholding]

---

### Post by KEE on 2008-12-07
wow that took a long time to delete

---

### Post by SPr on 2008-12-07
:) Glad it's gone.

---

