---
title: "lock screen not working and system logs in without password...."
date: 2014-10-13
forum: Desktop Environments
---

### Post by jvidaurre7 on 2014-10-13
[COLOR=#333333][FONT=Ubuntu]The lock screen on Ubuntu 14.04.1 LTS is not working for some reason, .it wants to lock...however the screen just bounces...would appreciate any insight here...thanks... I believe the package for the lockscreen is gnome-screensaver[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I expected the screen to lock.
Instead the screen just bounces and doesn't lock. this happened after i updated to the new version of ubuntu.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]here is a video of it not locking: [http://youtu.be/RCCepVCQ0Zo](http://youtu.be/RCCepVCQ0Zo)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Here is the auth.log for when I tried to lock the screen[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Oct 12 22:58:15 jorge-MS-7788 compiz: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Oct 12 22:58:15 jorge-MS-7788 compiz: PAM adding faulty module: pam_kwallet.so[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Oct 12 22:58:15 jorge-MS-7788 compiz: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" was met by user "jorge"

the lock screen comes up  with the command:  "dm-tool lock" in terminal howeverican log in by just clicking in the empty password field under the username. I would like to have to enter a password to login, how do I do that? When I go to change the password in user accounts the change password 
box is greyed out. I would also like to lock the screen with the gui.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]When I boot ubuntu I can login without entering the password, I would like to have to enter a password, how can I do this?

kind regards[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]thanks[/FONT][/COLOR]

---

### Post by jvidaurre7 on 2014-10-14
I think this has to do with passwords as I cant set a password to login.

---

### Post by deadflowr on 2014-10-14
You would have set a password when you installed Ubuntu.
(You have to input a password to proceed with the installation, it's required)
However, it seems you most likely also set it to autologin as well.

I do not set it to auto login so I'm not sure, but I would look at the settings in System Settings >> Brightness and Lock and see whether the toogle for require password is set for on or off.

To access the user accounts settings you need to click on the lock in the right corner, and input your password.
If for some odd reason, you cannot remember the password you set during installation, you might need to do a quick reset.
Looky here:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by jvidaurre7 on 2014-10-14
I believe the autologin setting is off. Here is a pic of the auto login settings: [IMG]http://i.imgur.com/zXA6K0k.png[/IMG]

---

### Post by jvidaurre7 on 2014-10-14
It seems that somehow my user got added to the nopasswordlogin group. Removing my user from this group would solve the problem so I solved this by going into the terminal and typing in the command line:  sudo gedit /etc/group and deleting my user name from the nopasswdlogin group in the text file and then saving the file again. Now I can lock the screen and the system requests a password on the ubuntu login screen. The screen wouldn't lock before because there was no password with which to lock the screen. The system didn't request a password because the user was in the nopasswordlogin group. Thanks.

Kind Regards

---

