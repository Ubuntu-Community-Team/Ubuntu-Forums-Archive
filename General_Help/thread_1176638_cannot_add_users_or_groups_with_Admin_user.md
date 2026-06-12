---
title: "cannot add users or groups with Admin user?"
date: 2009-06-02
forum: General Help
---

### Post by r0ot5 on 2009-06-02
Hi, 

just install Ubuntu Desktop 8.04. Now i'm trying to add users from the Administration -> Users & Groups.

The add & unlock button is grayed out, I cannot add anything at all. I did try to use the sudo users-admin and still nothing...

not sure what to do now?

thx, 

r0ot5

---

### Post by blueridgedog on 2009-06-02
This appears to be a bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/231246](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/231246)

Note you can add users and groups via the command line:

```
sudo /usr/sbin/adduser
sudo /usr/bin/passwd USERNAME
sudo /usr/sbin/groupadd
```

You can put members in groups with the usermod command.

---

### Post by Macchi on 2009-06-14
I have seen this problem now on fresh installs of 8.04 and 9.04 while accessing the machine through remote desktops such as XDMCP and NX.

I will experiment more and post some comments later.




PS:
> **blueridgedog said:**
> 
...
Note you can add users and groups via the command line:
...

Sorry, but I have to make a remark on that: Yes, command line has been around for quite a while, probably since those early electro-mechanical teletypes got hooked to computers as terminals. We know that CLI solutions will get the job done and can be acceptable for certain workarounds. But my experience is that the need for CLI on basic adminstrative tasks will not contribute positively for the adoption of Ubuntu by wider groups.

---

### Post by lamego on 2009-06-14
> Sorry, but I have to make a remark on that: Yes, command line has been around for quite a while, probably since those early electro-mechanical teletypes got hooked to computers as terminals. We know that CLI solutions will get the job done and can be acceptable for certain workarounds. But my experience is that the need for CLI on basic adminstrative tasks will not contribute positively for the adoption of Ubuntu by wider groups.
This comment out of context, blueridgedog was just presenting the command line alternatives as a work around for the reported bug, he was not advocating it's usage as a replacement for the graphical interface.
In my experience the availability of choices, one of them been between CLI or GUI is one of Linux's strongest point's leading to it's adoption.

---

### Post by blueridgedog on 2009-06-14
> **Macchi said:**
>  But my experience is that the need for CLI on basic adminstrative tasks will not contribute positively for the adoption of Ubuntu by wider groups.

True!  But, I am a "land the plane" sort of guy and I will try my best to come up with alternatives to bugs for the very reason you mention above.  

What brought you across this old thread anyway?

---

