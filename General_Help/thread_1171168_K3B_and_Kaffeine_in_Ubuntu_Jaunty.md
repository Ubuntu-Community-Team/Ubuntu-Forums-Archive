---
title: "K3B and Kaffeine in Ubuntu Jaunty"
date: 2009-05-27
forum: General Help
---

### Post by olympic on 2009-05-27
Can someone advise if K3B and Kaffeine are compatible with Ubuntu Jaunty.  I have Brasero and Totem installed and both are working, but neither K3B or Kaffeine will start.  I notice some threads about these two apps when used with earlier versions (Feisty) but not with Jaunty.

---

### Post by Yellow Pasque on 2009-05-27
I am using K3B with Ubuntu Jaunty. Start the programs from the terminal and see what errors they give.

---

### Post by olympic on 2009-05-27
Hi,
This is the response.

[I]frankhr@Ubuntu9:~$ k3b
trying to create local folder /home/frankhr/.kde/share: Permission denied
trying to create local folder /home/frankhr/.kde/share: Permission denied
trying to create local folder /home/frankhr/.kde/share: Permission denied
trying to create local folder /home/frankhr/.kde/tmp-Ubuntu9: Permission denied
trying to create local folder /home/frankhr/.kde/share: Permission denied
trying to create local folder /home/frankhr/.kde/share: Permission denied
trying to create local folder /home/frankhr/.kde/share: Permission denied
trying to create local folder /home/frankhr/.kde/share: Permission denied
trying to create local folder /home/frankhr/.kde/share: Permission denied
trying to create local folder /home/frankhr/.kde/socket-Ubuntu9: Permission denied
trying to create local folder /home/frankhr/.kde/socket-Ubuntu9: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/frankhr/.kde/socket-Ubuntu9/kdeinit__0'
frankhr@Ubuntu9:~$ [/I]

---

### Post by Yellow Pasque on 2009-05-27
```
sudo chown -R frankhr:frankhr ~/.kde
```

---

### Post by olympic on 2009-05-27
Marvellous - thank you

Both k3b and kaffeine are now working.:p

---

