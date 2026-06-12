---
title: "Two problems"
date: 2009-04-11
forum: General Help
---

### Post by Grim Tuesday on 2009-04-11
First, I couldnt get my monitor to 1280X1024. I was fiddling about in the options section, and I accidently switched my resolution to one that my monitor does not support. Of course, I waited for my monitor to go back to normal resolution, but it never did. Now, I am stuck with one account (the admin account) that cant display anything, and another accout (normal privileges) that can, but cant do anything about it, as it has no user priveleges. This is very annoying. It is complicated by the fact that I am running a triple boot, so a simple reinstall cant be done. Can anyone help me fix this?

---

### Post by tommcd on 2009-04-11
Boot to reocovery mode and choose the option "xfix fix video" (or whatever it says). Then reboot and you should be good.

---

### Post by Grim Tuesday on 2009-04-11
I cant do that. Whenever I select XFIX, it says something about corruption after a sec or so. By rooting around in the root interface, all i managed to do was delete my old account, and not get a new one.

EDIT: this means that there is no root user on this system now

---

### Post by apmcd47 on 2009-04-12
> **Grim Tuesday said:**
> I cant do that. Whenever I select XFIX, it says something about corruption after a sec or so. By rooting around in the root interface, all i managed to do was delete my old account, and not get a new one.

EDIT: this means that there is no root user on this system now

Do you have a live disc? Boot from that, mount your root partition read/write and edit the etc/group file to put your remaining account into the admin group.

Andrew

---

### Post by tommcd on 2009-04-12
> **Grim Tuesday said:**
> I cant do that. Whenever I select XFIX, it says something about corruption after a sec or so.

What does it say is corrupted? Can you post the errors?
You could also try booting to recovery mode and choose the option to drop to a terminal and run:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg
```
and go through it. Choose the defaults if you are not sure what to select. See this:
[https://help.ubuntu.com/community/XDisaster](https://help.ubuntu.com/community/XDisaster)
> **Grim Tuesday said:**
> 
 By rooting around in the root interface, all i managed to do was delete my old account, and not get a new one.
EDIT: this means that there is no root user on this system now

**How** did you delete your account? Does your /home/user_name directory still exist?

In any case boot to recovery mode, drop to a terminal and run:
```
sudo adduser your_user_name
```
This will re-create your user account.
To add a password for your user:
> sudo passwd your_user_name
Then:
```
sudo groups your_user_name
```
This will list what groups your user is now a member of. On my system it returns:
```
tom adm dialout cdrom plugdev lpadmin admin sambashare
```
To add yourself to any of those groups that you are not a member of:
```
sudo gpasswd -a group1 group2 group3
```
You will need to be a member of the **admin** group to sudo. Use the same user name you had before, so you don't have to edit /etc/sudoers file.
Then reboot with **sudo reboot** and see how it goes.

---

### Post by Grim Tuesday on 2009-04-14
Thankyou sooooooooooooo much. It is now working perfectly, and at the correct resolution. Thanks.

EDIT: There is now a new problem. :(. For some reason I cant enable the restrcted drivers. when I do, i get an error:
```
 SystemError: Failed to lock /var/cache/apt/archives/lock
```

---

