---
title: "Logout checkboxes not available"
date: 2006-04-30
forum: Desktop Environments
---

### Post by v_oo_v on 2006-04-30
Hello All,

When I logout, the logout menu does not show checkboxes for the available options (see attachment):

[http://photos1.blogger.com/blogger/7946/1139/1600/logout.jpg](http://photos1.blogger.com/blogger/7946/1139/1600/logout.jpg)

The only relation I could find is that I just installed some GDM greeter themes from [www.gnome-look.org](www.gnome-look.org). 

Even if I set the default "Human" theme and logout screen does not change this "buggish" behaviour.

Curiously, if i check the place where checkboxes are supposed to be, actions are performed properly (Thus Logout, Shutdown, Restart or Hibernate).

Any idea about this?.

Thanks in advance.

---

### Post by louis_nichols on 2006-05-01
I had a pretty similar issue with greeter themes and, unfortunatelly, I never was able to solve mine. So everything else is fine, except these widgets? Did you try something like:

```
sudo dpkg-reconfigure gdm
```

This should bring everything to default (assuming, of course, that your installing the themes is really the culprit).

As for installing eye-candy, I recommend [gnome-art]("http://packages.ubuntu.com/breezy/gnome/gnome-art") and [gcursor]("http://packages.ubuntu.com/breezy/gnome/gcursor").

---

### Post by BORTKOMMEN on 2006-05-16
No checkboxes for me either. I have changed display manager to KDM and then back to GDM with the command "sudo dpkg-reconfigure gdm", since then the checkboxes vanished.

I have Ubuntu, Kubuntu, and Xubuntu installed on my computer.

---

