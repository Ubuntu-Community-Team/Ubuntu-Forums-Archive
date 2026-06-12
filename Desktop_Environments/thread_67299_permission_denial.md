---
title: "permission denial"
date: 2005-09-19
forum: Desktop Environments
---

### Post by mdozama on 2005-09-19
hello to all! need help here!

im just a noob at ubuntu. i played around at my user account. probably unchecked those permissions! lolz. now everytime i use the root terminal. after logging the password. i kept on getting these.
[http://www.ubuntuforums.org/attachment.php?attachmentid=2502&stc=1](http://www.ubuntuforums.org/attachment.php?attachmentid=2502&stc=1)

how do i go back to those permissions! how to log in as root in desktop? 

thanks a lot!

---

### Post by Emerzen on 2005-09-19
mdozma, not sure exaclty what your error is?  If you messed up your permissions you can try this:

Go to Applications>accessories>terminal.  After it opens up type

----------------------------------------------------------------
sudo nautilus
----------------------------------------------------------------

enter your password and a file browser w/ root priveleges will open.  Browse to any file  you need and you can change the permissions as needed.  If you've forgotten/accidentally changed your password, there is a way to reset it documented at

----------------------------------------------------------------
[Ubuntuguide](http://www.ubuntuguide.org) 
----------------------------------------------------------------

The site is down at the moment, and I don't remember how to do it off the top of my head, but give me a little more detail on your problem and I'll see what I can come up, or maybe someone else w/ more experience can help you.

---

### Post by Xian on 2005-09-19
Sounds like you have lost sudo priviledges.

Choose "Recovery Mode" when you restart your computer. 
That will boot you to a terminal with ROOT priviledges. 

Modify the sudoers and add yourself to the file.

At the command prompt:

```
$ visudo
```

Then add a line similar to this:

```
your_username ALL=(ALL) ALL
```

---

