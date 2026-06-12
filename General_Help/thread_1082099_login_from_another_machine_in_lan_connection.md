---
title: "login from another machine in lan connection"
date: 2009-02-27
forum: General Help
---

### Post by krishna1650 on 2009-02-27
i have ubuntu on my machine. i have samba working. now i want to log in to the machine from other win xp machines which are connected by lan connection. 
help needed.

---

### Post by smani on 2009-02-27
You first need to create some shares (right click on a folder -> sharing options), then from windows you should be able to access to the ubuntu box via \\name\share_name or \\ipaddress\share_name - this will allow you to browse the files of the ubuntu box remotely.

---

### Post by krishna1650 on 2009-02-27
> **smani said:**
> You first need to create some shares (right click on a folder -> sharing options), then from windows you should be able to access to the ubuntu box via \\name\share_name or \\ipaddress\share_name - this will allow you to browse the files of the ubuntu box remotely.

i want to know how to log in, not to access the shared files.

---

### Post by smani on 2009-02-27
In that case you it is not samba you need. You should specify more what you mean by logging in: if you want to see the desktop through a virtual screen, have a look at remote desktop (system->preferences->remote desktop). You can then use a program such as vncviewer ([www.realvnc.com](www.realvnc.com)) to connect to the pc. There are also console based approaches such as ssh.

---

### Post by Peter09 on 2009-02-27
You need to understand what you want to do. VNC requires you to have already logged in to the remote machine before you can see the desktop. SSH and packages like NXFree will allow access to a machine with no one already logged in (no existing desktop)

---

### Post by krishna1650 on 2009-02-27
> **smani said:**
> In that case you it is not samba you need. You should specify more what you mean by logging in: if you want to see the desktop through a virtual screen, have a look at remote desktop (system->preferences->remote desktop). You can then use a program such as vncviewer ([www.realvnc.com](www.realvnc.com)) to connect to the pc. There are also console based approaches such as ssh.

yes i want ssh. how to set up ssh and enable remote login ?
thanks for help.

---

### Post by NTolerance on 2009-02-27
> **krishna1650 said:**
> yes i want ssh. how to set up ssh and enable remote login ?
thanks for help.

Install SSH server:
```
sudo apt-get install ssh
```

Download the [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/) SSH client for Windows.  Put in the IP address of your Ubuntu machine into PuTTY and you're all set.

---

### Post by Peter09 on 2009-02-27
First on the server you need to install openssh-server

```
sudo apt-get install openssh-server
```

Once done you should be able to remotely login 

```
ssh -X <username>@<server> xterm
```

the above command will give you an xterm on the server

```
ssh -X <username>@<server> nautilus
```

will run nautilus on the remote machine.

---

