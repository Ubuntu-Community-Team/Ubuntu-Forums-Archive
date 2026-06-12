---
title: "Mounting ISO files"
date: 2007-04-30
forum: Desktop Environments
---

### Post by daimon on 2007-04-30
Hi I'm new in the forum and I want to give an idea for the new ubuntu. 

It would be great if we were able to mount our .ISO (and similar) files by just browsing and clicking on them with the right-mouse-button.

---

### Post by TACtech on 2007-04-30
try Gmount - A graphical tool to easily mount your CD images

---

### Post by Aetherius on 2007-04-30
How about this then......

crack open a terminal and type

```
gedit ~/.gnome2/nautilus-scripts/mount-iso
```

this will open up a blank text document.

Paste this in:

```
#!/bin/bash
exists=`ls /media/ | grep iso`
gksudo echo "mounting iso"
if [ -e $exists ]
then
gksudo mkdir /media/iso
fi
sudo umount /media/iso
sudo mount -t iso9660 -o loop $1 /media/iso
```

save it, and close it

now type this in the terminal

```
sudo chmod a+x ~/.gnome2/nautilus-scripts/mount-iso
```

now go find you ISO in nautilus and right click it, under the scripts menu select mount-iso and TADA, your iso will be mounted at /media/iso

feel free to hack and chop


;)

---

### Post by Señor Ameba on 2007-05-03
I followed your advise, but due to unknown reasons to me the script didn't work as expected. It created the "iso" folder in /media , but couldn't mount the image file. I didn't have time to  .
se the error message. The terminal said nothing
Anyways, do you have any suggestions on what might be my problem?

---

### Post by taurus on 2007-05-03
Applications -> Accessories -> Terminal
```
sudo mount -t iso9660 filename.iso /media/iso -o loop
df -h
```

---

### Post by lamadredelsapo on 2007-05-13
What is "df -h" needed for? I just did "sudo mount -t iso9660 filename.iso /media/iso -o loop" and it worked fine for me under dapper.

---

