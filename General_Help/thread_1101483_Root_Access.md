---
title: "Root Access"
date: 2009-03-20
forum: General Help
---

### Post by accooper on 2009-03-20
OK here is a really easy question for you Unbuntu gurus.  How do I give myself root access?

I wish to have complete control over my machine.

Andrew

---

### Post by taurus on 2009-03-20
If you are the first user, then you have root privilege.  So basically, you would have a full control of your machine.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

p.s.  Just be careful when you run a command with sudo because you can trash your machine beyond repair.

---

### Post by Sub101 on 2009-03-20
If you mean to log in as root then I believe that it is against forum policy for us to tell you. A quick Internet search would probably give you the answers anyway.

However running a program as root can be achieved with the sudo command.

[EDIT: It looks like it might actually be allowed to show users to login as root. Thanks fieroboom]

---

### Post by accooper on 2009-03-20
OK, let me tell you what I am trying to do.  First I downloaded a program called pysdm it is suposed to allow me to mount on boot up all my drives.  But when I run it it says "you need root access to run this program".  What do I do here?

Andrew

---

### Post by taurus on 2009-03-20
That program is in the repos.  But if you want to run it, then try

```
gksudo pysdm
```
Use the same password that you log in with.  

If you want to mount your partitions/drives upon boot, just add an entry for each partition/drive in /etc/fstab.

---

### Post by Nano_ext3 on 2009-03-20
The most common way to gain root access as any user is to :
```
sudo su -
```

This will drop you into a root shell.  I have been told this is better way to handle root, not **sudo su**.  You can also put "sudo" in front of any command to run that command as root.  To open your file manager as root do this:
```

sudo nautilus
sudo thunar

```

The first , nautilus is for ubuntu, the second, thunar, is for Xubuntu.  Type which one applies to you, not both.

Hope this helps!

_Nano

---

