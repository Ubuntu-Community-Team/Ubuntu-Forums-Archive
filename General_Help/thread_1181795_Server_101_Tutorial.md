---
title: "Server 101 Tutorial"
date: 2009-06-08
forum: General Help
---

### Post by 2quick on 2009-06-08
Hello!

I am currently trying to set up a server for myself and some guys in my current location.  I currently have very limited internet access and need to find some information.

I am new(never done it before) to Linux servers.  I have downloaded and installed Ubuntu Server 9.04 on a laptop.  Now I need a basic walk through on how to set up all the services I need to set up.  If I could be pointed in something that comes in a .pdf that would be even better.  I do have the Ubuntu Server guide from here.  I am looking for maybe something even more basic.

First a basic question, for file sharing using Samba I should have the server connected to a switch/router, then all of the computers hooked up the the switch/router.  The ethernet cable for the server should be going to the internet connection in the router.  Is this the correct physical set up?

Second I am looking to set up a shared external hard drive across the network and use the server as a Quality or Service device to limit bandwidth usage for users on the network.

So am I correct in thinking I should be using Apache as a web server and Samba as the file server.  I have some software from TES that can do the QoS job, but it is limited to 16 users and I am looking at 45 people.

Summed up I am deployed to Afghanistan and going to get a satellite for internet service and I want to make sure that everyone gets their fair bit of the bandwidth.  Any help is MUCH appreciated :)

Thanks guys!

---

### Post by Villiam on 2009-06-08
You may like to check this pdf out: [https://help.ubuntu.com/6.06/pdf/ubuntu/C/serverguide.pdf](https://help.ubuntu.com/6.06/pdf/ubuntu/C/serverguide.pdf)

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by 2quick on 2009-06-08
> **Villiam said:**
> You may like to check this pdf out: [https://help.ubuntu.com/6.06/pdf/ubuntu/C/serverguide.pdf](https://help.ubuntu.com/6.06/pdf/ubuntu/C/serverguide.pdf)

Thanks for the reply, but that what I have read and was trying to get a little bit more information.  I have almost no knowledge of how to get this all set up and running..:)

---

### Post by Iowan on 2009-06-08
> **2quick said:**
> First a basic question, for file sharing using Samba I should have the server connected to a switch/router, then all of the computers hooked up the the switch/router.  The ethernet cable for the server should be going to the internet connection in the router.  Is this the correct physical set up?I would probably put the server and all computers on the same side of the router/switch, and save the internet connection for the satellite connection.

On the other hand, if the server is gonna be regulating bandwidth, it will probably need to be inline (which may require two NIC's).

---

### Post by 2quick on 2009-06-09
> **Iowan said:**
> I would probably put the server and all computers on the same side of the router/switch, and save the internet connection for the satellite connection.

On the other hand, if the server is gonna be regulating bandwidth, it will probably need to be inline (which may require two NIC's).

If I use the TES software it does require 2 NIC's, and I am sure it will be the same way with any QoS setup.  Thanks for the input.

Is there any other software that anyone knows of for QoS?

Thanks!

---

