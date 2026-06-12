---
title: "[SOLVED] Disk Space Issues"
date: 2008-12-30
forum: General Help
---

### Post by j2fraser on 2008-12-30
I'm having problems with my system which I strongly suspect are disk space related. Evolution, for example, is throwing errors storing the inbox: "No space left on device."

I thought (oh boy) that it would be a good idea to get rid of some of the rather large (~7-11Gb) backup files on my disk to create space, so I ran (oh boy) "sudo nautilus" and then deleted them from /var/backup... except, the system did not reflect space freed up on / (on my system = /dev/sdb1)

When I reverted back to the shell, it said something about entries left in hash tables... ouch. I rebooted onto the LiveCD and ran fsck.ext3 on /dev/sdb1, but no errors showed.

df-h shows:
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             138G  134G     0 100% /
varrun                1.8G  116K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G   72K  1.8G   1% /dev
devshm                1.8G   12K  1.8G   1% /dev/shm
lrm                   1.8G   44M  1.7G   3% /lib/modules/2.6.24-22-generic/volatile
/dev/sdb2             137G   50G   88G  37% /media/sdb2
overflow              1.0M   40K  984K   4% /tmp


...but /dev/sdb1 is the same partition from which I just deleted about 30Gigs of backups!

Everything my system does is now cramped by space issues, but I (seem to) have precious little to spare. I have run apt-get clean, emptied the trash, etc. -- all to no avail. Help!

---

### Post by redilyn on 2008-12-30
Can you run the disk usage analyzer to see whats using all the space?

I think that root has its own trash folder as well. You might want to check to make sure there is nothing left in there.

To check this:

Open nautilus as root
Browse to root's home
press ctrl+h
look for .local/share/trash/files

---

### Post by 2hot6ft2 on 2008-12-30
For future reference this has a nice cleanup feature [http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)
Also if you run ```
sudo apt-get autoremove
``` it will clear out some packages that are no longer needed.

Localepurge - purges language files for things you don't speak or anticipate speaking.

GtkOrphan- removes orphaned files, frees disk space
INSTEAD... You could just install deborphan and create a new filter in Synaptics:

Settings > Filters > New and uncheck all boxes except 'Orphaned'. You'll now have a new category in the Custom tab that does the same as gtkorphan.

---

### Post by redilyn on 2008-12-30
One small problem with him installing Localepurge or deborphan

He has 0% free space :)

---

### Post by 2hot6ft2 on 2008-12-30
> **redilyn said:**
> One small problem with him installing Localepurge or deborphan

He has 0% free space :)
Obviously he would have to do the other clean ups first. Personally I would start uninstalling things I don't need first right after the autoremove and then autoremove again afterwards. Could always reinstall them once the space issue is resolved.

---

### Post by nikgare on 2008-12-30
How did you delete those backups? By deleteing them to your trash bin?
Delete your trash!

---

### Post by j2fraser on 2008-12-30
> **redilyn said:**
> I think that root has its own trash folder as well. You might want to check to make sure there is nothing left in there.

To check this:

Open nautilus as root
Browse to root's home
press ctrl+h
look for .local/share/trash/files
Thanks everybody. The above was the ticket. All my old backups were parked in root's trash. Check this out...

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             138G   23G  108G  18% /
varrun                1.8G  116K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G   72K  1.8G   1% /dev
devshm                1.8G   12K  1.8G   1% /dev/shm
lrm                   1.8G   44M  1.7G   3% /lib/modules/2.6.24-22-generic/volatile
/dev/sdb2             137G   50G   88G  37% /media/sdb2
overflow              1.0M   44K  980K   5% /tmp
/dev/sda5             130G   39G   92G  30% /media/disk


That's a heck of a lot of (useless) backups! I did keep one complete backup, just in case though... :) Oh... btw, I also reconfigured my backup setup!

---

