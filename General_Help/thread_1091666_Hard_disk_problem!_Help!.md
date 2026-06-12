---
title: "Hard disk problem! Help!"
date: 2009-03-09
forum: General Help
---

### Post by Carl_Barks on 2009-03-09
Hello there fellow ubunt-ers.
I've been using a feisty distro for almost 2 years now. I have standar disk with the OS in it and a NTFS disk where i kept all my data (music, pictures, files etc.).
I had mounted it perfectly, ntfs-3g and all.

Today, i accidentaly close the pc by pressing the power-supply's button that's on the back of the pc unit.
I turned it on again immediately and logged in my OS. 

BUT!

My mounted hard disk had disappeared! OMG! I thought that it could had broke down or sth, but in the GNOME Partition Editor I can see it. It was unmounted. If press right-click mount it mounts it all well, but as we all know, if i mount it this way i won't have permission on it.

So i went to mount it again with the traditional way.
sudo mount -a ...

Failed to mount '/dev/sdb1': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!

...

I tried to "ignore" it and do the :
sudo chown -R

the command started running, and I could see all my file names and directories go through the screen via the change permission thing.

So, at least i know they DO exist in the hard drive. BUT, CAN I ACCESS THEM?
I don't have a Windows PC right now to do the chdsk /f ...

What do u think? Is there any hope for my files ? Anything else i can do?

---

### Post by taurus on 2009-03-09
What is the exact error message when you try to mount it from a terminal?

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```

---

### Post by Carl_Barks on 2009-03-09
the exact same i write above too:

Failed to mount '/dev/sdb1': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.

---

### Post by taurus on 2009-03-09
So you don't have windows on your machine that you can run that command to fix it?

---

### Post by Carl_Barks on 2009-03-09
No, I don't. That's why i asked here. 

I read that there is a similar equivalent command on ubuntu called ntfsfix .

Should I use it? Cause i read that it could damage the data on the disk, and my top priority now is to save my files.

---

