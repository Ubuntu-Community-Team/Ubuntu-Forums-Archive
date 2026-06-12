---
title: "Is this a bug (media:/ related)?"
date: 2005-06-11
forum: Desktop Environments
---

### Post by SGC on 2005-06-11
I'm not sure if this a known bug or just my own problem. 

Folders accessed by **media:/** can't be moved to the trash and there is no "share" tab in folder properties.

When I try to delete a folder, i get this error message:
*creating folders is not supported with protocol trash*

The same folders when accessed from **/media/** can be deleted and shared

If this is not a bug, how can I fix it?

---

### Post by Arthemys on 2005-06-12
**media:/** is the same as say **smb:/** or **http://**
They're protocols, it's probably a bug in Nautilus because essentially **media:/** just browses the /media directory.

---

### Post by Firetech on 2005-06-12
[QUOTE=Arthemys]**media:/** is the same as say **smb:/** or **http://**
They're protocols, it's probably a bug in Nautilus because essentially **media:/** just browses the /media directory.[/QUOTE]
 I don't think it's a bug in Nautilus because this is the Kubuntu forum.
media:/ in Konqueror also browses hard disks, so I guess the share thing just isn't implemented.
The folder thing might be a bug though.

---

### Post by SGC on 2005-06-12
I'm using Konqueror not Nautilus

Can anybody please confirm that folders can't be deleted from **media:/** using konqueror.

---

### Post by Takis on 2005-06-12
I don't really get what you mean. Keep in mind that 'media:/' and '/media/' are not the same thing - see attachments.

Uhm...how did you create a folder in 'media:/' in the first place? When I open Konqueror there, I get a listing of my harddrive partitions and my floppy drive (and a CD, if it's in).

---

### Post by SGC on 2005-06-12
[QUOTE=Takis]I don't really get what you mean. Keep in mind that 'media:/' and '/media/' are not the same thing - see attachments.

Uhm...how did you create a folder in 'media:/' in the first place? When I open Konqueror there, I get a listing of my harddrive partitions and my floppy drive (and a CD, if it's in).[/QUOTE]
 I was talking about folders that start with media:/ 

examples:
media:/hdc1/home/SGC/FOLDER_NAME
media:/hdc1/root/Desktop/FOLDER_NAME

Basicaly any folder in my hard disk that accessed from media:/ I can't deleted

If I access the same folder from one of my mount points /media/hdc1, /media/hdd1, and /media/hda1 I can deleted and share it on the network.

---

### Post by Takis on 2005-06-13
Okeydokey I had a look. You can't actually trash the folder, although proper delete (SHIFT+Del) works.

WRT to sharing, my guess is that the utilities (e.g. Samba) you use to share a folder require a proper (i.e. /some/thing) path to the folder, rather than something like media:/ .

I wouldn't call this a bug, just part of the way the system works, I guess.

---

### Post by SGC on 2005-06-13
[QUOTE=Takis]Okeydokey I had a look. You can't actually trash the folder, although proper delete (SHIFT+Del) works.

WRT to sharing, my guess is that the utilities (e.g. Samba) you use to share a folder require a proper (i.e. /some/thing) path to the folder, rather than something like media:/ .

I wouldn't call this a bug, just part of the way the system works, I guess.[/QUOTE]
 Ok, Thanks Takis

---

