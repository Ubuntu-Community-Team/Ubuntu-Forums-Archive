---
title: "E: Directory '/var/log/apt/' missing"
date: 2009-05-08
forum: General Help
---

### Post by a person on 2009-05-08
Every time I use aptitude, I get:

```
E: Directory '/var/log/apt/' missing
```

I have (or am supposed to have) this in tmpfs.

My /etc/fstab:
[http://pastebin.ubuntu.com/166688/](http://pastebin.ubuntu.com/166688/)

My output to mount:
[http://pastebin.ubuntu.com/166687/](http://pastebin.ubuntu.com/166687/)

Anyone have any ideas?

Why can't apt just create this directory itself?  Other programs seem to do it fine.

---

### Post by aysiu on 2009-05-08
I don't know why apt doesn't just create the directory, but, yes, if you put /var/log as tmpfs in your /etc/fstab then /var/log/apt will be gone when you reboot the computer, since /var/log's contents are in RAM and not on the hard drive.

Maybe you can create some kind of startup script that takes care of it every time you log in? ```
#!/bin/bash
sudo mkdir /var/log/apt
```

---

### Post by ibuclaw on 2009-05-08
You can put what aysiu suggested in the rc.local file
```
sudo gedit /etc/rc.local
```

Although, since that file is ran as root, you do not need to use sudo.
```
mkdir -p /var/log/apt
```
Regards
Iain

---

### Post by a person on 2009-05-09
Thanks for the suggestions.  I've considered a script that creates the directories but what bugs me is that I have /var/log/apt in my /etc/fstab.  I may just have to go the script route.

---

