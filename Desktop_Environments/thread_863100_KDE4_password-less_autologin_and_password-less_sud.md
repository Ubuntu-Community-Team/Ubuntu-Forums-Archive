---
title: "KDE4 password-less autologin and password-less sudo"
date: 2008-07-18
forum: Desktop Environments
---

### Post by Neo¹ on 2008-07-18
Hi All,

before I start; I know, this is security risk but I really need it. 
I need to have password-less autologin in KDE4. I tried to change it in the KDE4 configuration but it simply does not works. After start I get message "Login Failed" and it go back to the normal login screen.

I would like to also use sudo without password (like on the live cd) and if it possible also the wallet manager. Or maybe it is possible in to change the behaviour of network manager in this was, that it just log in in the WLAN without asking for password.

I need it for a Tablet-PC. I need to be able to use it without keyboard. 

Any ideas ??

Regards,
Neo

---

### Post by kuja on 2008-07-28
So, password-less login and auto-login with kdm4 aren't working for you? Hmm, try installing the "kdm" package (for the kde3 version) and running the command ```
sudo dpkg-reconfigure kdm
```
Select kdm, and then configure it with ```
kcmshell kdm
``` It should work without question.

Passwordless sudo is possible, but like you said it's a pretty [size=4]huge[/size] security risk, and there's usually a better way to go about things ... If you're absolutely sure you want to do it though ... run this command in a konsole ```
sudo EDITOR=kate visudo
```

Now, look for this line:```
%admin ALL=(ALL) ALL
```

Change it to:```
%admin ALL=NOPASSWD: ALL
```
Save, exit, and reboot.

The wallet manager will be pretty easy to do, just change its password to a blank password.

---

