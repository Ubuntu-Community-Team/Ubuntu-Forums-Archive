---
title: "User logins LXDE"
date: 2011-04-27
forum: Desktop Environments
---

### Post by Zaytuun on 2011-04-27
I've just installed lubuntu onto my desktop and I'm loving it so far with one exception:

The login screen. You have to manually type in the username for the user you wish to login as. Is there a way to set up the login so it lists the users for you, so you can just click the user and type in the password like regular old GNOME Ubuntu? I've searched but found nothing. 

Thanks in advance!

---

### Post by cavalier911 on 2011-04-27
Lubuntu's lxdm has no user list feature.
I consider it a security vulnerability and always disable it in Ubuntu's gdm.
Let them figure out the** username **and password, not just the password.

---

### Post by Zaytuun on 2011-04-27
> **cavalier911 said:**
> Lubuntu's lxdm has no user list feature.
I consider it a security vulnerability and always disable it in Ubuntu's gdm.
Let them figure out the** username **and password, not just the password.

I see your point, but I find it a bit inconvenient and I am used to Gnome's login manager. Hopefully whenever a new version of LXDM comes out it'll have a user list feature. Thanks for the info.

---

### Post by Copper Bezel on 2011-04-27
Couldn't you just install gdm and launch from there? It wouldn't require installing Gnome. Hell, it's the default login screen for XFCE and Xubuntu in Ubuntu, despite the fact that there's an xfdm, too.

---

### Post by Zaytuun on 2011-04-27
> **Copper Bezel said:**
> Couldn't you just install gdm and launch from there? It wouldn't require installing Gnome. Hell, it's the default login screen for XFCE and Xubuntu in Ubuntu, despite the fact that there's an xfdm, too.

Can anyone second this? Sample space of two please lol.

---

### Post by carolinason on 2011-09-09
i agree, it is not a security issue here and i would rather not install gdm.

---

### Post by kerry_s on 2011-09-09
> **Zaytuun said:**
> Can anyone second this? Sample space of two please lol.

Yes, you can install gdm. It will ask which you want to use, select gdm

---

### Post by carolinason on 2011-09-12
lxdm does have a user list feature. however, there is a bug in the current version. this link describes how to edit the lxdm conf file to enable the user list. when i checked mine it was already configured for the user list, but it is not showing due to the bug.

[http://askubuntu.com/questions/39613/how-to-enable-user-list-in-lxdm-login-manager]("http://askubuntu.com/questions/39613/how-to-enable-user-list-in-lxdm-login-manager")

synaptic wanted to install several sound server packages along with gdm, so i didn't install it.

bug is here [https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/666590]("https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/666590")

---

### Post by amjjawad on 2011-09-22
> **carolinason said:**
> i would rather **not **install gdm.

Ditto.

---

### Post by lat00 on 2012-06-25
Does anyone followed up this issue?
The bug page looks like died.
I would like to have the user chooser! Unfortunately not good enough to recompile the code by myself. any help?

---

