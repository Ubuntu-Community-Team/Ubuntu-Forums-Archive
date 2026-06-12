---
title: "[SOLVED] unable to run skype"
date: 2008-10-17
forum: Desktop Environments
---

### Post by techie_india on 2008-10-17
Hi
I have installed the Skype 2.0 in ubuntu 8.04 
as this:

[B]sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb 

Selecting previously deselected package skype.
(Reading database ... 160769 files and directories currently installed.)
Unpacking skype (from skype-debian_2.0.0.72-1_i386.deb) ...
Setting up skype (2.0.0.72-1) ...[/B]

When I try to run the skype , it is showing this error:

**skype: symbol lookup error: /usr/lib/libQtDBus.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv**

Can anybody help what Im doing wrong while installing it

Thanks and regards

---

### Post by pytheas22 on 2008-10-17
Are you using 64-bit Ubuntu?  If so, you need to do a few special things in order to get Skype to work, since it only provides a 32-bit installer.  There are [instructions on this page]("http://ubuntuforums.org/showthread.php?t=432295") that are easy to follow.

---

### Post by nikgare on 2008-10-17
Skype for x64 (and other arcs) is available from the Medibuntu repos here: [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by techie_india on 2008-10-18
No Im not using x64 bit.
Is there any method to install skype with all its dependecies

---

### Post by pytheas22 on 2008-10-18
If you google for '/usr/lib/libQtDBus.so.4: undefined symbol' some stuff comes up.  It seems that the problem has to do with the qt libraries--are you using KDE?  It may help (according to what I'm reading) to refresh your KDE configuration files by typing:
```

mv ~/.kde ~/.kde-OLD
```

Then log out of KDE and back in, and it may work.  NOTE: this will revert you back to the default KDE environment, removing any customizations that you've applied to your desktop (e.g. custom menus, desktop background, etc.).

Beyond that, you could always use Gnome.

---

### Post by Mazin on 2008-10-18
I recommend adding the Medibuntu repos to your system and installing Skype from there with Synaptic.  This way, all dependencies are automatically installed with Skype.  Furthermore, you may have some issues if you're using Pulseaudio, and may need the skype-oss package which Medibuntu also makes available.

Otherwise, maybe dpkg didn't install other packages that skype depends on.  Try running Synaptic and see if it tells you to install anything.

---

### Post by nikgare on 2008-10-18
> No Im not using x64 bit.

I know, that's why I said that other architectures are also available there

---

### Post by techie_india on 2008-10-20
Hi all ,
Thanks for all your sugestion 
I have added the repository:
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

Then I have searh for the skype ,
I have got as:

Skype
Skype-common
Skype-static

I have installed all these ,then it is working now.

Initially I installed only Skype.

Thanks all for your suggestions

Regards

---

