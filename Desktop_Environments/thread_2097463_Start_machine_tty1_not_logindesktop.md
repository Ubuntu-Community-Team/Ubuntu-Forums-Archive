---
title: "Start machine: tty1 not login/desktop"
date: 2012-12-23
forum: Desktop Environments
---

### Post by opholdings on 2012-12-23
Installed Gnome in 12.04. Was working fine. Now every time the machine starts, the tty1 appears.

Can access the desktop with:
sudo /etc/init.d/gdm restart

Can access the desktop without gnome with
xstart

Tried deleting .Xauthority and will occassionally work.

What can I do to have the desktop automatically appear when the machine is turned on?

OK.

Tried this and now the desktop is not working. Cannot right click or copy files to the desktop. All desktop icons are in the desktop folder.
	

To update to Gnome 3.6, you need to add these two PPAs:

sudo add-apt-repository ppa:ricotz/testing
sudo add-apt-repository ppa:gnome3-team/gnome3

Then run

sudo apt-get update
sudo apt-get upgrade

Still not working. Any ideas to get back to the normal login screen and desktop?

---

### Post by ibjsb4 on 2012-12-23
From: ppa:ricotz/testing

=== WARNING ===
Make sure you know what you are doing! You are getting bleeding edge snapshots!
You should have a stable experience most of the time, but there will be problems!

Using this ppa could break your system or make it unstable!
So you need to know how to repair it using something like ppa-purge.

---

### Post by opholdings on 2012-12-23
Solved.

Thanks for the direction.

sudo ppa-purge ppa:ricotz/testing

The tty1 login at startup was solved by changing nvidia drivers.

---

