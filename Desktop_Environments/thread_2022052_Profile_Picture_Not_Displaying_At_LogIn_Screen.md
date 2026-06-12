---
title: "Profile Picture Not Displaying At LogIn Screen"
date: 2012-07-10
forum: Desktop Environments
---

### Post by egarza on 2012-07-10
I have searched and searched and searched.
Running Xubuntu 12.04 with LightDM.

I have my .face picture saved in /home/<username>.
I have a picture saved as /var/lib/AccountsService/icons/<username>.
My /var/lib/AccountsService/users/<username> config file has the following line:
Icons=/var/lib/AccountsService/icons/<username>.
The profile picture shows up if I go to System->Users And Groups.

I have tried saving the picture as both 96x96 and 96x72.

For whatever reasons it will not show up on the login screen.
Any ideas?

---

### Post by freedmax on 2012-12-06
> **egarza said:**
> I have searched and searched and searched.
Running Xubuntu 12.04 with LightDM.

I have my .face picture saved in /home/<username>.
I have a picture saved as /var/lib/AccountsService/icons/<username>.
My /var/lib/AccountsService/users/<username> config file has the following line:
Icons=/var/lib/AccountsService/icons/<username>.
The profile picture shows up if I go to System->Users And Groups.

I have tried saving the picture as both 96x96 and 96x72.

For whatever reasons it will not show up on the login screen.
Any ideas?

For lightdm-gtk-greeter (Xubuntu 12.04, Lubuntu 12.04 and others):

1) put your small .face image in your /home/username (if it's not already)

2) edit the file /usr/share/lightdm-gtk-greeter/greeter.ui (with root permissions) and modify the line

<property name="fixed_height_mode">True</property>

in

<property name="fixed_height_mode">False</property>

3) logout

---

### Post by Merrattic on 2012-12-09
Thanks freedmax, this works well :)

---

