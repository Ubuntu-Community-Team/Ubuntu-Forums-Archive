---
title: "How to disable GUI from starting on boot?"
date: 2019-06-01
forum: Desktop Environments
---

### Post by kpatz on 2019-06-01
I have two systems I just upgraded to 18.04 LTS (they were 16.04 before).  One is my main box, primarily a file server but it also serves as a Linux desktop and Virtualbox host so I run the standard Gnome on it (minimal desktop install).

The 2nd box is my backup server, which sits in my closet, with no monitor, keyboard or mouse connected and is just powered up once a week to receive ZFS snapshots from my main server.

I installed the same Ubuntu on both boxes....18.04.2 desktop 64-bit minimal install, so the GUI (Gnome) is installed, along with Firefox etc.  But I would like to have the backup server not start the GUI by default, just boot up so I can ssh to it.

I could have just installed the Server edition on it, but I wanted the same install on both boxes, so the backup server can be swapped in if the main server dies.  But it would be nice to have the machine boot up and not start the GUI by default while it sits in my closet.

I googled how to do it and found a 5 year old query on AskUbuntu, but it didn't work in 18.04.  I tried putting "text" in the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub and ran update-grub.  I also tried **systemctl disable gdm**, but neither of these worked.  The GUI still starts on boot.  In the old init days, disabling gdm (or lightdm) from starting did the trick.  But not so on systemd.

Suggestions?

Thanks...

---

### Post by again? on 2019-06-01
To boot to console...
```
sudo systemctl set-default multi-user.target
```
Reboot.

To boot to display manager greeter...
```
sudo systemctl set-default graphical.target
```


If you wish to start the graphical environment from the console...
```
sudo systemctl start gdm3.service
```

If it's an upgrade you may have lightdm display manager also installed, in which case you could alternatively run...
```
sudo systemctl start lightdm.service
```

---

### Post by kpatz on 2019-06-02
Thanks, that worked!  Marked as solved.

Though, I had a small mishap.  I issued the command thinking I was ssh'd into the backup server.  I wasn't.  I disabled the GUI on my main server instead.  Realized it when I issued the reboot command and my main server rebooted to a console. :confused:

So I'm also thankful you shared the command to undo this and bring the GUI back.  I'm good now.

---

### Post by again? on 2019-06-02
No problem, if you're interested you can look at the relevant files in /lib/systemd/system/
You'll see graphical.target wants a display-manager.service where as multi-user.target does not.

More info... 
```
man systemd.special
```

---

