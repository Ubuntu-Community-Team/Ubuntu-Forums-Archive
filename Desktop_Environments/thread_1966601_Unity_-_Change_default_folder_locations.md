---
title: "Unity - Change default folder locations"
date: 2012-04-27
forum: Desktop Environments
---

### Post by TheValk on 2012-04-27
I have searched for the answer here but none appear to work for me.

I have a new install of 12.04.
I want to change the default Music and Video folder locations from my Home directory to a NAS directory.

I understand that I need to edit .config/user-dirs.dirs to point to the new location, which is /media/Nas/Music.

I have tried XDG_MUSIC_DIR="/media/Nas/Music"
I have tried XDG_MUSIC_DIR="$HOME/Music" pointing to a sym link of the same name.

Each time after a reboot the user-dirs.dirs file is rewritten to XDG_MUSIC_DIR="$HOME"  and the special music link in the Home Folder and Computer List is lost.

Any help would be welcome as I quite like the new Unity interface.

---

### Post by nothingspecial on 2012-04-27
What I do is bind the Music on the external drive to my home in fstab like so

First a line to mount the external drive


```
LABEL=media /mnt/media ext4 defaults 0 0
```

Then one to bind the Music directory on /mnt/media to my Music directory

```
/mnt/media/Music  /home/ns/Music  none  bind
```

---

### Post by TheValk on 2012-04-27
> **nothingspecial said:**
> What I do is bind the Music on the external drive to my home in fstab like so

First a line to mount the external drive


```
LABEL=media /mnt/media ext4 defaults 0 0
```

Then one to bind the Music directory on /mnt/media to my Music directory

```
/mnt/media/Music  /home/ns/Music  none  bind
```

Thing  is, this is a NAS drive on the network so I have to mount it with Samba, thus

//lg-nas-n2a2.local/service /media/NasMedia cifs credentials=/etc/samba/credentials,uid=1000,gid=1000 0 0

Music is a subfolder of the mounted NasMedia.

How would the bind operation work?

Thanks

---

### Post by nothingspecial on 2012-04-27
Oh, sorry, missed that.

I am unsure with samba but I would think you might need the netdev option in fstab to prevent it trying to mount the music drive before the network is up.

---

### Post by TheValk on 2012-04-27
OK, I found the answer.

I needed to sudo to /etc/xdg/user-dirs.conf and edit enabled=True to enabled=False.

This prevented my user-dirs.dirs being constantly overwritten by the defaults.

---

