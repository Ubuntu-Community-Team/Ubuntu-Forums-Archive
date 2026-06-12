---
title: "Automatic Login with gdm display manager"
date: 2012-06-23
forum: Desktop Environments
---

### Post by pajoohesh on 2012-06-23
Hi all,

I have changed my dispaly manager to gdm and removed many stuff like unity, compiz, etc to speed up my netbook which turned out to be very useful. Now the problem is that I don't know how to enable automatic login with gdm.

I even created the file /etc/gdm/gdm.conf and put this inside but did not work:
AutomaticLoginEnable=true
AutomaticLogin=username

Any help is appreciated,

---

### Post by pajoohesh on 2012-06-26
No body yet?

---

### Post by nadarockyraccoon on 2012-07-14
I believe the file in /etc/gdm should be custom.conf. I actually used the gnome-control-center to create this file. I know this works because it will cause gdm to fail and you'll have to login to a terminal, delete this file, reboot, and manually login. I'm not sure exactly what the problem is, but I'm on to finding a solution, any help is appriciated.

---

### Post by nadarockyraccoon on 2012-07-15
All right I've got a solution that worked for me. In a terminal
```
sudo apt-get install lightdm unity-greeter
```
When prompted select lightdm as the default display manager. That should change /etc/X11/default-display-manager to read /usr/sbin/lightdm.
Now make sure that autologin is enabled by editing /etc/lightdm/lightdm.conf to contain ```
autologin-user=*username*
```as the last line, *username* being replaced with your username.

or you can use the gnome-control-center(System Settings) and enable automatic login for the user there.

Also I'm not sure how you got to your current configuration but if you want the classic ubntu desktop (oh the good old days) type in a terminal```
sudo apt-get install gnome-session-fallback
```
if you haven't already, this will ensure GNOME classic is an option when loging in.

Upon rebooting you will be given an error "can't load user-session 'Ubuntu'". Click Cancel and when sent to the login screen select the user to automatically login (assuming that username is the same as the line you edited in the lightdm.conf file) and click the ubuntu logo to the right of the password input and selct the desktop session you want, GNOME Classic(No Effects) in my case. Type in your password and you are good to go! The next time you boot your computer it should automatically login to the session you chose.

Now if only I could figure out how to get those menus to look and feel like they used too.

---

### Post by pajoohesh on 2012-07-18
Thanks :). Everything is OK now by installing lightdm.

---

