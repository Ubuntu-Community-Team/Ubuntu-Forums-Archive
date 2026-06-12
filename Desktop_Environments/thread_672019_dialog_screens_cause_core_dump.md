---
title: "dialog screens cause core dump"
date: 2008-01-19
forum: Desktop Environments
---

### Post by stuart.crouch on 2008-01-19
Its getting to the point now where I dont often need help with ubuntu, but this has got me completely stumped and pretty much stops me doing anything productive on my PC

Anytime I launch an open/save dialog screen from open office or gedit the entire window closes.  I ran both from a commandline to try and get some output and all that appears is

gedit
Segmentation fault (core dumped)

I've disabled all my fancy effects, and set everything back to the human theme (something I read in another post for this problem in open office).  Both still crash and I have no idea how to fix it.  I tried a complete removal of open office, and the re-installing from synaptic but that didn't help either :(

Can anyone give me some pointers on what to do here as I'm out of ideas!

Thanks
--
Stuart Crouch

---

### Post by jeffus_il on 2008-01-19
Open a terminal, type ```
du -h
``` to see your disk space usage.
Open Nautilus and empty trash in all the accounts you use.

[COLOR=Red]Sorry about the typo[/COLOR]

---

### Post by reiserfs on 2008-01-19
Actually it should be:

```

df -h

```

to show your disk space usage.

Try running:

```

strace -f gedit

```

That may give you some pointers, specifically near the part it dies.

---

### Post by stuart.crouch on 2008-01-19
I emptied my trash, it only had 31 mb of data.  Its only me that uses this PC so I checked root as well but there was no .Trash under /root
 
Then I ran df -h

```

stuart@stuart-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.6G  901M  6.3G  13% /
varrun                505M   88K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   76K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda5              40G   18G   21G  47% /home
/dev/sda6             7.8G  2.5G  5.0G  34% /usr
/dev/sda2              56G   37G   20G  65% /windows

```

Nothing looked like it was running out of space...
so I ran strace -f gedit, here are the last few lines

```

[pid  7132] gettimeofday({1200753596, 620893}, NULL) = 0
[pid  7132] open("/home/stuart/.gtk-bookmarks", O_RDONLY|O_LARGEFILE) = 16
[pid  7132] fstat64(16, {st_mode=S_IFREG|0600, st_size=113, ...}) = 0
[pid  7132] read(16, "w@\253\377\211\352\246nc\233\207VI\365\345W\366\36|\375"..., 113) = 113
[pid  7132] close(16)                   = 0
[pid  7132] open("/home/stuart/.gtk-bookmarks", O_RDONLY|O_LARGEFILE) = 16
[pid  7132] fstat64(16, {st_mode=S_IFREG|0600, st_size=113, ...}) = 0
[pid  7132] read(16, "w@\253\377\211\352\246nc\233\207VI\365\345W\366\36|\375"..., 113) = 113
[pid  7132] close(16)                   = 0
[pid  7132] --- SIGSEGV (Segmentation fault) @ 0 (0) ---
[pid  7162] <... futex resumed> )       = ? ERESTART_RESTARTBLOCK (To be restarted)
[pid  7161] <... futex resumed> )       = ? ERESTART_RESTARTBLOCK (To be restarted)
[pid  7162] +++ killed by SIGSEGV (core dumped) +++
Process 7162 detached
[pid  7161] +++ killed by SIGSEGV (core dumped) +++
Process 7161 detached
Process 7132 detached

```

The last thing it tried to do was access .gtk-bookmarks, so I had a quick peek.  It looked like random crap, usually gtk stuff is human readable (ini or xml) so I made the assumption it was corrupt and renamed the file to .gtk-bookmarks-old. 

Tried both oOffice -writer and gedit, and it worked!  I can now open and save files again.

Thanks for your help guys :)

---

