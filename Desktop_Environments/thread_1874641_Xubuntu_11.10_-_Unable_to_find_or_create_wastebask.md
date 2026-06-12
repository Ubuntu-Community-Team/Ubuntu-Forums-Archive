---
title: "Xubuntu 11.10 - Unable to find or create wastebasket directory"
date: 2011-11-03
forum: Desktop Environments
---

### Post by Kronalias on 2011-11-03
In my flight to sanity from Unity to Xfce (Xubuntu 11.10) I've hit a little hiccup.

When I try to delete a file on a network shared directory using Thunar this message pops up in a window ...
"Unable to find or create wastebasket directory"

Using Thunar I can quite happily create files and copy them in that directory - but not delete them.

I'd really appreciate a little help please - any ideas would be very welcome!

---

### Post by LewisTM on 2011-11-03
Would be interested in solving that too. It's certainly a bug for non UNIX filesystems. 
For now, you can just Shift-delete. This will erase the file without attempting to send it to the trash.

---

### Post by gsmanners on 2011-11-03
This problem is similar to:

[https://bbs.archlinux.org/viewtopic.php?id=114774](https://bbs.archlinux.org/viewtopic.php?id=114774)

---

### Post by Kronalias on 2011-11-04
@LewisTM: Thanks! Shift-delete does what I want, so I've marked the thread as solved.

@gsmanners: Also thanks!
I've been mucking about with my /etc/fstab - specifically this line:
```
UUID=0b0164cf-331b-45c9-a019-d2ccfa4be8ee / ext4 errors=remount-ro 0 1
```I confirmed my UID was 1000 with this:
```
-u MY_USERNAME
```and then included uid=1000 in the options. Aall that happened was that the system was unable to mount /
Annoyingly the whole system would only boot in read only mode, so I used a rescue CD to edit fstab back to normal.

Worth a try, but I think I'll just put up with a lack of wastebasket - after all, it's no different from working at the command line...

Cheers, K

---

### Post by LewisTM on 2011-11-04
Hmm, I can confirm that gsmanners's solution does work.
I appended uid=1000,gid=1000 to my network share fstab entry (an SMB share) 
Don't do that for you root '/' entry, that will mess things up for sure!

Now I can send files to the trash and restore them no problem
Still a bug to me but easily fixed

---

### Post by Kronalias on 2011-11-04
> Don't do that for you root '/' entry, that will mess things up for sure!I did and it did :oops:

Now I think I know why I should set up the partitions manually rather than let the Ubuntu installer just bung in root and swap...

---

