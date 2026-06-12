---
title: "can no longer access folders"
date: 2011-03-17
forum: Desktop Environments
---

### Post by dmwdrown on 2011-03-17
Hello I am new to Ubuntu and have been using it for a few months. Recently when I have gone to the Places drop down box and tried to get into any of my folders i get this message: 


> Could not open location 'file:///home/username'
Failed to execute child process "/usr/bin/arista-transcode" (No such file or directory)I have looked through the forum for the past few days and have still not found a solution that works. Any ideas/solutions will be greatly appreciated. 

P.S. As i am an extremely new user please use small words! :lolflag:

---

### Post by Krytarik on 2011-03-17
It seems like you have inadvertedly chosen "arista-transcode" as the default application to handle folders.

Solution: Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Greetings.

---

### Post by dmwdrown on 2011-03-18
Thank you as soon as i can get into my computer i will give it a try. It installed new updates and will no longer accept my log in password-sigh :\

---

### Post by Krytarik on 2011-03-18
> **dmwdrown said:**
> Thank you as soon as i can get into my computer i will give it a try. It installed new updates and will no longer accept my log in password-sigh :\
Do you get a "password incorrect" message or simply nothing?
Try to login at the console, press Ctrl+Alt+F1 when you are at GDM's login screen to get to one.

To reset your password follow this guide:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by dmwdrown on 2011-03-19
I don't get any message at all it acts like it is going to load, goes to a blank screen and then takes me back to the log in screen. I tried ctrl+alt+f1 and typed in username and password it told me some info on what version of ubuntu i am running gave me the website address for documemtation and then says: username@username-Dell-DM061:~$ and then i dont know what to type after that.
:)

---

### Post by Krytarik on 2011-03-19
Please check "~/.xsession-errors" for error messages after trying again to log in:
```
more ~/.xsession-errors
```

---

### Post by dmwdrown on 2011-03-19
It says: no such file or directory

---

### Post by Krytarik on 2011-03-19
> **dmwdrown said:**
> It says: no such file or directory
Oh, I made a typo, sorry! :P
I corrected the previous post. Please try again.

---

### Post by dmwdrown on 2011-03-19
It says:

"/etc/gdm/Xsession: Beginning session setup..

Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit.d/all_ALL linked to /etc/x11/xinit/xinput.d/default.
/etc/gdm/Xsession: Beginning session setup...
.: 34: cant open /home/username/.profile

---

### Post by Krytarik on 2011-03-19
Please run those command:```

sudo chown USER.USER -R /home/USER
```

---

### Post by dmwdrown on 2011-03-19
It says: chown: invalid user: 'USER.USER'

---

### Post by dmwdrown on 2011-03-19
It says: chown: invalid user: 'USER.USER'

---

### Post by Krytarik on 2011-03-19
> **dmwdrown said:**
> It says: chown: invalid user: 'USER.USER'
Hey, you need to replace it with your user name! I thought that was obvious enough. ;-)

---

### Post by dmwdrown on 2011-03-19
Sorry! I did say I am a total novice at this :) okay so i am assuming everytime you put in user that i am supposed to substitue it with my username...I did that and it asked for my password which I typed in and then nothing.....

---

### Post by Krytarik on 2011-03-19
Sorry, I assumed that you'll know what I mean, because I thought you replaced this one. Or is it your real username?
> **dmwdrown said:**
> 
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit.d/all_ALL linked to /etc/x11/xinit/xinput.d/default.
/etc/gdm/Xsession: Beginning session setup...
.: 34: cant open /home/**username**/.profile
> **dmwdrown said:**
> I did that and it asked for my password  which I typed in and then nothing.....
The output of those command is indeed nothing, if run correctly.
Did you try to log into your desktop after that!?

---

### Post by dmwdrown on 2011-03-19
Sorry for being such a novice but how do i do that?
i tied typing in sudo login and it asked for my username and password which i typed in and then it just said welcome to ubuntu my last login date and what version is running. I am not sure how to get to the actual startup page from here....
Thank you for all your help and patience :)

---

### Post by Krytarik on 2011-03-19
> **dmwdrown said:**
> Sorry for being such a novice but how do i do that?

Just reboot. ;-)

---

### Post by dmwdrown on 2011-03-19
Reboot didnt work. Just did the same thing it was doing before....  :(

---

### Post by Krytarik on 2011-03-20
Do you have an encrypted home directory or something like that?

When you login at the console and do "ls -al", do you see all the contents of your home directory?

---

