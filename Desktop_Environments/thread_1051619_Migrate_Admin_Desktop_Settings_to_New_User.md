---
title: "Migrate Admin Desktop Settings to New User"
date: 2009-01-26
forum: Desktop Environments
---

### Post by keithld on 2009-01-26
Well now that I have been around the forums for a while I see that it not a good idea to be logged in as Administrator all the time.. I have set up a new user and since I have all my AWM Manager/Dock, Firefox Bookmarks/Settings, Panels, Songbird, SKYPE, Desktop Theme, etc. setups the way I want them, is there any way to copy or move those to the new user???...


I also found out, that running SKYPE with sudo Skype for some Logitech Quickcams (or all Webcams) is a bad idea, so anyone doing that you can do this and it works...

Edit /etc/rc.local to make the camera device permissions available to all users on system startup.

sudo gedit /etc/rc.local

The line just before "exit 0", put in:

chmod 777 /dev/video0


The last two lines of /etc/rc.local should look like this:

chmod 777 /dev/video0
exit 0


Thanks guys,

Keith

---

### Post by pytheas22 on 2009-01-26
Being logged in under an account with administrator rights is not that dangerous, because you still need to enter your password before you can use 'sudo' to do anything that would damage the system.  In most other Linux distributions, which use 'su' instead of 'sudo', logging in as root can be a hazard--that may be where you got the idea that you shouldn't log in as administrator in Ubuntu.  But being logged in with 'sudo' privileges is not equivalent to being root--actually the root account doesn't really exist in Ubuntu.  The Ubuntu installer wouldn't give the first user account sudo privileges if it were a security risk.

But if you really want to use a non-privileged account, why not just go to System>Administration>Users and Groups and create a new account just for administrative tasks, and then take away the privilege for your existing account to 'Administer the System'?  This would be a simpler and more efficient solution than creating a second account and moving your files over (although if that's what you really want to do, I'll give instructions if you ask).

Just make sure that there's always at least one account on your system that has administrative privileges.

Also, your solution for the webcam, while valid, is not the most secure way to do it.  You should almost never have a good reason to give something 777 permissions.  A better way to make the webcam available to all users would be to create a group for webcam users and add all accounts to it that you want to be able to access the device.  But have 777 permissions on the webcam is realistically not the end of the world, so don't necessarily change it if it's working now.

---

### Post by keithld on 2009-01-26
Thanks **pytheas22** those are good tips...

Like I said I'm new to Ubuntu and I did have SKYPE loading from Sessions/Startup Programs with the command sudo skype... I thought it was a No, No...

Oh well...  :popcorn:

---

