---
title: "others can't ssh to my IP"
date: 2006-01-04
forum: General Help
---

### Post by jackuto on 2006-01-04
hi all, i have a question about ssh, as far as i know that ssh in my newly install ubuntu 5.10 are working well for me to enter any linux base PC at my office, but somehow others PC can't ssh into my newly install ubuntu 5.10. 

i wonder what am i missing for my ssh settings, could anybody give a hand pls? thanks in advance!

---

### Post by DaMasta on 2006-01-04
You have the server running? You have the port open? You have them as a user? Lots of possibilites as you can see.

---

### Post by monkblah on 2006-01-04
1) can you ssh into your own PC, from your own PC?

2) if you run ssh verbosly (eg ssh -vvv -l my_login 128.34.33.12), it will print out a bunch of debugging messages that might help.

---

### Post by sabitha on 2006-01-04
[QUOTE=jackuto]hi all, i have a question about ssh, as far as i know that ssh in my newly install ubuntu 5.10 are working well for me to enter any linux base PC at my office, but somehow others PC can't ssh into my newly install ubuntu 5.10. 

i wonder what am i missing for my ssh settings, could anybody give a hand pls? thanks in advance![/QUOTE]
have you installed ssh on your newly install ubuntu if you already do that try restart the ssh service
code :
sudo /etc/init.d/ssh start

---

### Post by jackuto on 2006-01-04
hi all! i've try the command ssh -vvv -l my_login [my ip]\

heres the return message showed at the prompt:
OpenSSH_4.1p1 Debian-7ubuntu4, OpenSSL 0.9.7g 11 Apr 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.203 [my ip] port 22.
debug1: connect to address [my ip] port 22: Connection refused
ssh: connect to host [my ip] port 22: Connection refused

i've checked that in my /etc/ssh/ has only 2 files: moduli and ssh_config. 
while my other colleagues are using gentoo, i search out their ssh folder and have plenty setting files inside... 

can i know the proper general procedures to setup ssh so that their gentoo can ssh into my ubuntu 5.10?:confused:

---

### Post by piedamaro on 2006-01-04
It seems you are missing the server; it should be an sshd_config file under /etc/ssh
Try sudo apt-get install openssh-server.

---

### Post by Tal on 2006-01-04
[QUOTE=piedamaro]It seems you are missing the server; it should be an sshd_config file under /etc/ssh
Try sudo apt-get install openssh-server.[/QUOTE]

Bingo. This one took me a sec after installing Ubuntu for the first time as well.

---

