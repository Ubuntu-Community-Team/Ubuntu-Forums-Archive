---
title: "Problem after installing cinnamon"
date: 2013-12-10
forum: Desktop Environments
---

### Post by elkhedewy on 2013-12-10
Hello
 i just installed cinnamon on ubuntu 12.4
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
 After the installation complete, i logged in using cinnamon .. but i found that the menu icons exist but without the images
Also folders and files exist but the icon itself is not exist
 i logged out and tried to login using gnome classic and gnome 2 .. everthing works fine
 how to make the icons appear correctly?
 you can look at the attached file to understand

---

### Post by Confused Computer User on 2013-12-10
This apperas to affect not only you but others as well.

Follow the link bellow and eventually someone should post a solution to the issue.

[ubuntu 12.04 & cinnamon]("http://askubuntu.com/questions/386835/ubuntu-12-04-cinnamon")

---

### Post by Frogs Hair on 2013-12-10
I found a similar bug report and I have seen other posts on this problem, but don't know of any solutions. Make sure you are applying icons from the Cinnamon settings and not the Tweak Tool. When I tried Cinnamon I had to reset the icons from the Cinnamon Settings to solve the problem but I was using 13.04 at the time.     

[https://bugs.launchpad.net/ubuntu/+source/cinnamon/+bug/1245094](https://bugs.launchpad.net/ubuntu/+source/cinnamon/+bug/1245094)

---

### Post by elkhedewy on 2013-12-10
> **Frogs Hair said:**
> I found a similar bug report and I have seen other posts on this problem, but don't know of any solutions. Make sure you are applying icons from the Cinnamon settings and not the Tweak Tool. When I tried Cinnamon I had to reset the icons from the Cinnamon Settings to solve the problem but I was using 13.04 at the time.     

[https://bugs.launchpad.net/ubuntu/+source/cinnamon/+bug/1245094](https://bugs.launchpad.net/ubuntu/+source/cinnamon/+bug/1245094)

i logged in and tried what they're saying:
 Try changing the icon theme in System Tools > System Settings > Themes to something like Ubuntu-Mono-Dark.

i did that but now cinnamon is keep crashing .. everytime i try to login using my username and choose cinnamon, i got the error message at the attachments.
by the way i tried to uninstall it and reinstall it again, but nothing changed.
then tried to add new user to check if the problem is per user, but also cinnamon crashed after logging in to the new user too
and here is the syslog :

> Dec 10 23:08:31 elkhedewy cinnamon-session[8039]:  WARNING: Error while executing session-migration: Failed to execute  child process "session-migration"
 (No such file or directory)
Dec  10 23:08:31 elkhedewy kernel: [ 1068.271081] cinnamon[8116]: segfault  at 20 ip 00007f8ea94269f8 sp 00007fff91012830 error 4 in  libcogl.so.9.1.0[7f8
ea9409000+83000]
Dec 10 23:08:47 elkhedewy goa[8293]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Dec 10 23:08:49 elkhedewy cinnamon-session[8039]: CRITICAL: csm_manager_set_phase: assertion `CSM_IS_MANAGER (manager)' failed
Dec 10 23:08:49 elkhedewy cinnamon-session[8039]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed

---

### Post by buzzingrobot on 2013-12-11
I saw the same missing icon issue on an install of Linux Mint 16 Cinnamon.  Switching to different icon sets fixed it.  It seem, perhaps, that not every icon set provides icons for every use in Cinnamon. 

I'm not sure the Mint team has yet ported this Cinnamon version to Mint 13, which is based on the 12.04 release.  If not, then it isn't surprising problems pop up on 12.04.

In any case, I'd use only Cinnamon's tools to configure it.

---

### Post by elkhedewy on 2013-12-14
The problem now is cinnamon not working

its keep crashing

everytime i try to login using my username and choose cinnamon, i got the error message at the attachments.
by the way i tried to uninstall it and reinstall it again, but nothing changed.
then tried to add new user to check if the problem is per user, but also cinnamon crashed after logging in to the new user too
and here is the syslog :
			 				Dec 10 23:08:31 elkhedewy cinnamon-session[8039]:  WARNING: Error  while executing session-migration: Failed to execute  child process  "session-migration"
 (No such file or directory)
Dec  10 23:08:31 elkhedewy kernel: [ 1068.271081] cinnamon[8116]:  segfault  at 20 ip 00007f8ea94269f8 sp 00007fff91012830 error 4 in   libcogl.so.9.1.0[7f8
ea9409000+83000]
Dec 10 23:08:47 elkhedewy goa[8293]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Dec 10 23:08:49 elkhedewy cinnamon-session[8039]: CRITICAL: csm_manager_set_phase: assertion `CSM_IS_MANAGER (manager)' failed
Dec 10 23:08:49 elkhedewy cinnamon-session[8039]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed

---

### Post by cmcanulty on 2013-12-14
you may just have to go to synaptic and install the proper icon set example (gnome-icons) without the parentheses etc

---

### Post by rewyllys on 2013-12-15
One possible solution that you might consider is that of simply installing Linux Mint Maya with Cinnamon directly.  

Maya is the version of LM that is based on Ubuntu 12.04. LM backports new versions of Cinnamon into Maya with only a few days delay after the Cinnamon updates are first released.

---

### Post by Frogs Hair on 2013-12-15
This problem has been reported on the Mint and Fedora operating systems as well  looks like  a specific cinnamon problem .

---

### Post by castillojdavid on 2013-12-15
Try System settings -> Themes -> Other settings an there mark the "Show icons in menus" and "Show icons on buttons" boxes. I had the same problem and both were unmarked by default, I don't know why. Worked for me, hope it works for you.

---

### Post by buzzingrobot on 2013-12-18
The Mint folks have have posted a notice ([http://blog.linuxmint.com/?p=2524](http://blog.linuxmint.com/?p=2524)) that a backport of Cinnamon 2 is now available for Mint 13, which is based on 12.04. You might try adding their backport repo and installing Cinnamon from there.

---

### Post by elkhedewy on 2013-12-24
Hello,,

i solved the cinnamon crashing problem by installing new system .

and after that i found that i still having the 1st problem which is the icons is not showed.

finally i found the solution :

1- go to system settings
2- log in to themes
3- press on other settings tab
4- choose from drop down menu in icon,, choose whatever you want 

this will show all icons again

Thanks all

---

