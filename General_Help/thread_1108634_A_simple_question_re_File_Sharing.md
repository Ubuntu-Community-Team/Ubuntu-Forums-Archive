---
title: "A simple question re: File Sharing"
date: 2009-03-27
forum: General Help
---

### Post by ozguitarplayer on 2009-03-27
I think I've dug myself into a hole with file sharing.
I have two computers both with Hardy Heron and I need to set up file sharing and I'm finding it not as easy as it's supposed to be.

So hopefully a simple question; is Samba needed for file sharing between two Ubuntu computers?

---

### Post by bigbencg on 2009-03-27
Samba is not needed but could be used.  Linux uses NFS (Network File System) to share files between computers.  There might be a graphical utility to set up an NFS share, you would have to research it.  I do it through command line.  NFS is nice because it is stateless, if you are transferring files between computers and one is turned off, the other will wait for the connection to be restored and continue as if nothing happened.

If you wish to learn the command line process, let me know.

---

### Post by bigbencg on 2009-03-27
I found a guide that can help you with NFS should you choose to learn it.

[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

Otherwise samba would work if security is not a huge issue.

---

### Post by ozguitarplayer on 2009-03-27
thanks bigbencg,
does this mean that if I don't use Samba then NFS will be used by default or does it need to be installed..I had the feeling that using NFS is all to do with using terminal, which I's too new and slow at to be of use, so I need at first the simplest method possible at first..

---

### Post by mb_webguy on 2009-03-28
NFS does have its advantages, but Samba is much easier to set up, as it's built in to Ubuntu.  All you have to do is right-click on any folder and select Sharing Options.  Set the sharing options you want, such as the share name of the folder and access rights, then click Create Share.  If this is the first time you've done this, you will be asked if you want to install Samba.  If you say yes, Samba will be installed for you.  Unfortunately, since Samba wasn't installed, you'll need to now go back and set the sharing options on the folder again for them to take effect.

---

### Post by ozguitarplayer on 2009-03-28
thanks mb_ewbguy,
so I need either Samba or NFS...I'm not up for NFS yet....I have tried Samba and can only get it to work from pc1 - pc2 and cannot connect ps2 - pc1 when I try I get a request for user name and password and my user name and password don't work..pc1 isn't allowing access from pc2...
.so that started me thinking maybe Samba is causing problems and maybe I can get on without it however I can't so I'll keep fiddeling.....

---

### Post by mhgsys on 2009-03-28
> 
have tried Samba and can only get it to work from pc1 - pc2 and cannot connect ps2 - pc1 when I try I get a request for user name and password and my user name and password don't work..pc1 isn't allowing access from pc2...


```

sudo nano /etc/samba/smb.conf

```

first, make sure there on the same workgroup.
then:
in Section Authentification
remove the ; to enable

```
 security = share 
```

in Section Authentification.
remove the ; to enable
```


 guest account = nobody

```

---

