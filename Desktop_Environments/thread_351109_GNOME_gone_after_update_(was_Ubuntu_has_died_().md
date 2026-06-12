---
title: "GNOME gone after update (was: Ubuntu has died :()"
date: 2007-02-01
forum: Desktop Environments
---

### Post by chris90uk on 2007-02-01
It was installed great on my laptop. I installed the wireless doodah inside it and had wireless networking working. After that I couldn't shut down with clicking, I had to press ctrl alt backspace. Now, I can't log in. i just get a brown screen with a cursor on it and nothing else. I tried a failsafe gnome and that doesn't work. The only thing that works is failsafe terminal. I am posting this from a Mac, the only computer I have that works!

Can someone help solve the problem with my laptop? Thanks if you can!

---

### Post by tyler_roach on 2007-02-01
Go into a failsafe terminal and enter the following commands: 

sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session

Then reboot.
If that doesn't work, let me know.

---

### Post by chris90uk on 2007-02-01
> **tyler_roach said:**
> Go into a failsafe terminal and enter the following commands: 

sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session

Then reboot.
If that doesn't work, let me know.
Nope, still getting the same brown background when I try to log in.

---

### Post by tyler_roach on 2007-02-01
OK, try this:

sudo aptitude reinstall ubuntu-desktop

If that doesn't work (it didn't with me) more drastic measures may be required.

---

### Post by tyler_roach on 2007-02-01
BTW, I'm assuming you have internet connectivity?

---

### Post by chris90uk on 2007-02-01
Yes I have internet, that reinstall didn't work I'm afraid. Any other suggestions?

---

### Post by Brunellus on 2007-02-01
post a more detailed description of what you did before the fault occurred.  "some wireless doodah" isn't enough information for us to know what might have gone wrong and/or how to put it right.

---

### Post by chris90uk on 2007-02-01
> **Brunellus said:**
> post a more detailed description of what you did before the fault occurred.  "some wireless doodah" isn't enough information for us to know what might have gone wrong and/or how to put it right.

I'd already installed the drivers for the Broadcom inside the computer beforehand, and got the router. I set it all up, put in the WEP thing and it worked but I couldn't shut down properly. Now today it has packed in.

---

### Post by tyler_roach on 2007-02-01
This problem happened to me twice, and I couldn't get any constructive help: The first time I just reinstalled Ubuntu from scratch. The second time, I just dumped Gnome (that's what's not working with you) and installed KDE by doing the following:

sudo aptitude install kdm kubuntu-desktop

Then, on the login screen I chose KDE, and everything was fine (but different). Having used KDE, I actually prefer it, so I purged my system of Gnome using the following instructions:

[http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

However this is a rather drastic step (you will have to download ~400MB), so maybe someone here knows an easier solution.

---

### Post by Brunellus on 2007-02-01
thread title changed and moved to a more competent forum.  let's see who knows about this.

---

