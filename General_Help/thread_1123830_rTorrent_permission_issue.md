---
title: "rTorrent permission issue"
date: 2009-04-12
forum: General Help
---

### Post by mocka on 2009-04-12
Recently I installed rTorrent together with wTorrent.

Now I'm having a permission problem. Whenever I try to add files or folders to the folders rTorrent use, I'm rejected by the server. I tried to figure out a workaround for this so I tried to copy a finished torrent file to another directory on the computer, this, however, only results with rTorrent being incapable of hashing the torrent, because of lacking permissions.

How do I fix this so I can be able to add and remove folders freely within the rTorrent directories and to be able to use rTorrent for directories outside its own?

---

### Post by taurus on 2009-04-12
Do you have permissions to write to whatever directory you have rtorrent save to?

---

### Post by mocka on 2009-04-13
I think I don't. As I'm very new to Ubuntu Server, I do not know how to manage permissions.

EDIT: Recently I read up a bit on how to change permissions on folders, so I tried the following command on the rTorrent folder:

chmod -R 755 /home/rt/torrents/done

This did not work. This is the output i received:
```

mocka@Hubuntuserver:~$ chmod -R 755 /home/rt/torrents/done
chmod: changing permissions of `/home/rt/torrents/done': Operation not permitted

```

---

### Post by AnjinSan on 2009-04-16
> **mocka said:**
> 
mocka@Hubuntuserver:~$ chmod -R 755 /home/rt/torrents/done
chmod: changing permissions of `/home/rt/torrents/done': Operation not permitted

You have to set it with sudo chmod -R 755 /home/rt/torrents/done. And if 755 dont work try 777.

---

### Post by mocka on 2009-04-17
I did it with the root account, then there was no hassle. Anyway, I've seen many say that chmod 777 should be avoided - why?

I've already tried with the chmod 755 and 775 but rTorrent won't hash the files unless I chmod 777.

---

### Post by mocka on 2009-04-17
I did it with the root account, then there was no hassle. Anyway, I've seen many say that chmod 777 should be avoided - why?

I've already tried with the chmod 755 and 775 but rTorrent won't hash the files unless I chmod 777.

---

### Post by AnjinSan on 2009-04-17
777 is avoided for other permissions i though, nothing can happen if u put permissions 777 for your whole torrent partition, and you did not need to make root account, you are the root, but most commands are runned under user. So to execute a command as root you must put sudo in front of the command.

---

