---
title: "Thin client?"
date: 2006-09-24
forum: Desktop Environments
---

### Post by Schalken on 2006-09-24
I was just wondering if, say I had two Ubuntu computers on my home network, would one computer be able to 'log in' to the other, so that it is runing like a thin client?

Also is it possible to run just one application on someone else's computer, while the IO goes though your own?

---

### Post by Shay Stephens on 2006-09-24
VNC?  Or is that overkill for the situation?

---

### Post by blackened on 2006-09-24
> Also is it possible to run just one application on someone else's computer, while the IO goes though your own?

Assuming you have ssh installed:

```
ssh -X <hostname> /usr/bin/gnome-terminal
```

Replace pieces as needed. Remember that the executable path is on the remote machine.

---

### Post by lamego on 2006-09-24
There are packages specific to build thin client services on Ubuntu, please check:
[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

---

### Post by Schalken on 2006-10-01
Then what's the 'Remote' tab in the 'System -> Administration -> Login Window' for?

Doesn't this 'Remote login' or 'XDCMP' provide some sort of thin or fat client capabilities, as [this WIkipedia article section]("http://en.wikipedia.org/wiki/XDMCP#Local_and_remote_display_management") mentions?

---

### Post by Crooksey on 2006-10-01
From the GDM, "Remote login via XDMCP"

[http://en.wikipedia.org/wiki/XDMCP](http://en.wikipedia.org/wiki/XDMCP)

That work?

---

### Post by Schalken on 2006-10-01
> **Crooksey said:**
> That work?
I don't know, does it?

I'm being hypothetical. I don't actually have two Ubuntu computers on a network.

What capabilities does this 'XDMCP' provide? Can a SUSE or Windows computer log into an Ubuntu computer, for example, or vice versa? What configuration is required from a fresh Ubuntu install? What is actually running on the client computer and the server? Can it be done over the Internet? How many computers is it suitable for?

And when is it necessary to instead boot the entire computer off the network? What's the difference between it and VNC?

---

### Post by treris on 2006-10-01
I actually have two pc's working this way. I have an old laptop (p2-333mhz, 160mb, 4,5Gb) which is running xubuntu and a newer desktop pc (amd64 3500, 1Gb, 3*160Gb) which is running kubuntu.

Normally, obviously, I use my desktop, but when I have to go somewhere and still have to do some computing I bring my laptop. I then use [FreeNX]("https://help.ubuntu.com/community/FreeNX") to log in to my desktop to be able to use OpenOffice and have access to all of my files. OpenOffice obviously not running too stellar on my laptop this solution using FreeNX has worked out quite well for me and is very easy to get working.
Another thing I like about FreeNX is that there are client app's available for both linux and windows so that I can also use it to log in to my computer from computers running windows.

Hope this gives you some information

---

