---
title: "virtual drives"
date: 2006-01-12
forum: Desktop Environments
---

### Post by npodges on 2006-01-12
are there any virtual cd drive tools in the ubuntu repos? (similar to daemon tools, or alcohol 120% on windows)
if so, would wine recognize them?
thanks,
-nick

---

### Post by ritger on 2006-01-12
You don't need those (not for .iso anyways). Support for that is built-into the kernel. Just do
```
$ sudo mount -o loop /Data/something.iso /mnt/destination
```
where something is the iso you want to mount, and /mnt/destionation the destination where to mount to. Make sure the destination exists though.

---

### Post by npodges on 2006-01-12
oh, neat. thanks.

actually though i have an image on here now that's a .nrg (created with nero, i think) are there any tools to handle that? i supposed i could send it to another machine and convert it to iso, or connect a physical cdrom..

---

### Post by npodges on 2006-01-12
i found this:
[http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/Mount-ISO-image-2216.shtml)
which is a free program that looks like it does what i want. moust iso or nrg and converts. thanks.

---

### Post by tetrafuran on 2007-06-29
it all sounds promising however when I attempted to install it (click - > run in terminal) I got this:

> ./install.sh: 146: function: not found

Couldn't find !
Type the full path here or press "Ctrl+C" to abort: 


I don't really understand whants wants. I tried to give it the path to install.sh. same thing.

---

### Post by superyounan1 on 2007-06-29
> **tetrafuran said:**
> it all sounds promising however when I attempted to install it (click - > run in terminal) I got this:



I don't really understand whants wants. I tried to give it the path to install.sh. same thing.

you have to navigate to the location of the script before run ```
./install.sh
```
the "./" means "this directory", when you first start a console window, it automatically goes to the home folder. so either navigate to the location of the script then run that same command again, or type in the full path to the file install.sh

or maybe just right-click on the file install.sh and choose "run in terminal", but its better to do it manually so you can see the output messages

[update] sorry didn't read your other message all the way, didn't realize you entered the full path already. Try now to change the permissions of the file and run it again, run ```
sudo chmod +x ./install.sh
``` or maybe  ```
sudo chmod 777 ./install.sh
```

---

### Post by tetrafuran on 2007-06-30
Thanks for the help. Originally the file had execute rights, so changing it to 777 didn't change the reality much. In any case I did put it to 777 just to see if it works. However I'm still getting the same error. Could it be caused by my 64 bit ubuntu? It wouldn't be the first time. In fact nowadays I seem to blame that for everything even though it might be caused by something totally different.

---

