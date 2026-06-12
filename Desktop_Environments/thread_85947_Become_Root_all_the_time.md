---
title: "Become Root all the time"
date: 2005-11-03
forum: Desktop Environments
---

### Post by johnfarrow on 2005-11-03
When I try to copy/move/edit files, a lot of the time I am not authorized to do what I want.

How can I start a project and be the root until I no longer want to be the root.  How can hidden files be viewable all the time.  I am still trying to enlarge the scrollbar in firefox.

Thanks
John

---

### Post by raublekick on 2005-11-03
If you are working through the terminal you will only have to enter the sudo password once. After that you can use sudo without the need for a password. 

I have no idea how you would accomplish this in, say, Nautilus.

---

### Post by jasay on 2005-11-03
```
sudo -s -H
``` should turn you into root in the terminal so you don't have to type sudo all the time. ```
su <username>
``` to swith back to user from root.

```
gksudo nautilus
``` will get you a root nautilus browser.  

To view hidden files in nautilus: Edit > Preference, click "show hidden and backup files."  To view in terminal ```
ls -a
```, but that only works once.  I don't know if there is a way to do it all the time, but you could make an alias so you don't have to type the option.

---

### Post by matthew on 2005-11-03
In a terminal you can type "sudo su" and then your password and you will be root from that point on until you type "exit" to drop back to normal user status.

For Nautilus, start it from the terminal with "sudo nautilus" and you will have root power in the gui.

***be careful out there!

---

### Post by aysiu on 2005-11-03
Echoing jasay, I highly recommend ```
gksudo nautilus
```

---

### Post by not_cool on 2005-11-03
Like raublekick said, you can use sudo in the terminal. You don't need Nautilus whatsoever for opening, moving, or copying files. Lets say that you want to open and edit /etc/ld.so.conf, which requires root privilages.

BTW these directions are for the total noob, sorry if they are too basic.

1. Open a terminal.

2. you can use the command cd to change to a directory and then open a file using a program such as gedit.

```
markus@ubuntu:~$ cd /etc
markus@ubuntu:/etc$ sudo gedit ld.so.conf

```

I now have the file opened with full read/write privilages so I can make all the changes I want. When you are done, save it and close it.

The command to move files is:
```
markus@ubuntu:~$sudo mv
```

And to copy files:

```
markus@ubuntu:~$ sudo cp
```

Again, you probably already know these, but this can be used for a noob reading the forums.

---

### Post by not_cool on 2005-11-03
I don't know for sure how to enlarge the scrollbar in Firefox, but you can find out yourself by opening up a Firefox window and typing about:config into the address bar.

---

### Post by Zwack on 2005-11-03
I guess the big question is why do you need to be root...

If you are just working with files then unless they are owned by another user you shouldn't need to be root...

try changing the ownership of the files with sudo chown -R <username> <files>

Running as root all of the time is not a good idea...

Z.

---

### Post by JakeSpeare on 2005-11-03
you can also just enable the root account by assigning it a password and logging in as root when you need to do admin stuff.

> sudo passwd root

Very handy if you have a bunch of stuff to do.  Just be sure to log out when done.   Being root all the time is baaaaaaaaaaaad :)

---

### Post by johnfarrow on 2005-11-03
I need to edit the files userChrome.css and userContent.css.
They are currently in /etc/mozilla-firefox/profile and I need to move the folder to /home/john as per instructions from a member of this form.

And An outstanding forum this is indeed.  Seems like all are eager to help a noob.

I really appreciate that

John Farrow

---

### Post by theine on 2005-11-03
[QUOTE=johnfarrow]I need to edit the files userChrome.css and userContent.css.
They are currently in /etc/mozilla-firefox/profile and I need to move the folder to /home/john as per instructions from a member of this form.[/QUOTE]

I'm pretty sure it will be enough to just copy /etc/mozilla-firefox/profile to your home directory in this case.

---

