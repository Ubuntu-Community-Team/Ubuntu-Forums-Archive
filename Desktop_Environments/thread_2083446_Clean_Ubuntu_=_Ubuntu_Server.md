---
title: "Clean Ubuntu = Ubuntu Server?"
date: 2012-11-12
forum: Desktop Environments
---

### Post by tschinz on 2012-11-12
Hello Guys,

I need a clean ubuntu installation but I don't want Unity or so much other crap delivered with the Ubuntu installation. 

I'm a Gnome user but there is unfortunately no real supported Gnome Ubuntu installation. 

So I was wondering if I can use the Server installation to have a clean simple lightweight ubuntu and then install my Graphical user interface to it. 

Is there any drawback to the ubuntu server installation, what is specially included there?

Thanks for your opinions and informations

---

### Post by Cheesemill on 2012-11-12
Yes you can do this. Instead of using the Server CD I tend to use the Mini CD instead to install a command line system. The only difference is the Mini CD downloads all of the packages it installs from the internet so your system is up to date from the moment it is installed. You end up with a minimal CLI installation no matter which CD you use though.

[http://cdimage.ubuntu.com/netboot/](http://cdimage.ubuntu.com/netboot/)

---

### Post by tschinz on 2012-11-12
That's great news. And thanks for the hint about the Mini CD, I'm always annoyed that you have to install X updates after a "fresh" installation. It feels like windows updates ;-)

Are there any problems installing Gnome onto it? I guess X server is also not included.

Are there any special features in the Server edition?

---

### Post by papibe on 2012-11-12
> **Cheesemill said:**
> I tend to use the Mini CD

+1. Here is the [link]("https://help.ubuntu.com/community/Installation/MinimalCD") to the minimal install CDs.

If you choose a command line install using the minimal CD, you would have a bare bones installation, and no GUI.

You can add any desktop environment later using either apt-get or tasksel. Here's an [example]("http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24").

Regards.

---

### Post by papibe on 2012-11-12
> **tschinz said:**
> Are there any special features in the Server edition?
The server installation will offer more options (e.g.,cluster cloud) and server meta packages like LAMP, Samba, NFS server, etc.

It is also a viable option to do it with the server CD.

Regards.

---

### Post by tschinz on 2012-11-12
I would need Samba and NFS anyway so Server installation will be my choice. 

Also thanks for the installing howto link.

Thanks for the fast replies and the infos you guys rock

---

