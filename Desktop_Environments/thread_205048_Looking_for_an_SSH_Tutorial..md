---
title: "Looking for an SSH Tutorial."
date: 2006-06-27
forum: Desktop Environments
---

### Post by eXCeSS on 2006-06-27
All I know about SSH is that is is good for securly transfering files, and that's what I'm looking to do.

Is there any guides that can help me set this thing up?
I've never done this before and I'm hoping that I can get this working to get files off my home computer when I'm at college.

Thanks.

---

### Post by CameronCalver on 2006-06-28
Ok i have done this before i can give you step by step instruction but 1 things is it a wireless connection or wireless connections and is it  ubuntu to ubuntu

---

### Post by jazzgossen on 2006-06-28
Install openssh-server on your home machine. Then you will be able to login to it from college with an ssh client. Just do 

ssh yourusername@yourhomeaddress

if you use Unix/Linux, or run PuTTY if you run Windows. 

To transfer files, you can use scp, which works pretty mych like cp. 

scp username@hostname:remotepath localpath

There also secure FTP, which might be more handy for transferring files than scp, but I never used that myself.

---

### Post by az on 2006-06-28
You can also connect to an ssh server ( a box running ssh that is listening for connections) using nautilus.  You can transfer files the same way you would locally.

---

### Post by BlueSun on 2008-07-10
Try this one:
[COLOR="Blue"]
[FONT="Courier New"][SIZE="4"][http://principialabs.com/beginning-ssh-on-ubuntu/]("http://principialabs.com/beginning-ssh-on-ubuntu/")[/SIZE][/FONT][/COLOR]

---

