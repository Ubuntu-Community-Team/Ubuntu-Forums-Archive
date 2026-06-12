---
title: "Connecting to ubuntu server running gnome via ssh"
date: 2007-08-30
forum: Desktop Environments
---

### Post by mtime2457 on 2007-08-30
I'm trying to connect to an Ubuntu Server which currently has the GUI installed from a Windows Pro workstation with SSH.  Can someone explain to me how to do this.

---

### Post by f00buntu on 2007-08-30
Make sure sshd is installed and running on the Ubuntu Server ```

dpkg-query -s ssh
```
If not install sshd
```
sudo apt-get install ssh
```
Check if it's running
```
ps aux | grep sshd
```
You should see a sshd process running: /usr/sbin/sshd

Look up the ip of the Ubuntu server ```
ip addr
```

Forward a port in your router if you're using a router and connecting over the internet
Connect to the server with a windows ssh client e.g. [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/")

---

### Post by mtime2457 on 2007-08-30
Thank You!  We apparently deleted ssh when we were testing, I didn't even bother to look.  But when I did, it wasn't install.  Now I just have to figure out what the command is to connect to the server via ssh directly into the GUI.

---

