---
title: "Alternative to gnome-vfs sftp virtual mounting?"
date: 2006-01-04
forum: Desktop Environments
---

### Post by David Olivier on 2006-01-04
It seems that when I mount (with the "connect to server" tool) a remote volume via sftp, it is not really mounted from the system point of view. It doesn't appear when I type the df command, for instance. The files appear in the file browser (Nautilus) but  this seems to be a kind of private abstraction. For instance, I can't open these files in Firefox. After looking around it seems linked to an abstraction called gnome-vfs.

I'm not sure I like this very much! (I suppose there are reasons for it to be done this way, but as it is I don't grasp them.)

Is there an alternative, that might allow me to *really* mount a remote file system via sftp? Or via nfs, that would do too.

The same question applies for Windows volumes, apparently, that are "mounted" through smb.

---

### Post by David Olivier on 2006-01-04
I found the answer all by myself! :cool: 

The answer is called sshfs. It's documented on:

[http://fuse.sourceforge.net/sshfs.html]("http://fuse.sourceforge.net/sshfs.html")

On that page it says you first have to install fuse. I don't know what that is, but it all got installed seamlessly when I asked the Synaptic package manager to install sshfs.

After completing the installation, when I tried to mount a distant volume by following the instructions on the Web page:

```

$ # Making the mount point:
$ sudo mkdir -p /Volumes/mountpoint
$ sudo chown me:me /Volumes/mountpoint
$
$ # And then mounting:
$ sshfs me@hostname: /Volumes/mountpoint

```

 at first it didn't work, complaining:

```
fuse: failed to exec fusermount: Permission denied
```

I was, as recommended, running sshfs under my user account, and the fusermount executable mentioned in the error message (/usr/bin/fusermount) was in effect not executable by ordinary users.

I fixed the problem by changing the permissions on the fuseraccount executable:

```
sudo chmod o+x /usr/bin/fusermount
```

After that it worked perfectly.

The mounted volumes don't appear on the desktop or in the Nautilus "Places" left panel. That's a bit unexpected for someone used to the Macintosh or Windows model, but it seems quite normal in fact, since once mounted the volumes are just part of the same tree. They can be accessed in the file browser just by navigating to them.

---

### Post by Suger on 2006-01-04
Yes, I love sshfs.

For samba, you have smbmount (must be the smbfs package in synaptic) which gives nice results to.

---

### Post by sciurus on 2006-01-04
[QUOTE=David Olivier]
After completing the installation, when I tried to mount a distant volume by following the instructions on the Web page:

```
fuse: failed to exec fusermount: Permission denied
```

I was, as recommended, running sshfs under my user account, and the fusermount executable mentioned in the error message (/usr/bin/fusermount) was in effect not executable by ordinary users.

I fixed the problem by changing the permissions on the fuseraccount executable:

```
sudo chmod o+x /usr/bin/fusermount
```

After that it worked perfectly.
[/QUOTE]

The recommended solution is to add yourself to the 'fuse' group. See step 3 [here]("http://www.ubuntuforums.org/showthread.php?t=103860"): ```
sudo adduser your-username fuse
```, then log out and log back in.

---

### Post by David Olivier on 2006-01-07
[QUOTE=Suger]Yes, I love sshfs.

For samba, you have smbmount (must be the smbfs package in synaptic) which gives nice results to.[/QUOTE]

Thanks. I'll try that when I get back to work on Monday.

---

### Post by David Olivier on 2006-01-08
[QUOTE=sciurus]The recommended solution is to add yourself to the 'fuse' group. See step 3 [here]("http://www.ubuntuforums.org/showthread.php?t=103860"): ```
sudo adduser your-username fuse
```, then log out and log back in.[/QUOTE]

Thanks. I hadn't seen that thread, it has all the answers.

David

---

