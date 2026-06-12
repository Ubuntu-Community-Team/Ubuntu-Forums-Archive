---
title: "managing network shares"
date: 2009-04-07
forum: General Help
---

### Post by mickey13 on 2009-04-07
Hey all,

I have some network shares I set up a while back using gnome.  I'd prefer to manage my network shares from the command prompt now.  Where are network share definitions stored?  Thanks in advance for the help.

Mickey

---

### Post by doas777 on 2009-04-07
well traditionally, samba configuration is stored in the smb.conf.
you can open it with:
```

sudo nano /etc/samba/smb.conf

```
(replace 'nano' with your cli editor of choice)

after you edit the file, be sure to restart samba with:
```
sudo /etc/init.d/samba restart
```

I have had a few problems with samba when I've used the GUI sharing before configuring it by hand. I hope it goes smoothly for you however.

good luck,
franklin

---

### Post by mickey13 on 2009-04-10
I'm actually looking for the file that contains the name of the share that's associated with the shared directory that I created in gnome.  Thanks.

---

