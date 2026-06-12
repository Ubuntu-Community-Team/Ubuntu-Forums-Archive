---
title: "How do I get out of kubuntu?"
date: 2010-10-03
forum: Desktop Environments
---

### Post by hortstu on 2010-10-03
I installed the kubuntu desktop.  I logged out of my session and restarted and I no longer have the session option at the bottom of the log in screen.  How do I switch back to gnome?


I'm not quite used to it and for efficiencies sake I'd like to stick with gnome while working, at least until I learn KDE.

---

### Post by akwatve on 2010-10-03
Are sure ubuntu-desktop was not uninstalled while you installed kubuntu-desktop ?
EDIT : You can check this by going to adept/synaptic and verifying if ubuntu-desktop is still installed.

---

### Post by hortstu on 2010-10-03
It seems like that's a possibility.  I didn't select any option for that though.  How do I run them both?

---

### Post by hortstu on 2010-10-03
I don't know my way around this desktop.

how do I get to adept/synaptic?

I went to the software center and typed in gnome.  I had a lot of stuff installed but the GNOME desktop environment (w/ extra components) was not installed.

---

### Post by hortstu on 2010-10-03
I tried to install the gnome desktop but it won't let me saying it can't satisfy the dependencies or something.  

This is kinda getting to me.  Any suggestions on how to get back to gnome?  If I can only use one I'd prefer gnome at this point.

---

### Post by wilee-nilee on 2010-10-03
In a terminal in Ubuntu.
```
sudo apt-get install ubuntu-desktop
```

Here is a link on removing whole desktops make sure you choose the correct version, e.g. the distro you have installed to remove.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

You can have multiple desktop choices at login you click the choice form a list at the bottom of the login screen after you click the user before entering the password.

---

### Post by hortstu on 2010-10-03
Thanks,  I appreciate the help.  This is what I get when I enter the suggested command.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 libparted0 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Does this mean I've got gnome in here somewhere.  Why don't I have the option at the login screen?

---

### Post by wilee-nilee on 2010-10-03
At the login screen hit your name and then click the tabs at the screen bottom and choose the Ubuntu desktop, put your pass word in and have fun. Use the link to remove Kubuntu if needed , but be aware that it is a long list that may remove stuff you want so just understand how it works, and if you don't somebody on the forum will probably know.

---

### Post by hortstu on 2010-10-03
Wow thanks man I am dense.  I don't really want to uninstall KDE I want to learn it because I'm interested in having multiple unique desktops, but I didn't want to quit gnome til I've got it down.  Thanks for all the help.

---

### Post by wilee-nilee on 2010-10-03
> **hortstu said:**
> Wow thanks man I am dense.  I don't really want to uninstall KDE I want to learn it because I'm interested in having multiple unique desktops, but I didn't want to quit gnome til I've got it down.  Thanks for all the help.

Now you know, ;) there are two other desktops used as well Xubuntu a little lighter then Ubuntu and lxde a lot lighter. The only thing is that as you may notice already the overlapping programs show up in each desktop.

---

