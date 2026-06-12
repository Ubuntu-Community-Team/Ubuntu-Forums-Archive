---
title: "Network share is smbfs mounted, but mp3s still won't play."
date: 2006-07-25
forum: Desktop Environments
---

### Post by Cordate on 2006-07-25
My fstab file has the following line added to it:
```
//apocalypso23/My\040Music  /mnt/Vikki  smbfs  credentials=/etc/samba/credentials,uid=1000,iocharset=utf8,codepage=unicode,unicode,umask=022 0 0
```
and I've done a ```
sudo mount -a
``` and now the icon for the shares is appearing on my desktop, but when I browse to an mp3 file on that XP box, I still can't play it here on the Ubuntu box. Am I missing something from the fstab entry?

Edit: and I've found that the /mount/Vikki folder contains weird things:

[IMG]http://img.photobucket.com/albums/v67/Pixy_Styx/Posts/weirdthings.png[/IMG]

Hmmmm.....    :confused:

---

### Post by it.henrik on 2006-07-26
Strange .. how does it look like if you go there through places-network servers-windows network etc etc

You know that ubuntu cant play mp3:s from a standard installation? its easy to fix though. Just search for a howto or something

---

### Post by philippe_carlo on 2006-07-26
> **Cordate said:**
> My fstab file has the following line added to it:
```
//apocalypso23/My\040Music  /mnt/Vikki  smbfs  credentials=/etc/samba/credentials,uid=1000,iocharset=utf8,codepage=unicode,unicode,umask=022 0 0
```
and I've done a ```
sudo mount -a
``` and now the icon for the shares is appearing on my desktop, but when I browse to an mp3 file on that XP box, I still can't play it here on the Ubuntu box. Am I missing something from the fstab entry?

Edit: and I've found that the /mount/Vikki folder contains weird things:

....


Not sure if it will help but try changing the fstab line into this (create the /media/Vikki directory first):
```

//apocalypso23/My\ Music       /media/Vikki       cifs    credentials=/etc/samba/credentials,dmask=777,fmask=777,user 0 0

```

---

### Post by Cordate on 2006-07-26
Hm..  it's the next day, I my fstab file is exactly the same as yesterday, but now it times out when connecting :S It seems like this connection is inconsistent- even yesterday sometimes it would tell me that a folder had no contents the first time I opened it, and then display the actual contents if I tried it again. 

carlo, I tried the cifs & media/Vikki thing (I'd actually already tried changing to media/Vikki :) ), but got various errors:

```
WARNING: 'dmask' not expressed in octal.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead.
WARNING: 'fmask' not expressed in octal.
WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.
mount error: could not find target server. TCP name apocalypso23/My Music not found
No ip address specified and hostname not found

```

And, yes, mp3s do play in XMMS on my box when they are "local" files- apparently that's why this share needs to be mounted, so that XMMS will view them as being local files. Otherwise I have to copy them over to my Ubuntu box and that's a pretty inefficient way to do it!

---

### Post by mwtb on 2006-07-31
The warnings about dir_mode etc. are resolvable by reading the "man mount.cifs" pages, however,for now you can probably ignore them. The bit you should try changing is the //apocalypso23/ reference. Change that to be the IP address of the machine, e.g. //192.168.0.1/.

---

