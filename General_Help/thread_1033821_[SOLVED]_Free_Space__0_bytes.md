---
title: "[SOLVED] Free Space : 0 bytes?"
date: 2009-01-07
forum: General Help
---

### Post by n2stc on 2009-01-07
My home drive seems to be full, but deleting files and emptying the trash doesn't help.

---

### Post by jerome1232 on 2009-01-07
Can you post the output of these so we can see where your space is being used up at

```
sudo du -hx --max-depth=1 /
df -h
```

---

### Post by n2stc on 2009-01-07
```

4.0K    /srv
48K     /media
4.7M    /bin
3.5G    /root
6.5M    /sbin
16M     /etc
4.0K    /initrd
2.9G    /usr
4.0K    /opt
2.3M    /lost+found
8.0K    /mnt
0       /tmp
381M    /var
0       /proc
3.4G    /home
34M     /boot
228M    /lib
0       /dev
0       /sys
11G     /

```
Thanks

---

### Post by n2stc on 2009-01-07
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              11G   11G     0 100% /
varrun                189M  284K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
udev                  189M   64K  189M   1% /dev
devshm                189M     0  189M   0% /dev/shm
lrm                   189M   34M  155M  18% /lib/modules/2.6.22-15-generic/volatile
/dev/sda6              18G   12G  6.7G  63% /media/XP_SHARE
overflow              1.0M   76K  948K   8% /tmp

```

---

### Post by jerome1232 on 2009-01-07
Right away I notice 3.5GB in /root, have you been deleting alot of stuff in nautilus as root? You need to check what's in there, and delete it if it's just trash.

```
sudo ls -la /root/.local/share/Trash/files

```

if there's anything there then delete like this
```
sudo rm -rf /root/.local/share/Trash
```

---

### Post by n2stc on 2009-01-07
That did it THANKS!!!!

Why did't deleting files from other places work?

---

### Post by jerome1232 on 2009-01-07
This is a guess but if you were deleting them in a root nautilus, then they were getting moved into roots trash, so you aren't freeing up space just moving it to root trash folder.

Emptying your normal users trash obivously won't touch the roots trash folder, so if you delete files in a root nautilus hold shift when you press delete to bypass sending them to trash. They actually get deleted that way.

---

### Post by n2stc on 2009-01-07
Makes sense.  Members should also know that the original symptom was getting bounced back to the log-in screen in KDE 3.5, after the correct password was supplied.  No error or message is displayed.  I found out by going back to the GNOME desk top.

---

