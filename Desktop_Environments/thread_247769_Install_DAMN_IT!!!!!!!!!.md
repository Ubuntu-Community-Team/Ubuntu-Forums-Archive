---
title: "Install DAMN IT!!!!!!!!!"
date: 2006-08-31
forum: Desktop Environments
---

### Post by tux dude on 2006-08-31
Each time i try 2 install programs it come sup with a msg saying that there is no such file or directory!
PLZ HELP ME (sum screen shots soon)

---

### Post by hajk on 2006-08-31
Not using Synaptic? Universe/multiverse repositories enabled?

N.B. Don't shout, please.

---

### Post by tux dude on 2006-08-31
i dunno wat ur talking bout.plz explain

---

### Post by amo-ej1 on 2006-08-31
describe your problem, explain what steps you take and what the result of those steps is (and what the expected result is).

---

### Post by Dramist on 2006-08-31
yes i am also new to linux (sorry for the asumption) and i dont know about any of this, i see people doing all this stuff sudo blah blah what does it mean and how do you use it lol

---

### Post by amo-ej1 on 2006-08-31
The sudo part is easy. Withing linux (and unix) you have the concept of multiple users. You log in as a normal user which has limited abilities on the system. He can't install programs, he (or she) can't erase the harddisk, ... there is a different user (called 'root') which has all these privileges. It's dangerous to run a system as root since many people have damaged their installation by doing so, running rm -rf / as root, by accident will erase your harddrive running rm -rf / as a normal user will give you a lot of warnings because you have no permission to do so.

Thus the solution is 'su' or 'sudo' these commands allow you to temporary elevate your permissions. So 'sudo bla bluh' will run the 'bla' command with parameters 'bluh' as a root user. Which users have the privilige to do this is defined in the file /etc/sudoers . So 'sudo apt-get install gaim' will run the command 'apt-get' with parameters 'install gaim' as a root user. Runnin this without sudo will give you an error on permissions. And apt-get install gaim will download gaim and install it (including the dependencies).

that's it ;)

---

### Post by tux dude on 2006-08-31
well,i click on the install icon and it ses that there is no such file or directory.Im using xp at the moment Hold on and ill boot up my Linux BOx and get sum screens...:o

---

### Post by tux dude on 2006-08-31
!TEST!
[IMG]E:/My desktop.png[/IMG]

---

### Post by tux dude on 2006-08-31
[E:\My desktop.png]("E:\My desktop.png")

---

### Post by tux dude on 2006-08-31
How do u input images!

---

### Post by Tamihania on 2006-08-31
> **tux dude said:**
> How do u input images!

You have to upload them to the net - fi. imageshack.com, fotki.com, Flickr...
You can link your uploaded picture to here then...

I hope it will help.

tami

---

