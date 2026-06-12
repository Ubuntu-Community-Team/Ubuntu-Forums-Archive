---
title: "Samba on a base installation"
date: 2006-01-02
forum: General Help
---

### Post by Jammy_Stuff on 2006-01-02
I have an old PC set up with a base (server) installation and I'm planning to use it as a file server (for Windows PCs). What packages do I need to install and how do I configure it all?

---

### Post by lutrafobic on 2006-01-02
You need samba. (the client is included but not the server)

Install it by using this command:
```
sudo apt-get install samba
```

then you have to make your configuration. Open the configuration file with this command:
```
sudo nano /etc/samba/smb.conf 
```
(When written the file done, you use    CTRL-X   Y    Enter, to quit and save the file)

..and here is a page with instructions about how to setup the configuration-file:

[http://us1.samba.org/samba/docs/man/Samba-Guide/simple.html](http://us1.samba.org/samba/docs/man/Samba-Guide/simple.html)

---

