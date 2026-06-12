---
title: "gnome 2.16 &amp; playing multimedia from smb"
date: 2006-11-11
forum: Desktop Environments
---

### Post by anzevi on 2006-11-11
Hi!

I switched from dapper to edgy and noticed that i cannot play  multimedia files across smb network anymore (throe nautilus smb://server/some_share...).

This goes for all multimedia files (music and videos). They cannot be opened directly on a smb share (except xine is capable of doing this for some video files). In dapper i could play all files thrue smb browser (nautilus) directly. Now, the fun is over :( 

Is this a feature or a bug?

---

### Post by woedend on 2006-11-11
im not sure why it worked earlier and now does not, but i had this problem in xmms, which doesnt recognize smb protocol.  Have you tried using smbfs?  thats what i ended up doing, basically mounts the share to appear as a directory.

---

### Post by jeff777 on 2006-11-11
I have the same issue.  If I browse "smb://Server/Share/" in Nautilus I can't play any movies from my server.  If I actually mount the smb share, I can.

I think this is a permission issue.  I don't seem to have execute permission when connected to an smb share via nautilus (smb://).  Is there anyway to configure what permissions nautilus applies to browsed smb shares?

---

### Post by anzevi on 2006-11-12
It's the same issue with Fedora 6, so looks like this is a "feature" in Gnome 2.16. But why is this feature terminated? I don't get it, seriously.

---

### Post by jeff777 on 2006-11-12
The real question for me is: How difficult is it to configure this "feature"?  Correct me if I'm wrong, but I believe that execute permission is required to play media files.  Looking in the file properties of the movies on my smb share in Nautilus, it looks like I'm missing execute permission.  

Somewhere, some nautilus script or process must mount the smb share with a particular umask.  It should be possible to change it so that it mounts the smb share with execute permissions.  I wonder if this behavior can be changed by editing a config file, or if its necessary to change something in the source and recompile.

I looked through any nautilus configuration files I could find, but I don't see anything obvious.  Anyone else have any idea?

---

### Post by abbeychase on 2006-11-13
> **anzevi said:**
> It's the same issue with Fedora 6, so looks like this is a "feature" in Gnome 2.16. But why is this feature terminated? I don't get it, seriously.

No, it isn't a feature of gnome...  I can do it just fine in Gentoo, although have not tried here (ubuntu) yet.  Have you tried mounting the samba directory where your media files are?  try
```

mount -t smbfs //whatever-the-name-of-media-files-directory-is /mnt/chose-a-mount-point -o username:whatever-the-username-is

```

this is how i access my media server, which is win2k:
```

mount -t smbfs //media/f /mnt/media0 -o username:administrator 
```
 
//media is the name of our media server, got movies and stuff on it.
the /f is one of the hard drives on which we store media (named f on windows)

/mnt/media* is the name i chose to mount the partition on.

then i can cd to the directory and go from there.

---

### Post by kelbizzle on 2006-11-18
> **abbeychase said:**
> No, it isn't a feature of gnome...  I can do it just fine in Gentoo, although have not tried here (ubuntu) yet.  Have you tried mounting the samba directory where your media files are? try chose to mount the partition on.


I tried what you said. It's how I have it mounted already. 
This way= No Dice :-(
Did anyone report it as a bug?

---

### Post by zgornel on 2006-11-18
In order to get full functionality with samba shares, the shares have to be mounted. The nautilus way is just not working.
P.S. One of these days... one of these days I'm gonna see what's this gentoo all aboot. :D

---

### Post by kelbizzle on 2006-11-19
I managed to get it mounted. but for some reason when new files and folders are added to the folder on the computer thats sharing aren't showing up in the mounted drive. I tried to unmount it. I tried remounting it. I checked the permissions But there not showing how come??

---

### Post by Quietlife on 2006-11-19
I have never been able to open avi & mpeg files directly from SMB with mplayer etc, but VLC (Video lan client) loves it :-)

I just changed the default app to open avi&mpg files to VLC and now I can double click files in nautilus and they open and play fine in VLC.

YMMV

Hope this helps

---

