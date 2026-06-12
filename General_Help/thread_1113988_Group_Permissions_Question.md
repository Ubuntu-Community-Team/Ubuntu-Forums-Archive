---
title: "Group Permissions Question"
date: 2009-04-02
forum: General Help
---

### Post by zoomiest on 2009-04-02
Just learning the exact science of permissions... please set me straight.

I have a Samba server running on Ubuntu server 8.10, and I have about 5 users, who I need to have full access to the contents of the directory...

In trying different things, I have now loosened the security to:

```
drwxrwxrwx 19 root team 4096...
```

and users still can't edit files within the directory, nor create files, etc... 

As I write this, I remember that I forgot about Samba... 

1) For every permission change, do I need to implement it in two places? (Samba and server system level)?

2) What is the best-practices permissions plan? (set file system to certain security level, then control the rest/details in Samba? Another plan?)

Thanx in advance.

---

### Post by nateperson on 2009-04-02
I would check the share permissions.  When mixing share and file permission the effective permission is always whatever the least restriction is.

So, even if you have full access file wise, but read only share wise, then your effective is read only.

---

### Post by jigsaws on 2009-04-02
Yes, you need to make in two places until you give full permissions at samba level.

You can think about samba permissions as about maximum permissions - for additional security. Then you can add permissions at filesystem level.

---

### Post by albinootje on 2009-04-02
> **zoomiest said:**
> 
1) For every permission change, do I need to implement it in two places? (Samba and server system level)?


Yes. Here's an example from a smb.conf :

[audio-video]
   comment = Audio and video files
   path = /home/audio-video
   force create mode = 0664
   public = yes
   writable = yes
   printable = no
   force security mode = 0770
   force group = your_group
   force directory mode = 0770

After using this you should use 770 on the directory and subdirectories you already have in use.
The "force user =" option could also be very useful to fix permission problems with Samba.

---

### Post by zoomiest on 2009-04-02
Awesome!
Thank you  - each one!
Where is that button, to signal a valid "thank-you" ?

---

### Post by zoomiest on 2009-04-03
A couple more questions:

1) Does the unix password synch setting in the smb.conf ever become problematic? does is alleviate the need to change two passwords everytime you change a password? (does the feature work?)

---

### Post by albinootje on 2009-04-03
> **zoomiest said:**
> Does the unix password synch setting in the smb.conf ever become problematic? does is alleviate the need to change two passwords everytime you change a password? (does the feature work?)

In the past I've quickly tried to make this work in a Samba+LDAP setup, but I couldn't make it to work back then. It should be possible though.

See here for a start :
[http://jaka.kubje.org/2007/05/14/unix-samba-password-sync-on-debian-etch/](http://jaka.kubje.org/2007/05/14/unix-samba-password-sync-on-debian-etch/)
[http://linuxwindows.org/2008/08/sync-the-linux-system-password-and-the-samba-password.html](http://linuxwindows.org/2008/08/sync-the-linux-system-password-and-the-samba-password.html)

---

