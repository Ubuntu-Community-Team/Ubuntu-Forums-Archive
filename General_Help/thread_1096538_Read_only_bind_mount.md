---
title: "Read only bind mount?"
date: 2009-03-15
forum: General Help
---

### Post by ownaginatious on 2009-03-15
I'm currently trying to set up vsftpd and need to give users access to folders by mounting said folders as read only within their home directories. The problem I'm having is that I don't know how to mount a folder using a bind mount as read only.

Here is what I need to make read only in the fstab:

Can anyone tell me how to make that "read-only"?

```
/media/windows1/Server_Core_Folder/FTP_Services /home/anon	none	bind	0	0
```

Any help would be greatly appreciated. 

Thanks!

---

### Post by dcstar on 2009-03-15
> **ownaginatious said:**
> I'm currently trying to set up vsftpd and need to give users access to folders by mounting said folders as read only within their home directories. The problem I'm having is that I don't know how to mount a folder using a bind mount as read only.

Here is what I need to make read only in the fstab:

Can anyone tell me how to make that "read-only"?

```
/media/windows1/Server_Core_Folder/FTP_Services /home/anon	none	bind	0	0
```

Any help would be greatly appreciated. 

Thanks!

From "man mount":

```
Note that the filesystem mount options will remain the same as those on the  original  mount  point,  and  cannot  be changed by passing the -o option along with --bind/--rbind.
```

---

### Post by ownaginatious on 2009-03-15
Aw crap... how do I get around this problem then? I find it really damn frustrating that some things which are practically common sense in windows are next to impossible in Ubuntu... and vice versa ;).

I guess that would change my question to, 

How do I allow write access to some of the users on vsftpd while disallowing it for others? I find it incredibly stupid that the only option I'm presented with is to have it on for all users or off for all users.

---

### Post by kevmitch on 2009-04-01
That man page is out of date as of 2.6.26 (Intrepid has 2.6.27). You can now create a 
[read only bind mount]("http://kernelnewbies.org/Linux_2_6_26#head-84b0b94f54cc4be3dd955b16a41cab633d11645b")

Alternatively you can use the bindfs package which is a user space alternative which should work for older kernels.

---

