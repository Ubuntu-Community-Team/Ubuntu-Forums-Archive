---
title: "XMMS player problems"
date: 2005-05-11
forum: Desktop Environments
---

### Post by Debianforce on 2005-05-11
Hello. First of all. Ubuntu is awesome! Everything works flawlessly.  :grin: 
Except XMMS player. Yes, it works, but if I want to play music from another PC in my LAN, via samba, to a Windows2000 client, which has a share, it displays the name of the song, but I cannot play it. The program Music player i think its called, can however play music from the windows machine. XMMS does not produce any error messages about this.
Is this a common problem in ubuntu, or is it just xmms that dont like windows share's  :-P
Thanks for ANY answer!!

---

### Post by Zelut on 2005-05-11
I'm having the same problem with XMMS.  Actually XMMS isn't playing *any* files from my local or remote drives.  I've just settled on using Music Player for my library.  It seems to work fine... just doesn't look as nice as I remember XMMS could.

---

### Post by Sam on 2005-05-12
If it cannot be read directly from samba, try to mount the share as a local folder.
```
$ sudo mkdir /media/sharename
$ sudo mount smb://computer/share /media/sharename/ -t smbfs -o username=myusername,password=mypassword
```
(There are a lot of threads about this)

---

### Post by andlinux21 on 2005-05-21
[FONT=Comic Sans MS][COLOR=Navy]Is it possible to run shoutcast or icecast using XMMS[/COLOR]?[/FONT]

---

### Post by dmccarney on 2005-05-21
I'm having a very similar problem. I have an external 160 gig harddrive formatted in NTFS and Ubuntu auto-mounts it no problem. Rythmbox can play all of the files off of it no problem but I don't like the interface/media library format very much and I'd like to use XMMS or Beep. I've installed both successfully but both of them can only open the file, display the tag info, and then crash when I try to click play. I see in a post above trying to mount it locally with Samba but this wouldn't apply to me because its not a networked windows drive correct? I'm quite certain that I have the correct mp3 drivers because Media Player (Rythmbox) can play them just fine, but I could be mistaken as I'm fairly new to Ubuntu. Any help would be greatly appreciated.

---

### Post by drspin on 2005-05-21
Disable the XMMS-MAD plugin (if installed) -- try changing the output pluging to Alsa or OSS --

---

