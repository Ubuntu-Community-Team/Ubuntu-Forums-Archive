---
title: "without the desktop environment......"
date: 2009-08-27
forum: Desktop Environments
---

### Post by u_kapaley256 on 2009-08-27
Hi,
i have a somewhat old pc with 1.6ghz pentium d and 512 mb ram
i am using intrepid.
sometimes running firefox with one or two more apps takes the life out of it
i'd rather that i run some lightweight thing on it rather than see its struggle 
so i want to know whether its fine to remove the GNOME desktop environment
would i be able to use the same apps??

---

### Post by NoaHall on 2009-08-27
Remove it and use what instead? xubuntu?

---

### Post by XubuRoxMySox on 2009-08-28
There are plenty of lightweight Linux distros out there. One that is awesome on lower spec hardware and has no desktop environment at all (just the Openbox window manager but it's awesome) is the Ubuntu-based [Crunchbang Linux]("http://crunchbanglinux.org"). I prefer a desktop environment, but it must be lightweight and super-simple ("kid-friendly"). I chose [LXDE]("http://lxde.org") because it perfectly fits the bill.

Ubuntu will run light and fast using it:

```
sudo apt-get install lxde
```

To install it, and use

```
sudo apt-get purge ubuntu-desktop
```

to remove the more resource-hungry Ubuntu default.

Log out. When you log back in, under the Options panel in the lower-left corner, choose LXDE for your next Session and give it a spin. It's lighter and faster than Xubuntu.

I use a [minimal Ubuntu]("https://help.ubuntu.com/community/Installation/MinimalCD") install with LXDE and my favorite aplications. It rocks!

-Robin

---

### Post by snowpine on 2009-08-28
> **u_kapaley256 said:**
> Hi,
i have a somewhat old pc with 1.6ghz pentium d and 512 mb ram
i am using intrepid.
sometimes running firefox with one or two more apps takes the life out of it
i'd rather that i run some lightweight thing on it rather than see its struggle 
so i want to know whether its fine to remove the GNOME desktop environment
would i be able to use the same apps??

Try a different web browser instead of Firefox: Opera, kazehakase, epiphany-browser, midori, etc.

---

