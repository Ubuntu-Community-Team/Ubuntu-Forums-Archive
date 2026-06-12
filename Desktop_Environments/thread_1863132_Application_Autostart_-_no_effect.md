---
title: "Application Autostart - no effect"
date: 2011-10-17
forum: Desktop Environments
---

### Post by noah++ on 2011-10-17
Hi,

I want my sshfs automounter to start when I log in. I made an entry in the Application Autostart area of my settings for this command,

```
afuse -o mount_template='sshfs -o reconnect %r: %m' -o nonempty -o unmount_template='fusermount -u -z %m' ~/sshfs/
```

but it seems to have no effect. If it worked, then issuing*ls ~/sshfs/me@ssh.mysite.com* would succeed. It doesn't work. Yet if I use the same *afuse* command in a shell, it does work.

Ideas?

---

### Post by ankspo71 on 2011-10-18
Hi,
It is usually better if we create scripts for the longer or complex commands.

```
#!/bin/sh

afuse -o mount_template='sshfs -o reconnect %r: %m' -o nonempty -o unmount_template='fusermount -u -z %m' ~/sshfs/
```

Now save the above code as sshfs-automounter.sh and put somewhere in your home folder.

Now right click on sshfs-automounter.sh, select properties, then in the permissions tab, check the box that says "Allow this file to run as program". Or you can use chmod +x to make the script executable:
```
chmod +x /path/to/sshfs-automounter.sh
```

Then you need to add it to your startup list:
```
Name: sshfs automounter
Command: sh /path/to/sshfs-automounter.sh
```

(The "sh" might not be needed in xfce's startup manager).

---

