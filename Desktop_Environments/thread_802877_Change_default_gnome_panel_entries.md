---
title: "Change default gnome panel entries"
date: 2008-05-21
forum: Desktop Environments
---

### Post by sleepkreep on 2008-05-21
I'm deploying GNOME across about 50 nodes with approximately 500 user accounts using NX and local boxes on the floor of the lab.  Having so many users causes problems when the fast-user-switch-applet loads.  So I removed the package.  However, now when a user logs in for the first time, they get an error saying the fast-user-switch-applet is not available and asks if they want to remove it.  Since many of the users have never used Linux before I need to completely remove the applet from the default panel configuration.  I removed the entries from /etc/gconf/schemas/panel-default-setup.entries but it still get loaded by default.  How do I remove it from the system's default configuration?

---

### Post by Keymaster on 2008-10-10
When I wanted to remove the applet it said I had to remove the whole graphics environment (ubuntu-desktop).  How did you remove the applet?  I'm also curious as to the answer to your original question.

---

### Post by sleepkreep on 2008-10-10
I went ahead and let it remove the ubuntu-desktop package.  It's only a meta package and contains nothing important, only dependencies. The default panel configuration can be changed by editing the /etc/gconf/schemas/panel-default-setup.entried file.  Basically, I got the panel the way wanted, then ran 'gconftool-2 --dump /apps/panel > default_settings.xml'.  Then I copied the default_settings.xml file to /etc/gconf/schemas/panel-default-setup.entries .   All brand new gnome logins have these settings by default.

---

### Post by Keymaster on 2008-10-10
So with the steps in your last post fast user switching applet can't be added to users panels?

---

### Post by sleepkreep on 2008-10-10
With my last post, the applet won't be added to the user's panel by default.  If you do not remove the fast-user-applet package, users will still be able to add it themselves.  Obviously, if you do remove the package, users will not be able to add it.

---

### Post by Keymaster on 2008-10-10
Actually another post in the forums (sorry I lost the link) showed that a program called pessulus could do the job.
```

sudo apt-get install pessulus
sudo pessulus #the interface is easy to figure out
sudo apt-get remove pessulus (as it is no longer needed, and wastes space
sudo reboot #let all changes take effect as /etc/init.d/gdm restart didn't make a difference

```
Thanks for the quick reply though

---

