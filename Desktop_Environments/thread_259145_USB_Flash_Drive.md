---
title: "USB Flash Drive"
date: 2006-09-17
forum: Desktop Environments
---

### Post by RexInTheCity on 2006-09-17
I'm trying to use a USB flash drive to transfer web site files that I'm working on between home and school. I need the Permissions to be 744 in order for the files to work with my web host. When I plug in my flash drive it has the permissions as 444 and it won't allow me to change them on the drive itself or any files on the drive. I tried right clicking on the drive/file > properties > permissions and changing it there but as soon as I check a box it becomes unchecked. I also tried using chmod at the terminal but it didn't work either.

The flash drive is formated as Fat32, school computers use windows xp.

Any help is grateful.

---

### Post by sktx on 2006-09-17
What I would probably do in your situation is copy the files to a "working" folder on my computer when I got home, set the permissions, and copy them back to the USB drive when I was done. 

Sound like something that would work?

---

### Post by spur on 2006-09-17
You might need to change the permissions with the drive connected to the computer it was when the files were originally crreated.

---

### Post by RexInTheCity on 2006-09-17
> **sktx said:**
> What I would probably do in your situation is copy the files to a "working" folder on my computer when I got home, set the permissions, and copy them back to the USB drive when I was done. 

Sound like something that would work?
That might work for a shorterm fix, but currently the files total 132mb so it's not exactly a quick copy over.

Edit: I just tried that and it is not even feasible unless there is a way to change the permission of all the files at once. I assumed highlighting all the files/folders and going to options > permissions would change the settins for all of them but it doesn't.

> **spur said:**
> You might need to change the permissions with the drive connected to the computer it was when the files were originally crreated.
Thats where I tried it.

---

### Post by RexInTheCity on 2006-09-18
*bump*

---

### Post by sktx on 2006-09-18
> **RexInTheCity said:**
> I just tried that and it is not even feasible unless there is a way to change the permission of all the files at once. I assumed highlighting all the files/folders and going to options > permissions would change the settins for all of them but it doesn't.

Try this: cd to the directory to which you've copied the contents of the usb drive, and run this command... 

```
chmod --recursive 744 *
```

note that if you have hidden files or directories (that start with a ".") , you'll have to run the command again, but the second time around add a "." in front of the wildcard, like so:

```
chmod --recursive 744 .*
```

i think that should cover it.  hope this helps.

---

### Post by RexInTheCity on 2006-09-18
Well now that I know I can chmod all the files at once...

Could someone write me a batch file type thing that would copy X folder to Y folder and chmod the Y folder? or point me to a good tutorial on how to do this? (never done anything like that in linux)

---

