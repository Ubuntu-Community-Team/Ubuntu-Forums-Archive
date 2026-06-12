---
title: "Windows / Ubuntu File Sharing"
date: 2006-03-17
forum: Desktop Environments
---

### Post by bluemike807 on 2006-03-17
Hello, I installed Breezy for the first time and Im having a bit of trouble finding my way around shared directories.

I've set up samba... sortof. 
From windows I can see the hostname of my Ubuntu machine, but if I try to access it, Im prompted for a username and password. I've tried entering what should be the right user/pass but it just fails.

One thing it seems to do is, immediately after I enter the user/pass is change the username to <windowshostname>/<myusername> which could very well be why its having problems.

Also, how can I get the reverse? map shared directories on my windows machine to my Ubuntu box?
I've followed the wiki on setting up Samba ([https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29))

But sudo apt-get install smbfs, doesnt work, it says it is referred to by another package and is not present.

Help?

---

### Post by frodon on 2006-03-17
Could you post the terminal output you get with the "sudo apt-get install smbfs" and your /etc/apt/sources.list file ? Maybe you didn't set the repository where smbfs is

---

### Post by Jason_25 on 2006-03-17
1.  Check  [ this ]("http://www.ubuntuforums.org/showthread.php?t=122837") thread, especially page two where I post my smb.conf.

2.  Is places > network servers not working for you?

---

### Post by bluemike807 on 2006-03-17
"sudo apt-get install smbfs"  yields:
Reading package lists... Done
Building dependency tree... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package smbfs has no installation candidate

And the sources uncommented are:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

---

### Post by bluemike807 on 2006-03-17
[QUOTE=Jason_25]1.  Check  [ this ]("http://www.ubuntuforums.org/showthread.php?t=122837") thread, especially page two where I post my smb.conf.

2.  Is places > network servers not working for you?[/QUOTE]

I checked out that thread, even got your .conf file but I didnt want to put in something I didnt wholly understand, especially given that I wasnt sure how it would impact my systems.

and no, network servers isnt working - it can *see* the windows folders, but I get a user/pass prompt which likewise doesnt work...

---

### Post by Jason_25 on 2006-03-17
Ok my XP pc at home is setup with simple file sharing.  That means no username or passwords.  I suggest you start with that before you work your way into passwords and such.  That smb.conf is setup for simple sharing just like xp's.  Just change my name to the name of the directory (your home) that you would like to share.

To restart the samba service
```

sudo /etc/init.d/samba restart

```

---

### Post by frodon on 2006-03-17
[QUOTE=bluemike807]"sudo apt-get install smbfs"  yields:
Reading package lists... Done
Building dependency tree... Done
Package smbfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package smbfs has no installation candidate

And the sources uncommented are:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted[/QUOTE]Ok, read this thread and add the missing repositories, it should solve this problem : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

