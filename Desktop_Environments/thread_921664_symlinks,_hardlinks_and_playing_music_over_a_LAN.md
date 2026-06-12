---
title: "symlinks, hardlinks and playing music over a LAN"
date: 2008-09-16
forum: Desktop Environments
---

### Post by neill on 2008-09-16
hi

i have all my music sitting on a headless ubuntu 8.04 server in /home/me/music and the kids both have accounts on the server with there own music folders symlinked to mine

in other words /home/me/music is symlinked to /home/kidA/music and /home/kidB/music

this saves me having to keep multiple copies of the same tunes and means that updates to my music folder are accessible for the kids

this works fine when the kids are using XP - we simply map their music folders and then point their copies of WinAmp (cf amarok or whatever) to the mapped folders to get the music. XP cannot distinguish between the 'real' files and the symlinked ones so it all works great

however ...

now i want to wean the kids off of XP so i need a way of doing exactly the same as the above in (k)ubuntu

so i mount the music folders either using mount -t or in fstab and when i browse to them all i see are the links and an error telling me that the folder to which they point (ie: /home/me/music) doesn't exist (ie is not mounted on that machine - and i have no intention of doing that !!). in other words linux is smart enough to see the symlinks for what they really are !!!

hardlinks *do* work but i'm not about to hardlink 4000 or more songs (as i can't hardlink a folder) and i'm not too sure this won't provide some mechanism by which the original files could get deleted

anyone any ideas how i can get around this ??

thanks

/neill

---

### Post by kpatz on 2008-09-16
So, let me get this straight, each kid has an Ubuntu (formerly XP) box that has an NFS mount to their home directory on the server?

In order for the symlinks to work, the target folder/file that they point to would have to be accessible on their machine.

Question #1:  What is /home/kid# mounted to on their box?  Let's say for example it's /mnt/kid#.  So, when the kid accesses /mnt/kid# they get their server home directory.

To make the music in your folder accessible, you'll need to mount your home folder (or just mount all of /home).  So, for example, mount the /home folder on the server to /mnt on the kid's PC, so they could then access /mnt/kidA, /mnt/kidB, /mnt/me, and so forth just like the corresponding /home folders on the server.

Then, redo your symlinks to be **relative** symlinks rather than absolute.  So, instead of /home/kidA/song1 being symlinked to /home/me/song1, you'd symlink using a relative path, such as ../me/song1.  The easiest way to do this is to go into the kid's home folder and then symlink using relative paths:

```

cd /home/kidA
ln -s ../me/song1 .    # link a single song
ln -s ../me/abc* .    # link all files starting with abc
ln -s ../me/songfolder .    # link a directory full of songs

```

But maybe a better way would be to set up a shared directory for music that you all listen to.

---

### Post by neill on 2008-09-16
OK

if i mount /home/me/music directly onto the kids' PCs then i don't need to redo the symlinks again as i can just point their music players at that mountpoint

```
//server/home/me/music /mnt/kids_music cifs username=kid,password=PW 0 0
```

and let amarok or whatever generate the collection from /mnt/kids

i tend to agree with your suggestion, however, that simply setting up all the music in some family share to which all have access is a better idea

i would need to make that read only for everyone except me to stop someone inadvertently trashing the whole lot, then i could add to it but nobody else, and any stuff they had that themselves could either be kept locally for them or added manually be me later

thanks for the input

:)

/neill

---

