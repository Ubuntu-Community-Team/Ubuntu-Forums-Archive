---
title: "cannot run some applications"
date: 2019-02-22
forum: Desktop Environments
---

### Post by sharkodlak on 2019-02-22
I can't run gnome calculator, musescore and some other apps. Ubuntu 18.10, also experiencing this in Ubuntu 18.04. From command line I see this:
```
shark@sharkuf:~$ gnome-calculator
 cannot create user data directory: /home/shark/snap/gnome-calculator/260: Not a directory

```
```
shark@sharkuf:~$ ll /home/shark/snap/gnome-calculator/total 24
drwxr-xr-x 6 shark shark 4096 úno 22 17:40 ./
drwxr-xr-x 6 shark shark 4096 úno 22 17:34 ../
drwxr-xr-x 2 shark shark 4096 kv&#283; 10  2018 222/
drwxr-xr-x 2 shark shark 4096 kv&#283; 10  2018 238/
drwxr-xr-x 2 shark shark 4096 kv&#283; 10  2018 260/
drwxr-xr-x 2 shark shark 4096 kv&#283; 10  2018 common/
lrwxrwxrwx 1 shark shark    3 úno 22 17:40 current -> 260/

```

I don't know what's the problem. Can you help me?

---

### Post by TheFu on 2019-02-25
snaps are the issue.  Uninstall the snap version of the package and reinstall the non-snap version.

IMHO, Snaps just aren't ready for common use yet.  Perhaps in 2-3 more years they will be. [https://www.reddit.com/r/Ubuntu/comments/889xjm/is_just_me_or_software_is_broken/](https://www.reddit.com/r/Ubuntu/comments/889xjm/is_just_me_or_software_is_broken/)  I hate using reddit for reference, but the other places are all chearleading and don't seem to say it like it really is. You can read more about snaps from the snap cheer squad here [https://docs.snapcraft.io/snap-documentation/3781](https://docs.snapcraft.io/snap-documentation/3781) - it is a good theory, but practical considerations need much more thought still, IMHO.

Ubuntu has a habit of introducing new technologies well before it is ready.  I'm still waiting for systemd to be ready for production use and it was introduced in 15.10. Seems to need about 2-3 more years too.

BTW, last week a fairly large security problem was announced with snaps, so if you are recently patched, some snap packages may be impacted by the fixes.

---

