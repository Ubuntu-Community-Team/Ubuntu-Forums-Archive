---
title: "APT broken - can't fix!"
date: 2008-07-01
forum: Desktop Environments
---

### Post by palob on 2008-07-01
Hi,

Can anyone help. I am a new Linux user. have installed Kubuntu KDE4 onto my desktop and have managed to break APT. i can't load it, i tried to attach a hard drive as another sources for loading software, thought it had failed. however it has entered this drive onto the end of the sources.list and everytime it tries to load apt fails with an error message saying it doesn't recognise this entry in line 56.  i have read everything I can find on apt but i can't seem to amend the sources file, it doesn't recognise my authority and keeps asking for the root user, i am the only user.

Sorry this has taken so long, but I'm getting to the point that i might abandon Linux, since it has me stumped! i have tried apt install etc etc

Thank you if anyone can help.

PS i've always been very good at breaking systems!

---

### Post by MacMan on 2008-07-01
To execute a command as root in (K)Ubuntu you use the sudo command. In this case, to edit your sources.list file as root you would open a Konsole and type something like:
```
 sudo kate /etc/apt/sources.list 
```
Press enter to execute the command: the system will ask you for your password: insert the password you use as a normal user.

Yours is a question about a very basic aspect of Ubuntu, so I suggest you go and read some documentation. That's the way you do it with Linux: **first** search around for tips (Google is your friend, and this forum is a huge knowledge base as well) and **then** eventually ask here.

With just a bit of patience you'll learn fast and become acquainted with your new Linux system in no time - and you'll have a lot of fun!

Ciao.

---

### Post by palob on 2008-07-01
hi,

Thank you for your help. i have tried sudo and your suggestion but it doesn't recognise the command.

---

### Post by MacMan on 2008-07-01
It would be very helpful to know exactly what output you got when you tried the command. Can you try again and paste the result here?

Ciao.

---

### Post by palob on 2008-07-01
Hi,

Thank you for your help.

response received

sudo: kate: command not found.

---

### Post by MacMan on 2008-07-02
You will have to make do with a console editor. Try this:
```
sudo nano -w /etc/apt/sources.list
```

Make your change, then press CTRL+X to exit. The program will ask you if you want to save your changes. You press Y to confirm. Good luck.

Ciao.

---

