---
title: "Transferring files through ssh"
date: 2009-01-29
forum: General Help
---

### Post by PhysicsNerd on 2009-01-29
I am very new to Linux, and know basically nothing, so keep that in mind.

I am trying to follow instructions from a professor and by reading the faq on the website for sharcnet (a computer network in Ontario for running science codes).

I am trying to transfer a directory from my laptop, located at /home/rmassey/Desktop/swift
swift is the directory I want transfered.  I can connect to the sharcnet server I'm working on, and when I try to transfer the file I type:

scp -r /home/rmassey/Desktop/swift/ [email]rmassey@silky.sharcnet.ca[/email]:home/

but I get the following error:

/home/rmassey/Desktop/swift: No such file or directory

Can anyone help me out?  Thanks.

---

### Post by jerome1232 on 2009-01-29
Sounds like what it says, your getting the path wrong.

What's the output of ls -l /home/rmassey/Desktop/swift

---

### Post by Nepherte on 2009-01-29
The way I understand it you are first ssh'ing in the server and then you try to transfer the file? You have to use the scp command instead of ssh'ing in the server.

---

### Post by PhysicsNerd on 2009-01-29
> **jerome1232 said:**
> Sounds like what it says, your getting the path wrong.

What's the output of ls -l /home/rmassey/Desktop/swift

It lists all the files and folders in swift.

---

### Post by PhysicsNerd on 2009-01-29
> **Nepherte said:**
> The way I understand it you are first ssh'ing in the server and then you try to transfer the file? You have to use the scp command instead of ssh'ing in the server.

Aha!  It worked, thank you very much, told you I'm new to this!

---

