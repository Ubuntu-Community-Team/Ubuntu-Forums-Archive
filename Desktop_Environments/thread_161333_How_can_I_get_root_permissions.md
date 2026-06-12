---
title: "How can I get root permissions?"
date: 2006-04-16
forum: Desktop Environments
---

### Post by dnccnd on 2006-04-16
Hallo!

I am following these instructions in the wiki in order to get my webcam to work:

[https://wiki.ubuntu.com/Webcam?highlight=%28webcam%29](https://wiki.ubuntu.com/Webcam?highlight=%28webcam%29)

The problem is that I cannot edit the file sources.list without root permissions. I remember that I read in other threads how to do this through Terminal but I can't find it anymore.

Can anyone help?

---

### Post by aysiu on 2006-04-16
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

---

### Post by babalou on 2006-04-16
[QUOTE=dnccnd]Hallo!

I am following these instructions in the wiki in order to get my webcam to work:

[https://wiki.ubuntu.com/Webcam?highlight=%28webcam%29](https://wiki.ubuntu.com/Webcam?highlight=%28webcam%29)

The problem is that I cannot edit the file sources.list without root permissions. I remember that I read in other threads how to do this through Terminal but I can't find it anymore.

Can anyone help?[/QUOTE]
start a terminal from the Application menu (top-left of your screen if you have not changed the default config), sub-menu Accessories.
Then from the terminal window, run your command (prefixing it with sudo):
to edit your config file, run from terminal: sudo gedit sources.list


yb

---

### Post by nanotube on 2006-04-16
for a good read on the whole root thing, check out this ubuntu wiki page:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by dnccnd on 2006-04-16
Hi guys!

Thanks a lot for all the information. It works!

---

