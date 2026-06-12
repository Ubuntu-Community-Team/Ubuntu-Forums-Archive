---
title: "Mounting WHS Shares - Do Not Have Write Privilleges"
date: 2009-03-07
forum: General Help
---

### Post by Andysan on 2009-03-07
Hi all,

I am trying to mount my WHS shares so that i can access them easily from Ubuntu Hardy.  If i navigate to smb://server/music/ i can write to my music directory no problem, but when i mount the directory at /mnt/server/music using the following line in fstab i cannot write to the directory:

//ipaddress/music /mnt/server/music cifs username=Andy,password=mypass,users,auto 0 0

I am thinking maybe i need to chmod on my /mnt/server/music directory, but i think permissions are fine?

drwxrwxrwx 1 root root 0 2008-10-01 09:32 users
drwxrwxrwx 1 root root 0 2008-10-02 11:57 video
drwxrwxrwx 1 root root 0 2009-03-07 11:51 pictures
drwxrwxrwx 1 root root 0 2009-03-07 12:53 music

Thanks in advance.:popcorn:

---

### Post by Andysan on 2009-03-07
Ive delved into this a bit deeper and its quite strange - under mnt/music, i can write files no problem.  If i navigate into mnt/music/subdirectory i can also write files, again, this is cool.

However, if i try to write to mnt/music/subdirectory from the mnt/music, i get a permissions error.  Seems i can only write to the current working directory?:(

---

### Post by s.dalas on 2009-03-07
> **Andysan said:**
> Ive delved into this a bit deeper and its quite strange - under mnt/music, i can write files no problem.  If i navigate into mnt/music/subdirectory i can also write files, again, this is cool.

However, if i try to write to mnt/music/subdirectory from the mnt/music, i get a permissions error.  Seems i can only write to the current working directory?:(

There is some mounting priveleges under "User and grups". Give it a try.

---

### Post by Andysan on 2009-03-07
Thanks,

I've taken a look but cant find anything re mounting - it seems all i can really do in Users & Groups is change the group i belong to and whether i can use tape drives etc.  Thanks for your suggestion though, it may just bt that im looking in the wrong place.

The issue really seems to be with subdirectories.  For example, I use Rhythmbox to rip CD's to my server, stored as follows:

/mnt/server/music/artistname/albumname/track1.mp3

When i try to rip a CD, it creates the artist and album folders but gives me a permissions error.  I click OK, and try to rip again to the same destination and it works OK.  It seems that it cant cope with creating subdirectories and writing to them in one swoop.

Does anyone have any suggestions please?

---

### Post by Andysan on 2009-03-07
To anyone with the same issue, i found that it is because root mounts the shares and then i access them (user), i think anyway.

I had to express the noperm parameter to overcome this:

//IPADDRESS/SHARE /mnt/FOLDER cifs username=USER,password=PASS,users,noperm,auto 0 0

---

