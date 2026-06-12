---
title: "How can I recovery /usr permission heirachy?"
date: 2008-12-23
forum: General Help
---

### Post by tee4cute on 2008-12-23
I'd done a big mistake. Actually, I didn't know how important about the /usr/* permission heirachy is before, so I'd changed the permission by using command

"chown -R <myuser> /usr".

Then, I rebooted the computer and I noticed that the "network manager" was disappeared from the taskbar. I tried to open it from menu "System -> Administration -> Network" and It said "You are not allowed to access system configuration", so I tried to open it in terminal and it showed the error about "wrong permission of setuid or some kinds like that". The other system tools such as "Time and Date" "Users and Groups" ... are gone too!.

I'd tried to change the permission back by "chown -R root /usr" and reinstall the package "gnome-system-tools" but it didn't work.

I've found the forum that is likely my case. They suggest to backup the data files and reinstall the os.

Anyone has a better solution for me? (I've installed many programs and packages and I don't want to waste the time to reinstall them all again.)

Thanks for any supports.

---

### Post by Titan8990 on 2008-12-23
That type of user error can only be fixed by freshly installing a new system or manually changing every permission to match a working system's permissions.

---

### Post by tee4cute on 2008-12-23
Thanks Titan8990 for rapidly answer.

That's mean I've to reinstall ubuntu now T^T.

(Good luck everyone !!!)

---

### Post by Titan8990 on 2008-12-23
Don't forget to backup files you may want to keep.

---

