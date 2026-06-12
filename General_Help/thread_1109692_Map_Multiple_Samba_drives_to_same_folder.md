---
title: "Map Multiple Samba drives to same folder"
date: 2009-03-29
forum: General Help
---

### Post by pattersondm85 on 2009-03-29
Hello,

I have two different media servers both have TV shows episodes. I will have them mapped to my Mythtv frontend. I include my /etc/fstab

```
#Jeffs mame box
//192.168.1.127/tv              /mythtv/TV              smbfs  username=guest,password=,uid=1000,iocharset=utf8,unicode  0  0
```

and 
```
#mythtv server
//192.168.1.141/TV              /mythtv/TV              smbfs  username=guest,password=,uid=1000,iocharset=utf8,unicode  0  0
```

When I include both of those in the fstab. Only, the first one is being mapped to my frontend.  Does anyone have any thought as  how to map two different shares on the network to one folder on a computer.

Thanks for any help your able to lend.
Pattersondm85

---

### Post by dcstar on 2009-03-29
> **pattersondm85 said:**
> Hello,

I have two different media servers both have TV shows episodes. I will have them mapped to my Mythtv frontend. I include my /etc/fstab

```
#Jeffs mame box
//192.168.1.127/tv              /mythtv/TV              smbfs  username=guest,password=,uid=1000,iocharset=utf8,unicode  0  0
```

and 
```
#mythtv server
//192.168.1.141/TV              /mythtv/TV              smbfs  username=guest,password=,uid=1000,iocharset=utf8,unicode  0  0
```

When I include both of those in the fstab. Only, the first one is being mapped to my frontend.  Does anyone have any thought as  how to map two different shares on the network to one folder on a computer.

Thanks for any help your able to lend.
Pattersondm85

You cannot have two resources mapped to the same mount point.

---

### Post by pattersondm85 on 2009-03-29
Is there no work around? Because, it is not possible for me to move hundreds of episodes from one computer to the other. So I really would to have them mapped to the same folder. Is it possible if I use NFS rather then samba? 

The folder that has the files mapped doesn't need to have write accesses to the samba share. I just need read and rights.

Any suggestions is much apprechated.

---

