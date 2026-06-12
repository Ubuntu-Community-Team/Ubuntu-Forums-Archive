---
title: "How do I make a tar backup of my home directory?"
date: 2006-01-19
forum: General Help
---

### Post by lapsey on 2006-01-19
i am trying to backup my home folder through tar... while i am sure my syntax is correct somehow it is not creating anything:

> sudo tar -cfz --exclude=*/.thumbnails/* --exclude=*/Desktop/* /home/thomas/ /home/thomas/Desktop/private/User\ Backups/thomas.tar.gz

tar: Removing leading `/' from member names
tar: /home/thomas/.sound-juicer.thomas: socket ignored
tar: /home/thomas/.gnome-system-monitor.thomas: socket ignored
tar: /home/thomas/z: file is the archive; not dumped
tar: /home/thomas/.totem.thomas: socket ignored



it would be great to get this working since I tend to destory my installation every other day (private is a mounted samba share)

---

### Post by GeneralZod on 2006-01-19
The name of resulting the tar.gz file is specified by the -f option, so you should try

```

sudo tar -czf /home/thomas/Desktop/private/User\ Backups/thomas.tar.gz --exclude=*/.thumbnails/* --exclude=*/Desktop/* /home/thomas/ 

```

instead (the old way may have been trying to create a file called "--exclude= blah blah" which is probably not what you want!)

---

### Post by lapsey on 2006-01-19
thanks, General.

The following worked deliciously: 

> sudo tar -czf /home/thomas/Desktop/private/User\ Backups/thomas.tar.gz --exclude=*/.thumbnails/* --exclude=*/.Trash/* --exclude=*/Desktop/* /home/thomas/

That is, everything except:
.thumbnails (200 MB .. why??)
.Trash
and Desktop

cool!

---

