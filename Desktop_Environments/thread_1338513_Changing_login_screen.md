---
title: "Changing login screen"
date: 2009-11-26
forum: Desktop Environments
---

### Post by kestrel1 on 2009-11-26
Having installed Xubuntu I am not yet used to it as I am with Ubuntu.
When I get the login screen up I have to click on a button that says login, then enter my username & password one after the other.
In Ubuntu 9.10 I can just click on my username & enter my password to login. I know this is possible in Xubuntu 9.10 as I have another system running it that this is working on. How can I change this on my current box.
Cheers

---

### Post by kestrel1 on 2009-11-26
Anyone?

---

### Post by slumbergod on 2009-11-26
By default, my Xubuntu shows the user list you are familiar with in Ubuntu. 

Many of us disabled it because it is a security risk in many situations (sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true). 

You should see the user list with at least one default user and a guest account. Maybe you could try the above command with false.

---

### Post by kestrel1 on 2009-11-26
> **slumbergod said:**
> By default, my Xubuntu shows the user list you are familiar with in Ubuntu. 

Many of us disabled it because it is a security risk in many situations (sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true). 

You should see the user list with at least one default user and a guest account. Maybe you could try the above command with false.

Hi, thanks for the suggestion, but this didn't work. I can't understand why I didn't get the user list as default, as the other system that I installed did. I used the same disk etc. any other suggestions?

---

### Post by kestrel1 on 2009-11-27
There must be a way to do this. It can be achieved in Ubuntu by using something like the GDM settings manager or something like that. The same app in Xubuntu does not give any options though. I have tried installing different packages to do with GDM, but none of this has given m e anything useful. I am getting close to re-installing unless I can figure this out soon. Maybe the install will go right if I do it again.
If you have any ideas I would appreciate hearing them within the next day or so or a re-install will take place.

---

