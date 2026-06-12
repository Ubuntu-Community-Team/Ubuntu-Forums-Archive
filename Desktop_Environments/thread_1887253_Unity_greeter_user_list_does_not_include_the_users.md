---
title: "Unity greeter user list does not include the users' pictures/photos"
date: 2011-11-26
forum: Desktop Environments
---

### Post by rpremuz on 2011-11-26
In Ubuntu 11.04 the login screen has the list of users accompanied with the pictures each user set in the properties of his or her user account (System Settings -> User Accounts).

Ubuntu 11.10 uses LightDM login manager with the Unity greeter (see [https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes](https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes)) which does not show the users' pictures.

Ubuntu 11.10 help has a chapter titled "Change your login screen photo" which says: "When you log in or switch users, you will see a list of users with their login photos." So, is there a way to show the users' pictures/photos in Unity greeter?

-- rpr.

---

### Post by Frogs Hair on 2011-11-26
As far as I can see the user picture changes in the session menu , but not the login screen .

---

### Post by rpremuz on 2012-05-20
Unity Greeter v. 0.2.8 (in Ubuntu 12.04) still does not show the user picture specified in the User Account tool.

On the other hand, Unity Greeter has now a new default feature: the background picture of the login screen corresponds to the desktop background (AKA wallpaper) of the user selected on the users list (see [http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/64002#64002](http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/64002#64002)).

To me it's an odd decision to implement the second feature and not to implement the first one.

---

### Post by nll on 2012-05-20
I also think this is an important missing feature. You could file a bug in Launchpad requesting that and try to get some "affects me too" votes, or send a message to the Unity Design mailing list to see what the developers think about this idea.

---

### Post by nll on 2012-05-20
> **rpremuz said:**
> On the other hand, Unity Greeter has now a new  default feature: the background picture of the login screen corresponds  to the desktop background (AKA wallpaper) of the user selected on the  users list (see [http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/64002#64002](http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/64002#64002)).

But that only happens when the user chooses a background from the default list, not a custom one.

---

### Post by aoakley on 2012-08-26
I have reported this as a bug. Replying here as this thread is showing up well on Google for searches involving Greeter, User Pictures, User Photos and similar.

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1041897](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1041897)

"Unity Greeter is not accessible to illiterate / preschool users"

My eldest daughter was brought up on Ubuntu 10.04 LTS. She was given her own account from around the age of three and logged in (passwordless) by clicking on her photo, since at the time she could not yet read.

My toddler twins will be three next week. I have upgraded to 12.04 LTS and it would appear that the replacement for GDM, the Unity Greeter, does not support user pictures/photos. The user has to be able to read their user name to log in.

(In case you're wondering what a preschooler does with Ubuntu, after login my children are presented with a highly simplistic OpenBox interface with a selection of desktop icons for Tux Paint, Tux Racer, Cheese, BBC CBeebies website etc.)

---

### Post by rpremuz on 2012-08-26
aoakley, I started this thread for similar reasons :-)

My nephew's first PC was also Ubuntu (8.10). At that time he was 3 years old and he liked PySyCache and some activities from GCompris suite.
At the age of 4 he was able to log on on his own by clicking his picture and typing a password (a pattern of keys).

With Ubuntu 11.10 things changed and I was not able to put his picture on the login screen :-(. Fortunately he had learned the first letters at that time and was able to recognize his name on the screen.

---

