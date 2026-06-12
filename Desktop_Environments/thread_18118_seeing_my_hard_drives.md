---
title: "seeing my hard drives"
date: 2005-03-04
forum: Desktop Environments
---

### Post by geovino on 2005-03-04
I just installed Ubuntu and I can't see my hardrives under Disks. I want to be able to see my hda and hdb hard drives. How do I set that up?

Thanks,
Dave

---

### Post by bored2k on 2005-03-04
[QUOTE=geovino]I just installed Ubuntu and I can't see my hardrives under Disks. I want to be able to see my hda and hdb hard drives. How do I set that up?

Thanks,
Dave[/QUOTE]


[hard drives help ; ntfs /fat ](http://ubuntuguide.org/#windows)

---

### Post by lorap on 2005-03-04
as i understand u wanna see volumes belonging to the windows?
am i right friend?
if so then do the next steps:
1.create say folder C:
mkdir /home/yourname/C
2.sudo mount /dev/hda1 /home/yourname/C -t vfat -o umask=000
3.sudo chmod 777
& u're done :)
all this was about your C: volume. if you wanna do the same things with D: drive then
you'd write hda2 instead of hda1.
u'vea good luck buddy!
shalom from holly land
pavel

---

### Post by geovino on 2005-03-05
Thanks, but I tried that and nothing happened. All I want on the desktop is and icon that I clip on to open and I can see the files on the Windows HD, hda. This should be there. Three other distros, Suse, Beatrix, Mepis, all have the drives on the desktop to access. 

How do I do that?

Thanks,
Dave

---

