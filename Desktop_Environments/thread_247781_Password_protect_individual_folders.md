---
title: "Password protect individual folders"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-08-31
Is it possible to password protect individual folders in my home directory?  I want to allow people to use my login, usually whilst I am there, for things like playing music etc, however in case I leave the room for a few moments, I don't want them to be able to view my private documents.

I don't really want to set up whole new user accounts, or to make the folders root-access only.  Just to make a separate password required to view particular folders.  

How do I do this?

---

### Post by amo-ej1 on 2006-08-31
Altough you said you don't want to set up user accounts it will be extremely easy to do so. Password protecting directories is not supported by the standard filesystems (why should they support that ? they use permissions ..). So save yourself a lot of trouble and create a simple guest account others can use and protect your files with an easy chmod.

---

### Post by Lunar_Lamp on 2006-08-31
It's something that would be very useful in a student environment; several people in my room, listening to music etc on my profile - I don't want to be worried about if I leave the room they are going to be able to view my personal files.  To have to logout and login as another user everytime anyone else is in the room is just a hassle (creating a new user account takes about 5 clicks, so isn't a problem, it's the inconvenience of logging in and out).

---

### Post by f76 on 2006-08-31
Create a folder w sudo and set the permissions so you cant read it as your normal user. then u can sudo to acess the stuff. That should work right?

sudo chmod u=rw,go= <folder name>

---

### Post by Lunar_Lamp on 2006-08-31
Sort of, but it means that if you double click on a folder that you need to use sudo to open you just get an empty folder; you need to use the command line to open the files contained within it.

---

### Post by tribaal on 2006-08-31
Well it's pretty easy to do if you set up a guest account:
Just give read permission to all your /home folder except the folders containing your personal stuff... :)

As simple as that.

- trib'

---

### Post by bluenova on 2006-08-31
You may want to take a look at [this thread](http://www.ubuntuforums.org/showthread.php?t=49007)

There is also a nautilus script where by you can right-click a file/dir to encrypt/password a directory. available [here](http://www.ubuntuforums.org/showthread.php?t=108513)

---

