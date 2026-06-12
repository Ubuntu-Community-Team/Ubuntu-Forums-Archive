---
title: "AAAAAAH!! What Happend!!! I can't login IN!!!"
date: 2008-07-09
forum: Desktop Environments
---

### Post by 4t0m1c_w07f on 2008-07-09
I tried logging into my gnome session and I got this:

```

/etc/gdm/Xsession: Beggining session setup...
Can't create dir /home/jared/Desktop
Can't create dir /home/jared/Desktop
Can't create dir /home/jared/Templates
Can't create dir /home/jared/Public
Can't create dir /home/jared/Documents
Can't create dir /home/jared/Music
Can't create dir /home/jared/Pictures
Can't create dir /home/jared/Videos
Can't create dir /home/jared/
Setting IM through im-switch for locale=en_ZA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default

(seahorse-agent:6065): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory `/home/jared/.gnome2/': Permission denied
```

HELP HELP HELP

---

### Post by p_quarles on 2008-07-09
What happens when you log in to a terminal session and run this?:
```
sudo /etc/init.d/gdm restart
```
And, what is the output of the following?:
```
id jared
```

---

### Post by 4t0m1c_w07f on 2008-07-09
```
uid=1000(jared) gid=1000(jared) groups(1000),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),124(sambashare)
```

---

