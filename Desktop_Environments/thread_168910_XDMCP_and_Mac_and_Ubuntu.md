---
title: "XDMCP and Mac and Ubuntu"
date: 2006-05-01
forum: Desktop Environments
---

### Post by theduke0 on 2006-05-01
I am a new mac user and would like to be able to use XDMCP for my personal linux box.  I am on an internal network and don't need the protection of ssh.  There are a several posts about xdmcp and ssh tunnelling, but I dont think that is what I need.  

I use the XDMCP chooser on my linux box to log into other machines on the network.  Now, I would like to be able to use the mac to log into my personal linux box and other computers on the network.  

I know this is more of a mac question, but the computer I would like to have a remote connection with is running ubuntu.    

Is there is a simple way to do this with a mac?  Could someone point me in the right direction?

---

### Post by drbobit on 2006-05-14
Hi,

I'm trying to do something similar (ish) with remote logon from a xebian machine and had some good success with ssh. Here's what I did...

Created a second user account on my ubuntu machine (How to is on the wiki)

```
ssh <username>@<ip address>
```

For me it was: "ssh xbox@192.168.1.4"
It will then ask you if you want to add this to the trusted hosts list, I think it's safe to say yes to this
Enter your password and you should get a new command prompt.
E.g. remoteuser@remotehost (for me it was xbox@ubuntu)

Then to open a new gnome (desktop) session...

```
gnome-session
```

I think you could also use this method with your primary login as well.

But if anyone does know if xdmcp can be run of non-ubuntu machines please reply to this post.

Thanks and happy ubuntu-ing :)

---

