---
title: "Ubuntu, please improve the way mounting works"
date: 2008-05-08
forum: Desktop Environments
---

### Post by ignasigarcia on 2008-05-08
May this post serve to correct me if I'm wrong, or may it serve (I hope so) to ubuntu and gnome to fix this basic issue.

The way ubuntu and gnome treat mount points is so inconsistent that from many applications users don't know how to access those mount points.

**Case 1:**

If I I use gnome *Connect to Server...* to mount a smb folder (so I have the corresponding folder in my Desktop and in computer:///), where's the real mount point so any other non-gtk-gnome application can browse through those contents? 

Instead of having a "virtual device" in the desktop and in computer:/// , wouldn't it be better have a real folder (put any neat icon if you may) where ALL linux applications can access it, even from the shell?


**Case2 :**

Since that *Case 1* is not perfect, many users like me create entries in /etc/fstab with network mount points so I can mount them to folders when needed. This is one of many I have:

```
//192.168.10.1/cavanilles       /media/cavanilles cifs    iocharset=utf8,noauto,user,credentials=/etc/samba/credentials   0 2
```


So, this, in gutsy, will show a smb folder in computer:/// If I double click on it, it will mount it to /media/cavanilles, and a mounted drive will show up in the desktop. ANY application will have access to the contents of that resource since it really is mounted to a folder in /media. See the attached picture of how gutsy does it right.


However, in hardy, that same entry in /etc/fstab will not show up in computer:/// until mounted. So I have to open a terminal and type "mount /media/cavanilles" to show it up and access it.


**Conclusion**

If I were a linux newbie, I would try *Case 1* and would see that for some applications I get access to the network resource, but no for others, and there is no way I can use bash to cd to the network resource. So I'd ask for help, and someone would come and tell me about *Case 2*, that I have to create a mount point in /etc/fstab and in order to access that share in hardy I have to type some command in the terminal because hardy no longer shows those fstab entries in computer:/// as gutsy did. Well, if I were a newbie, and saw this simple/basic operating system inconsistent behavior like this one, I might decide to turn to the dark side again. Luckily, I'm not a newbie...

I hope I'm wrong and some of you may provide a solution for this.

Thanks very much

Ignacio

---

### Post by ignasigarcia on 2008-05-09
Ok, I'm glad that I was wrong! I finally found a way for non gnome-gtl applications to access remote network points, even from the shell. When I mount any application from gnome's Connect to Server... mount points are created in ~/.gvfs/   It's a little hidden, but they're there. I just created a symlink ln-s .gvfs Servers and now anytime I want to access a connected server from any non-gnome application I go there.


Just wanted to share this in case someone else is interested.

---

### Post by bingoUV on 2008-05-09
cool, this is great. I was wondering what this .gvfs is for.

---

