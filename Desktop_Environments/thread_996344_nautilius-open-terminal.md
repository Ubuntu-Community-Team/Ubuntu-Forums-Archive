---
title: "nautilius-open-terminal"
date: 2008-11-28
forum: Desktop Environments
---

### Post by ganesh4it on 2008-11-28
Hi am new to Ubuntu forum and also working with linux..,

i dont know from where i can rise the new thread(mak e new post)...plz help me...


Also i need your help to install "nautilus-open-terminal 0.8"..
am trying past three day am not able to install.....

its very urgent plzz help me out...,

---

### Post by the yawner on 2008-11-28
> **mythmgn said:**
> I carelessly used apt-get command to remove a deb package,and it  removed the 'add/remove' in the applications menu as well.
   please tell me what's the deb package name of it in order that i could reinstall it.
   thanks

Try:
```

sudo apt-get install gnome-app-install

```
or just search for the package *gnome-app-install*.

=====
> **ganesh4it said:**
> Hi am new to Ubuntu forum and also working with linux..,

i dont know from where i can rise the new thread(mak e new post)...plz help me...

Look for the link New Thread to create your own thread and kindly avoid hijacking other threads in the future. As for your issue:

> 
Also i need your help to install "nautilus-open-terminal 0.8"..
am trying past three day am not able to install.....

its very urgent plzz help me out...,
```

sudo apt-get install nautilus-open-terminal

```

---

### Post by ganesh4it on 2008-11-28
hi its shoeing the following err:


[root@Infmy10321 nautilus-open-terminal-0.9]# sudo apt-get install nautilus-open-terminal
sudo: apt-get: command not found



wT SHELL I DO ? ? ?

---

### Post by ganesh4it on 2008-11-28
hi i got the installer of "nautilus-open-terminal 0.8" bujt while doinf 
"configure" and "configure.in" am getting the following Error . .
wt i need to do for this...,

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""


checking for NAUTILUS_LIBS... 
configure: error: Package requirements (libnautilus-extension >= 2.6.0 glib-2.0 >= 2.4.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the NAUTILUS_CFLAGS and NAUTILUS_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.



"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

---

### Post by the yawner on 2008-11-28
First off, it seems you're trying to compile the nautilus plugin. This is not necessary in Ubuntu as the package can easily be installed via _apt-get_. However, your installation appears to not have apt-get. Might I ask what Ubuntu version are you using? It's rather odd for apt-get to be missing.

> 
[root@Infmy10321 nautilus-open-terminal-0.9]#

Judging from the terminal prompt you have posted, I'm guessing you're using Fedora?

---

### Post by ganesh4it on 2008-12-06
hi need to install open terminal for my fedora 8(Linus PC)..
i tat its showing the above error :(

---

