---
title: "Using lxde on Ubuntu 14.04 LTS server and resolving minor fixes"
date: 2015-08-14
forum: Desktop Environments
---

### Post by c_xy on 2015-08-14
Hello,

We currently have lxde installed on Ubuntu 14.04.3 LTS server.

It is working okay, but there are some minor bug issues we are trying to resolve.

When I try using the update manager, I type:


```
gksudo update-manager
```


The window appears, I apply the updates and then exit. After exiting I get the following output:


> 
debconf: unable to initialize frontend: Gnome
debconf: (Can't locate Gtk2.pm in @INC (you may need to install the Gtk2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 91.)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Gnome
debconf: (Can't locate Gtk2.pm in @INC (you may need to install the Gtk2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 91.)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Gnome
debconf: (Can't locate Gtk2.pm in @INC (you may need to install the Gtk2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 91.)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Gnome
debconf: (Can't locate Gtk2.pm in @INC (you may need to install the Gtk2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 91.)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Gnome
debconf: (Can't locate Gtk2.pm in @INC (you may need to install the Gtk2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 91.)
debconf: falling back to frontend: Dialog



Also, If I use gedit

```
gedit &
```

I receive the following output:

> 

** (gedit:8029): WARNING **: Could not load theme icon user-bookmarks-symbolic: Icon 'user-bookmarks-symbolic' not present in theme

** (gedit:8029): WARNING **: Could not load theme icon user-home-symbolic: Icon 'user-home-symbolic' not present in theme

** (gedit:8029): WARNING **: Could not load theme icon drive-harddisk-symbolic: Icon 'drive-harddisk-symbolic' not present in theme





Not sure what is going on here. I don't know if this output is preventing me from doing anything. It hasn't yet. But, is this a sign of a bigger issue that needs attention. Is there a way to avoid this output. I recall in 10.04 there was a way to avoid seeing these Warnings as output. Is there a similar workaround for these issues in Ubuntu 14.04?

Any help is greatly appreciated.

Thank you for your time.

c

---

### Post by Bucky Ball on 2015-08-14
May I ask why you're launching update-manager in a terminal to update? Why not directly from the terminal?
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... will update and upgrade your current install to where it needs to be. It will NOT upgrade your release to a newer release. 

Doesn't fix your issue, but throwing it in and bumping your thread in the process. 

Do you boot to the lxde desktop? Or are you booting to a cursor? If the former, can't you get to the update manager via the applications menu? What happens if you do? If the latter, you are launching a GUI when there is no desktop running and maybe it is having issues closing the update-manager when finished because of it. Wild guess. :-k

---

### Post by c_xy on 2015-08-14
> **Bucky Ball said:**
> May I ask why you're launching update-manager in a terminal to update? Why not directly from the terminal?
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... will update and upgrade your current install to where it needs to be. It will NOT upgrade your release to a newer release. 



The main reason I launch update-manager is because....well..we've always installed updates this way.  But more importantly, we've manually installed a nvidia driver and we have to pay close attention to what updates are installed.

> 
Doesn't fix your issue, but throwing it in and bumping your thread in the process. 

Do you boot to the lxde desktop? Or are you booting to a cursor? If the former, can't you get to the update manager via the applications menu? What happens if you do? If the latter, you are launching a GUI when there is no desktop running and maybe it is having issues closing the update-manager when finished because of it. Wild guess. :-k

We boot to an lxde desktop.

This is the weird thing, I can't access the update manager (software updater) via the applications menu. I am a sudo user. However, it says I don't have required privileges to perform this action.  Is something new with 14.04? Or lxde? When I used 10.04 Gnome DE in the past, I could access update-manager via the applications window with no problems. Now, I can't do that at all despite having sudo privileges with 14.04 and lxde. This is why I've been forced to use the gksudo commands.

c

---

