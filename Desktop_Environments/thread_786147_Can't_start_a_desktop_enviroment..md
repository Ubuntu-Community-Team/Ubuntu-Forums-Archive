---
title: "Can't start a desktop enviroment."
date: 2008-05-07
forum: Desktop Environments
---

### Post by gneek on 2008-05-07
Hi everyone,

As usual, I messed up yet another install :P
Today, I decided to restart the computer (which I do very rarely) and Ubuntu showed me my log in screen, as usual (KDM).

When I tried to log in to Xfce (my primary DE), the system sat there for a while apparently trying to log me in, then spat KDM right back in my face. I was sort of confused at first, not knowing what to do. Then I tried to log in using KDE4, same thing. Then KDE 3.5. KDE tried to load, but then gave up with the following pop up message:

> "The following installation problem was detected while trying to start KDE:

   No write access to '/home/neek/.ICEauthority'

KDE is unable to start."

Then once I click OK, another funny looking window shows up saying

> "Could not start ksmserver. Check your installation."

Then the system goes back to KDM. So I figured... maybe ksmserver is some kind of a service that I accidentally turned off :(. And the thought of that scares me. Very much, I've had bad experiences with turning off services before...

So my question is... if ksmserver really is a service, is there any way I can start it (using Failsafe mode or a no-GUI session)?
And if it's not, what exactly is it and is there a way I can fix it?

Thanks in advance,
Nick T.

---

### Post by FakeOutdoorsman on 2008-05-08
I'm guessing there is a permission problem.  What do you see when you use the following command in a terminal?
```
ls -al ~/
```
Mine shows the following:
```
hamish@greasedscotsman:~$ ls -al ~/
drwxr-xr-x 33 hamish  hamish      4096 2008-05-07 21:02 .
drwxr-xr-x  3 root root     4096 2008-05-05 16:03 ..
-rw-------  1 hamish  hamish       636 2008-05-07 21:01 .ICEauthority
-rw-------  1 hamish  hamish       117 2008-05-07 21:01 .Xauthority
```
If you notice those two files with something other than "-rw-------" or owned by someone else then try to change the permission and owner:
```
chmod 600 ~/.ICEauthority
chown $USER:$USER ~/.ICEauthority
```

You may also need to check the owner and permission of the .ICE-unix directory:
```
ls -al /tmp
```
I get the following:
```
frink@mrpoopypants:~$ ls -al /tmp
drwxrwxrwt 12 root root 4096 2008-05-07 21:01 .
drwxr-xr-x 21 root root 4096 2008-05-05 15:38 ..
drwxrwxrwt  2 root root 4096 2008-05-07 21:01 .ICE-unix
```

If it is different for you try to fix the owner and permissions:
```
sudo chown root:root /tmp/.ICE-unix
sudo chmod 777 /tmp/.ICE-unix
```

---

### Post by gneek on 2008-05-09
Thanks for the info. I actually got X to start when I was in root (I got out of KDM and just used the text console). For some reason, "startx" wouldn't work on my normal user account "$", but only on root "#". I went to KDE Control Center and tinkered around with some permission settings in GUI. Now that I read your post and checked "ls -al ~/", .ICEauthority really does have "-rw-------" next to it!

Thanks for the reply. :)

---

