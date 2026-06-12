---
title: "Switching Users"
date: 2006-06-27
forum: Desktop Environments
---

### Post by simonn on 2006-06-27
I am posting this in case someone else has this problem. It is unlikely if you have been using modern gnome systems since day dot, but if you have used other distros and migrated users and data to Ubuntu (like me) then it is possible.

We had user switching setup and working in Breezy. It stopped working in Dapper because the list brought up when the switch user button was pressed when the screen was locked was empty. 

I could not find anything searching t'interweb so ended up looking in the source code to find the solution to the problem. This does not seem to have been documented anywhere.

 - With Gnome 2.14 gnome screensaver was introduced, replacing xscreensaver

 - gnome screensaver gets the list of users than can be switched to from Fast User Switcher Applet (FUSA). NOTE: gnome screensaver does not depend on FUSA at the source or package level, for valid reasons. xscreensaver simply opened a new login screen (which is also what gnome screensaver does dispite the fact that you have to select a user).

 - The list provided by FUSA will include currently logged in users and/or users that have their names in a comma seperated list set using the parameter *Include* and have numerical uids greater than or equal to the value set by the parameter *MinimalUID* in /etc/X11/gdm/gdm.conf.

e.g. in /etc/X11/gdm/gdm.conf

```

Include=user1,user2,user3
MinimalUID=1000

```

Will cause user1, user2 and user3 to be listed as long as their uid is greater or equal to 1000.

My problem was two-fold: 

 - I did not have FUSA installed in Breezy, as it was not needed, so when I upgraded to Dapper it was not installed either. This meant that gnome screensaver was unable to obtain a list of users.

 - The two users that use gnome (there are several physical users who only log in via sftp) had uids of less than the default value of MinimalUID which is 1000.

---

