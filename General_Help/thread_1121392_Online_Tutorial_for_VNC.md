---
title: "Online Tutorial for VNC?"
date: 2009-04-10
forum: General Help
---

### Post by crazypeppo on 2009-04-10
Are there any good novice tutorials for using VNC? Exactly what apps are needed and step by step instructions?

---

### Post by HermanAB on 2009-04-10
VNC is primarily a Windows thing.  SSH is better on Linux, so install the package called ssh-server.  SSH can do everything (and much more) VNC does over an encrypted link.

---

### Post by x C0MMAND0 x on 2009-04-10
I wouldn't say it's primarily a windows thing.  I use VNC to connect to my girlfriends mac all the time, and I use VNC from my office to connect to Windows servers for clients.

---

### Post by adult swim on 2009-04-10
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by dhughes on 2009-04-10
> **crazypeppo said:**
> Are there any good novice tutorials for using VNC? Exactly what apps are needed and step by step instructions?


[http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php](http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php)


 Obviously VNC has to be set up on each computer, the one you're using and the one you want to "view", after that just open a browser and type in the IP of the other computer you want to access and put 5900 at the end e.g. 192.168.1.101:5900 (also open up port 5900 on your router..see port forward.com for that) then enter the password you choose when setting up VNC on the other computer.

---

### Post by crazypeppo on 2009-04-11
Thanks for all the info... I have been playing around with vnc and open ssh-server and putty-tools a little. I am at school and want to access my linux computer from the schools windows computers. I also was playing around with trying to securely connect to my 64 yr old mothers ubuntu computer! YEah for her she's been using for almost a year.
I found a tutorial under the "how to" section here in the forums. I am just not familiar with all the protocols and differnet ways of remote connecting.

Thanks again for all your help, I will continue to read more about ssh and such.

---

