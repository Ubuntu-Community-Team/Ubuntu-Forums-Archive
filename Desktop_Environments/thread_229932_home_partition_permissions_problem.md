---
title: "/home partition permissions problem"
date: 2006-08-05
forum: Desktop Environments
---

### Post by msg on 2006-08-05
My partitions are as follows:

/ 10GB
swap 1 GB
/home 100GB

I just reinstalled ubuntu and reformatted the / and swap partitions but now it won't let me log in

The first message says

--------
Users $HOME/.dmrc fle is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.
--------

Then I click OK and it says

--------
Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

(Box) view details (~/.xsession-errors file)
--------

And in the errors box there's too much for me to type out on this cell phone but it says writing on '/home/msg/.gnome2_private/': operation not permitted' after trying to log in

Thanks

---

### Post by BitTorrentBuddha on 2006-08-05
Boot into a terminal and try (making sure to replace username with your username): ```
sudo chown -R username:username /home/username/
```

---

### Post by msg on 2006-08-05
Thanks a million!

worked perfectly

I didn't know how to boot into terminal so I just kept doing ctrl+alt+backspace until X crashed and a terminal came up :)

---

### Post by BitTorrentBuddha on 2006-08-05
Whatever works, works :D

---

