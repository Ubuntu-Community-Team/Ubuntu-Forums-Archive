---
title: "Ubuntu and Kubuntu"
date: 2010-11-29
forum: Desktop Environments
---

### Post by renehasekamp on 2010-11-29
I can't find this anywhere, although related issues are to be found all over the net. 
Here is my issue. I will simplify is as much as possible.Still all this might confuse you:

- I installed Ubuntu netbook 10.04.

- I put Kubuntu next to it, by installing "kubuntu netbook". I chose gdm for logging in. 

- This works perfect. I can use Ubuntu or Kubuntu on signing in.
This is my config A

- Later I changed gdm to kdm through "sudo dpkg-reconfigure gdm".
This is my config B.

Under config A: 
I can choose several options on login, among which Ubuntu netbook and Kubuntu netbook (kde). Both work well, but I cannot close down from Kubuntu. I have to log out and return to the login screen, from where I can close down.

Under config B: 
I get the same choice of login options, among which Ubuntu netbook. BUT when I choose that option, I am sent to Ubuntu desktop (Ubuntu with Gnome desktop) instead of Ubuntu netbook.
(Tried a dozen times) 
From there (Ubuntu desktop) I can close down, log out etc. But Ubuntu netbook is not available.

When I login to Kubuntu netbook under config B, I also have all the options to log out, close down etc., contrary to config A, that only lets me only log out of Kubuntu netbook.

I now went back to config A, because I want to be able to use Ubuntu netbook, and everything is as it was.

However: I would prefer config B, because I would like to be able shut down from Kubuntu, as well as from Ubuntu, but I would also like to use Ubuntu netbook.

Anybody? A bug in kdm?

---

### Post by renehasekamp on 2010-12-01
Although the problem remains a riddle to me (under kdm, when I choose "ubuntu netbook", on login, I get Gnome), I found a good workaround:

- When in Gnome, press ALT + F2,
- type "netbook-launcher" in the command box that appers (without quotes). This will give you the netbook interface. If you also want to make the gnome panels at the top and bottom of the screen invisible, do the following:
- right click on them and mark the box "make invisible automatically (or whatever this options is called in English).

This brings you as close as it gets to a Ubuntu netbook interface.

---

