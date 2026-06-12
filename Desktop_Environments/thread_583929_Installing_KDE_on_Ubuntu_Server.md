---
title: "Installing KDE on Ubuntu Server"
date: 2007-10-20
forum: Desktop Environments
---

### Post by Indefual on 2007-10-20
I know, I know... Don't use a graphic DE on a server.  I'm just playing around a bit and would like to be able to load X/KDE one a whim if need be.

On Ubuntu Server 7.10 I typed in "apt-get install KDE" and it did it's think.  I then typed startx after it finished and it gave me:

"xauth:  creating new authority file /home/indefual/.serverauth.15899
X: cannot stat /etc/X11/X (No such file or directory), aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console" 

(this is through ssh since I knew it wouldn't work)

So I thought that X wasn't installed.  I typed "apt-get install x" and "apt-get install x11" to no avail.

So I have two questions:

1) What's wrong, what do I need to install?

2) Is there any way to find out what a apt-get package's name is?  Is there a listing of them ALL somewhere, on my computer? Else where?  Searchable?

Thanks.  And yes, I'll look in to webmin and the like to my remote configuring needs. :)

---

### Post by arneo on 2008-06-11
KDE requires the "x-window-system-core" package, [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

---

