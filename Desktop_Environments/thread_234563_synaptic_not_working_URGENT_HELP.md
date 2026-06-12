---
title: "synaptic not working URGENT HELP"
date: 2006-08-11
forum: Desktop Environments
---

### Post by stop_that on 2006-08-11
when i click on it or try to install updates it says this

> E: ERROR: could not create configuration directory /root/.synaptic - mkdir (2 No such file or directory)

erm what should i do.. i need to install make HELP](*,)

---

### Post by llamakc on 2006-08-11
Run Synaptic as a user instead:

sudo synaptic

and not as root.

---

### Post by stop_that on 2006-08-11
nope still error message

---

### Post by llamakc on 2006-08-11
Run it from a Terminal and show us the error message again, please.

Are you root? Are you in the /root directory?

Do this as a user:

cd && sudo synaptic

---

### Post by stop_that on 2006-08-11
i do it as user NOT root user and a window pops up saying

> E: ERROR: could not create configuration directory /root/.synaptic - mkdir (2 No such file or directory)

---

### Post by llamakc on 2006-08-11
Once more, please run this from a Terminal and post THAT error message.

---

### Post by stop_that on 2006-08-11
it have ran it in terminal look

[IMG]http://img141.imageshack.us/img141/7404/screenshot1wb5.png[/IMG]

then enter pass and press enter and this pops up !

[IMG]http://img45.imageshack.us/img45/2329/screenshot2hr9.png[/IMG]

---

### Post by llamakc on 2006-08-11
Here's what mine looks like:

drwx------  3 root root 4.0K 2006-07-27 08:00 .synaptic

So do this:

sudo mkdir /root/.synaptic

sudo chmod 700 /root/.synaptic

And try running synaptic again. 

Have you toyed with system permissions at all in the past? Weird that you're having this problem. . . .

---

### Post by vijirajan on 2006-08-11
It looks like the home directory for user root is not set properly. I mean /root doesn't exist.

---

### Post by stop_that on 2006-08-11
i did previously work ](*,) 

i tried sudo mkdir /root/.synaptic
.....................................

[IMG]http://img146.imageshack.us/img146/1295/screenshot1im6.png[/IMG]

---

### Post by stop_that on 2006-08-11
> **llamakc said:**
> 
Have you toyed with system permissions at all in the past? Weird that you're having this problem. . . .
i thinki did beforei knew abit more about sudo ect..

---

### Post by vijirajan on 2006-08-11
Create the root directory first before creating .synaptic like below:

sudo mkdir /root
sudo mkdir /root/.synaptic

---

### Post by Limulus on 2006-08-11
Maybe reinstalling Synaptic will fix things... run:

```
sudo apt-get --reinstall install synaptic
```

and when its done, try Synaptic again.

---

### Post by stop_that on 2006-08-12
> **vijirajan said:**
> Create the root directory first before creating .synaptic like below:

sudo mkdir /root
sudo mkdir /root/.synaptic

thNK YOU SEEMSTO HAVE SOLVED IT:rolleyes: 

thanks to everyone who posted \\:D/

---

