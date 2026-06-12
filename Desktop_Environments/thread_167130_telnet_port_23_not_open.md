---
title: "telnet port 23 not open?"
date: 2006-04-27
forum: Desktop Environments
---

### Post by rocarm on 2006-04-27
I tried to telnet in and i couldn't. is there anyway to start telnet?
Do i have to apt-get something?

---

### Post by cgjones on 2006-04-27
Unless you have a very specific reason to be using telnet, you should look into SSH. It does the same as telnet and more and is secure.

---

### Post by rocarm on 2006-04-27
[QUOTE=rocarm]I tried to telnet in and i couldn't. is there anyway to start telnet?
Do i have to apt-get something?[/QUOTE]

ok, same thing, do i need to downloading something for ssh? or is it integrated.. the reason i ask, i've installed two different versions of stuff before and broke my install (apache, apach2 & firefox and mozilla firefox) etc. etc. 

thanks

---

### Post by cgjones on 2006-04-27
Ubuntu comes with the OpenSSH client, which allows you to log into computers running the OpenSSH server. To install the OpenSSH server so you can log into your own computer, open Synaptic and do a search for OpenSSH server. Mark it for installation and then click Apply. If you are doing this on the command line, type the following:
```

sudo apt-get install openssh-server

```
Once this is done, check out the man page for ssh to learn how to use it.
```

man ssh

```

---

### Post by rocarm on 2006-04-27
thanks

---

### Post by jazzmuzik on 2006-04-27
As cgjones was saying, use ssh instead of telnet:

ssh -2 username@192.168.99.4

where 192.168.99.4 is the address of the remote computer and username is the user account on the remote computer.

ssh is installed by default and it is for connecting to remote computers. The remote computer needs to be running the daemonized version of ssh. So if you want people to connect to your computer via ssh, install the server package, otherwise you can connect out with just ssh.

---

### Post by cgjones on 2006-04-27
Glad I could help.

---

