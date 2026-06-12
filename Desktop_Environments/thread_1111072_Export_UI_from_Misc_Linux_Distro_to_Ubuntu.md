---
title: "Export UI from Misc Linux Distro to Ubuntu"
date: 2009-03-30
forum: Desktop Environments
---

### Post by inadaze on 2009-03-30
Hey all,
I know there is a way to send the display of a linux machine to another linux machine but for some reason everything I have tried does not work.  At work, my PC is Ubuntu 8.10 and we build a product with a form of Linux on it.  We have a way to export a NEW UI from the Linux machine to our PC but I want to export the ACTUAL UI of the machine.  In other words, control what I see on the remote Linux machine instead of creating a new UI that just looks like what is on the remote machine.  

In case I am not being clear, as an example, I know that you can do this in Windows (sigh, yes I said it...).  There is a functionality that allows an admin to access remotely a Windows PC and you can actually see on the remote pc that the admin is moving your mouse etc...  This is the type of thing I was looking for.  There must be a way?

thanks
Jay

---

### Post by blackened on 2009-03-30
[https://help.ubuntu.com/community/VNC]("https://help.ubuntu.com/community/VNC")

---

### Post by inadaze on 2009-03-31
I can't use VNC becuase I cannot install the server on the machine I want to connect to.  the only way I see to do this is through SSH port-forwarding but I cannot figure it out.  I tried running :

ssh -L 5900:localhost:5900 root@myPCipaddress

on the machine I want to connect to but all it does is connect via ssh to my pc.  I feel like I am missing obvious steps that tutorials leave out because they assume that everyone knows how to do this, but I don't.  Just a little confused.

j

---

### Post by inadaze on 2009-03-31
Can I use Xephyr to connect from my PC to another computer?  If so, has anyone had experience and could give me a hand?

J

---

### Post by inadaze on 2009-04-02
Anyone?  Please....

I am sure that exporting X through ssh tunnel would work I just can't figure out how to use it.  I get confused because different tutorials do it differently and change which computer to do it from.  Anyone ever done this?

J

---

