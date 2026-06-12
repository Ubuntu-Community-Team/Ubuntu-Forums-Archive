---
title: "Can't seem to get sshfs to mount on bootup"
date: 2009-01-05
forum: General Help
---

### Post by jerome1232 on 2009-01-05
I can't seem to figure out how to get a sshfs share to mount automatically. I had this working before with nfs (different beasts I know) but I've decided I want sshfs now since I will be wanting to work with these shares over the internet on occasion. sshfs is secure and encrypted while nfs isn't.

I can mount it fine from the command line with the following command so I know everything is functioning correctly, I have a ssh key for this server that is unlocked on login.

This mounts the share and doesn't prompt me for a password since the key is already unlocked.
```
$ sshfs tss@192.168.1.4:/mnt/torrents /media/torrents
```

This is my line in fstab.
```
# sshfs on tss
sshfs#tss@192.168.1.3:/mnt/torrents /media/torrents fuse defaults,reconnect 0 0
```
The share doesn't get mounted at boot time and when I run "sudo mount -a" it prompts me for a password (for ssh, not to unlock the ssh key) I'm guessing since root is running the process.

So is there a way to point the sshfs command to my key (@/home/jeremy/.ssh/id_rsa) and tell it to use that for authentication? I can't seem to find anything in the man pages of sshfs.

Am I better off just slapping the command to mount in "sessions" to be ran when I log in?

---

### Post by Iowan on 2009-01-05
I found [this]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/") How-To as a link in [this]("http://ubuntuforums.org/showthread.php?&t=283131") thread (also a How-To).
Unfortunately, it doesn't say much about auto mounting.

---

### Post by lswb on 2009-01-05
sshfs uses fuse - "filesystem in userspace" rather than mounting through the kernel. If you just need automount for a user at login, you could write a script with the sshfs commands and put it in gnome sessions  or in .profile, which BTW is sourced during gui login. I have not tried this myself so there may be some caveats but seems like it would be easy to get working.

If you need to automount for the entire system, I don't know... maybe you could create a limited priviledge user similar to what some ftp servers do, then use something like

su username -C sshfs [email]user@blah.blah[/email]:blah mountpoint

in /etc/rc.local

Might try a google search, seems likely someone has already done this

---

### Post by bodhi.zazen on 2009-01-05
There is a nice write up here :

[http://ubuntuforums.org/showthread.php?t=430312](http://ubuntuforums.org/showthread.php?t=430312)

nice explanations too :)

---

### Post by jerome1232 on 2009-01-06
That how-to bohdi.zazen linked seems excellent, don't have time to try it right now though, currently just tossed the mount command into the sessions gui thing so that it auto mounts when I log in. 

Which is fine unless my wifi drops, then any app that was using the sshfs connection hangs hard.

The couple of threads I found by searching were all dead-ends, I think I can definitely get it running with these links. 

--Thanks to everybody.

---

