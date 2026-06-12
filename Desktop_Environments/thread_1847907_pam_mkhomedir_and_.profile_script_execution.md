---
title: "pam_mkhomedir and .profile script execution"
date: 2011-09-21
forum: Desktop Environments
---

### Post by hvaldecantos on 2011-09-21
Hello,

I'm setting up an ldap server for users' authentication. It's authenticating users right now, but when I use pam_mkhomedir to create home directory for a user that doesn't exist locally in a ubuntu ldap client, the .profile script seems to be not executed. I added some lines in the .profile script to create a symbolic link in /home/$USER/Desktop. The second time I login with this new user, the symbolic link is created. It is like the first time the .profile is executed too early before the home directory is created, or it is not executed at all.


 Is there a script that is executed after the home directory is created via pam_mkhomedir the first time?
 

 thanks.

---

### Post by hvaldecantos on 2012-03-27
As a solution I create a launcher in /etc/xdg/autostart/

A launcher is a file with some structured information:  /etc/xdg/autostart/mylauncher.desktop

[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=MyName
Exec=/usr/share/myscript.sh
Terminal=false

Then I create myscript.sh in /usr/share/

This is a temporal solution for me...

---

