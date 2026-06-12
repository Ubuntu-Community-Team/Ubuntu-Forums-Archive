---
title: "Connected to Samba shares"
date: 2006-06-14
forum: Desktop Environments
---

### Post by MrSam on 2006-06-14
Maybe I'm asking the wrong question about this.

I can see the shared drives in my file server through Network Servers under Places in the Ubuntu menu. I am then able to connect to them and open the drives and work with the files. The shared drives even have icons on my desktop.

The only problem I have at this point is the I don't see them on the file system in programs like mplayer and GnomeBaker so I can't get files from the shares into these programs unless I copy them to a local drive first. In Nautilus they are part of the main tree but don't show up at all in other programs.

Since I can see and use the shared drives it seems they must be mounted somewhere. Does anyone have an idea ablout where within the filesystem they would be found?

---

### Post by Arnaud_B on 2006-06-14
Hi, 
You should be able to access the shares from anywhere... this would be usually mounted in /media/sd* or /media/hd* ... then if you type in a terminal $mplayer /media/sd*/Documents\ and\ Settings/username/My\ Documents/My\ Music/whatever.mp3 it should play :-)
Try to see in nautilus if you can see where the folders you want to access are mounted...
Good luck!
A.

---

### Post by edopizza on 2006-06-19
I have a similar struggle: I need to upload files via a web page by picking them up from a Windows machine. I have first to copy the files locally because I can't access the Network servers from the popup window of firefox. 
In the media folder there are only fd and cd, no sd* or hd*. 
Any idea?

---

