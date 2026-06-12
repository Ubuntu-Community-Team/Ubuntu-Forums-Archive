---
title: "Changing permissions"
date: 2005-05-11
forum: Desktop Environments
---

### Post by Peter Alien on 2005-05-11
I know that i can execute commands in Konsole has a normal user and/or has Root.

But can i do the same in Konqueror, e.g. if i wanted to change permissions of a file, do i have to do it only in Konsole or can i do it in Konqueror? 

The problem is that i want to change a file that only has Root permission, can i change it in Konqueror without going to Konsole ? How ?

Thanks

---

### Post by Xian on 2005-05-11
[QUOTE=Peter Alien]The problem is that i want to change a file that only has Root permission, can i change it in Konqueror without going to Konsole ?[/QUOTE]
Yes, but you have to open Konqueror with root permissions.
To do this run the following command from either a terminal or the KDE start menu:

kdesu konqueror

Then right-click on the file in Konqueror > Properties > Permissions

---

### Post by Peter Alien on 2005-05-11
When i write that in Konsole, it gives me an error of:

"Could not open network socket
Please check that the DCOPSERVER program is running!"

and doenst happend anything more :(

---

### Post by Xian on 2005-05-11
[QUOTE=Peter Alien]When i write that in Konsole, it gives me an error of:

"Could not open network socket
Please check that the DCOPSERVER program is running!"

and doenst happend anything more :([/QUOTE]
Okay, then just goto to your KDE start menu and click on 'Run Command'. 
Enter the same thing: kdesu konqueror

That should work.

---

### Post by Peter Alien on 2005-05-11
Nope, gives the same error :(

---

### Post by Peter Alien on 2005-05-11
Ok i just got it...

I had to reboot Ubuntu, because he was getting a bit  :wink: nuts

Ok, many thanks :)

---

### Post by Xian on 2005-05-11
Check to see that you have write permissions to your /home directory, especially the hidden '.DCOPserver_linux__0' files. It should look something like what is shown below, save that your user name is in place of mine:

[img]http://img.photobucket.com/albums/v469/camplear/forums/dcop.jpg[/img]

---

### Post by Xian on 2005-05-11
[QUOTE=Peter Alien]I had to reboot Ubuntu, because he was getting a bit  :wink: nuts[/QUOTE]
Heh. I know the feeling. :)

---

