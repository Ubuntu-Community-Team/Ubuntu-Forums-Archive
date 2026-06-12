---
title: "Few very simple questions"
date: 2005-01-28
forum: Desktop Environments
---

### Post by wk1989 on 2005-01-28
Hello, I'm a new Ubuntu user with less than a day of experience, and I'm starting to like it!
However, I have 2 simple questions:
1. How do I log off Ubuntu saving all the settings? Because I tried the "sudo halt" command but it doesn't save any changes I made on GNOME.
2. How do I upgrade the version of Firefox that came with Warty to the latest version? I've searched the forums but the backports method doesn't seem to work (Synaptics tells me it cannot find the directory:().
3. I mounted one of my Windows partition and I'm faced with 2 problems. The first 1 is that folder and file names in Chinese doesn't display properly, it displays as a bunch of question marks. The 2nd problem is that I can't seem to play the mp3 files there, even if I move them namesto my Linux partition. BTW, the MP3 files have icons with a little lock on the upper riight side, I'm assuming this is the cause of the problem, or is it that warty doesn't come with mp3 codecs?

Thanks in advance!

---

### Post by Rancoras on 2005-01-28
[QUOTE=wk1989]1. How do I log off Ubuntu saving all the settings? Because I tried the "sudo halt" command but it doesn't save any changes I made on GNOME.[/QUOTE]

From a GUI, click Computer > Log Off and make sure the "save settings" box is checked.

[QUOTE=wk1989]2. How do I upgrade the version of Firefox that came with Warty to the latest version? I've searched the forums but the backports method doesn't seem to work (Synaptics tells me it cannot find the directory[/QUOTE]

Search around the forum, several people have installed the download version successfully.

[QUOTE=wk1989]3. I mounted one of my Windows partition and I'm faced with 2 problems. The first 1 is that folder and file names in Chinese doesn't display properly, it displays as a bunch of question marks. The 2nd problem is that I can't seem to play the mp3 files there, even if I move them namesto my Linux partition. BTW, the MP3 files have icons with a little lock on the upper riight side, I'm assuming this is the cause of the problem, or is it that warty doesn't come with mp3 codecs?[/QUOTE]

You didn't say, but I'm assuming the windows partition is NTFS?  If not then it's most likely FAT32.  Either way follow the instructions to mount it at [www.ubuntuguide.org](www.ubuntuguide.org) .  It's an invaluable resource.

---

### Post by retype on 2005-01-28
[QUOTE=wk1989]Hello, I'm a new Ubuntu user with less than a day of experience, and I'm starting to like it!
However, I have 2 simple questions:
1. How do I log off Ubuntu saving all the settings? Because I tried the "sudo halt" command but it doesn't save any changes I made on GNOME.[/QUOTE]
Already answered

[QUOTE=wk1989]2. How do I upgrade the version of Firefox that came with Warty to the latest version? I've searched the forums but the backports method doesn't seem to work (Synaptics tells me it cannot find the directory:().[/QUOTE]
You probably just entered wrong info.

[QUOTE=wk1989]3. I mounted one of my Windows partition and I'm faced with 2 problems. The first 1 is that folder and file names in Chinese doesn't display properly, it displays as a bunch of question marks. The 2nd problem is that I can't seem to play the mp3 files there, even if I move them namesto my Linux partition. BTW, the MP3 files have icons with a little lock on the upper riight side, I'm assuming this is the cause of the problem, or is it that warty doesn't come with mp3 codecs?

Thanks in advance![/QUOTE]
to play mp3 you have to install gstreamer-mad.
the lock on the file is because you can't write to it (NFS can only be monted read-only) and when you copy you copy with the read flag off, just turn it on on your linux partition then there will be no lock, but withou gstreamer-mad you will not be able to play it.

---

### Post by wk1989 on 2005-01-29
[QUOTE=Rancoras]From a GUI, click Computer > Log Off and make sure the "save settings" box is checked.[/quote]
It's the "save current setup" box right? I did it but it doesn't save my resolution settings.


> Search around the forum, several people have installed the download version successfully.
Thx, I'll try that.



> You didn't say, but I'm assuming the windows partition is NTFS?  If not then it's most likely FAT32.  Either way follow the instructions to mount it at 
Nope, it's a FAT32 drive, and I'm only expereinceing this problem with mp3 files, so I assume it doesn't have anything to do with the way I mounted the drive.

---

### Post by Rancoras on 2005-01-30
[QUOTE=wk1989]Nope, it's a FAT32 drive, and I'm only expereinceing this problem with mp3 files, so I assume it doesn't have anything to do with the way I mounted the drive.[/QUOTE]
You added gstreamer-mad like retype said?

---

### Post by wk1989 on 2005-01-30
[QUOTE=Rancoras]You added gstreamer-mad like retype said?[/QUOTE]
I just installed that, doesn't seem to work, I tried with Totem and Rhythmbox.
Totem told me "unable to play, reason unknow" or something like that, Rhythmbox told me "there's no plugin installed to handle a .mp3 file".

---

### Post by wk1989 on 2005-01-30
[QUOTE=wk1989]I just installed that, doesn't seem to work, I tried with Totem and Rhythmbox.
Totem told me "unable to play, reason unknow" or something like that, Rhythmbox told me "there's no plugin installed to handle a .mp3 file".[/QUOTE]
 Problem solved! Thanks for your support guys!! Works like a charm now!

---

