---
title: "Only as root I can access a FAT32 partition"
date: 2005-05-02
forum: Desktop Environments
---

### Post by joni on 2005-05-02
Hello, all.


Newbie question, I guess.

I have a FAT32 partition which is mounted as boot time using the default options.
The owner of the files in that partition is root, and I can't have write access to them.

I can delete or rename files using the Konsole and sudo, but when I login as user "joni" I can only edit copies of the files and not the files themselves (e.g., in OpenOffice).

How can I have write access to these files?

I tried changing the ownership of a particular file using chown:

sudo chown joni abc.doc

but I get a "operation not permitted" message.

I also tried changing the permissions using chmod:

sudo chmod a+w abc.doc

I get a message saying that the file mode was changed to "rwxrwxrwx" (as I wanted), but when I do:

ls -l

i see that the mode didn't really change and that it is still "-rwxr-xr-x".

What am I doing wrong?

Again, this is probably a newbie question, and there must be some fundamental fact about ownerships and permissions in Linux which is escaping me...  ;-) 

Thanks in advance.

Joao

---

### Post by nad on 2005-05-02
This is odd.

Unmount the volume. Modify the /etc/fstab line for this file system with the options: rw,user,noauto  instead of defaults.

Now the drive should show up in your Disks window (I'm not sure where as I use gnome ubuntu). Doubleclick the drive to mount it as 'joni'. Any different?

---

### Post by jamez on 2005-05-03
add these options to your fstab entry:
```
user,rw,umask=000
```

---

### Post by joni on 2005-05-03
I haven't tried any of those yet, but I hope they will work.

That first suggestion makes perfect sense to me, but there would be the disadvantage of losing the automount at boot time, right?

I also found the "umask" solution in the "Unofficial Ubuntu Starter Guide".

(sorry for posting without searching properly... the starter guide should be the first place to look...)

I'll try them and then let you know.

Thanks a lot for the responses! :grin: 

Joao

---

### Post by joni on 2005-05-05
Yep, it worked perfectly.

Thank you!

Joao

---

