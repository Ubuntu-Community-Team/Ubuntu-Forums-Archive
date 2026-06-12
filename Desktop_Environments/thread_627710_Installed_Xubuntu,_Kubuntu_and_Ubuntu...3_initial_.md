---
title: "Installed Xubuntu, Kubuntu and Ubuntu...3 initial problems"
date: 2007-11-30
forum: Desktop Environments
---

### Post by visiblesun on 2007-11-30
Hi, I'm relatively new to Ubuntu (or maybe a slow learner, since I've been with it over a year now)...I have a tx1000 hp laptop, with Ubuntu and Vista installed. I recently added Kubuntu desktop and Xubuntu desktop, which, although they work fine, have given me these 3 problems:

1) The login screen has defaulted to xubuntu (I'd prefer the old ubuntu, as it was originally) - how do I get it back?

2) The load screen before the login has defaulted to kubuntu (again, I'd prefer the old ubuntu) - how do I get it back??

3) I can't access my vista partition from any of the desktop environments - how do I get it back???

Thanks.

---

### Post by vikram on 2007-11-30
not sure what you mean by load screen. if you have all three desktop environments installed you can choose which one to use for a session. 

when you log in you should have a setting for session type along with the username and password. choosing KDE will bring up kubuntu, GNOME ubuntu and Xfce the xubuntu.

for the vista partition print the output of 

sudo fdisk -l

and 

mount

and 

cat /etc/fstab

maybe its only a mount issue.

---

### Post by Happy_Man on 2007-11-30
For your login screen issue: run ```
sudo dpkg-reconfigure xdm
``` and choose gdm. Then press ctrl-alt-backspace. It should load up the Ubuntu default login screen.

---

### Post by TeaSwigger on 2007-11-30
Don't worry, nobody knows everything and not many know very much about much. Or something like that. :)

> **visiblesun said:**
> Hi, I'm relatively new to Ubuntu (or maybe a slow learner, since I've been with it over a year now)...I have a tx1000 hp laptop, with Ubuntu and Vista installed. I recently added Kubuntu desktop and Xubuntu desktop, which, although they work fine, have given me these 3 problems:

1) The login screen has defaulted to xubuntu (I'd prefer the old ubuntu, as it was originally) - how do I get it back?

2) The load screen before the login has defaulted to kubuntu (again, I'd prefer the old ubuntu) - how do I get it back??

3) I can't access my vista partition from any of the desktop environments - how do I get it back???

Thanks.

Ok let's see. It might help you make sense of it to explain:

There is GRUB (the boot loader you see after starting). Then you have the usplash that displays while ubuntu is booting, the one with the progress bar. Then you have the login screen. You can choose which desktop to use there. Then you have the splash screen as the chosen login loads. Whew.

After GRUB, the boot's "managed" by the "desktop manager." You have two of them now. One is called GDM (gnome / ubuntu and xubuntu) and the other is called KDM (kde / kubuntu). Each of these has their own options for what usplash, login screen and splash you want to use.

So, to select, follow the suggestion from Happy_Man or it can always be changed later by modifying the /etc/X11/default-display-manager file. For KDM, the file should read /usr/bin/kdm. For GDM, the file should read /usr/sbin/gdm. You might go with GDM.

And you probably have 3 usplash screens to chose from, ubuntu, kubuntu or xubuntu. To change the usplash, run in a terminal:

```
sudo update-alternatives --config usplash-artwork.so
```

Choose usplash, you'll see the one for ubuntu.

Then run in a terminal:

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

You can do that whenever you like if you want to change again later. When that's done, you might chose to reboot and check if all's in order. To change the login and splash screens, go into Gnome / ubuntu or xubuntu and pick the ones you want. Hope that all makes sense.

---

### Post by TeaSwigger on 2007-11-30
> **visiblesun said:**
> 3) I can't access my vista partition from any of the desktop environments - how do I get it back???

That can be more complicated... hm not sure I know the answer for that. So you were accessing it fine before and then you added these packages and poof? I guess first thing to check, is the Vista partition listed in the file /etc/fstab ? It'd be noted as 'ntfs'.

---

