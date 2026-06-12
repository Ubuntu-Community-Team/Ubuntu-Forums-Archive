---
title: "Associate USB drive name/uuid with certain startup apps?"
date: 2010-08-23
forum: Desktop Environments
---

### Post by mdog on 2010-08-23
I have a Nook ebook reader and would like it to automatically open a certain application when I plug it in.

As standard it just opens a nautilus file browser.

I cannot find any settings that will let me associate a drive name/uuid with a certain application and google results came up saturated with how to make bootable USB drives.

The only solution I actually found was to make a .autorun script in the root of the drive to start my application, but it still requires user interaction and is not ideal since I would like to implement this across several machines with different users/applications.

---

### Post by diesch on 2010-08-23
One way is to write a udev rule to start the app. But as udev starts prograsm as root you may need to switch to another user first and maybe clone parts if its environment to make the app running. Usually that's quite ugly and a potentional security risc.

The better way is to have a program in the user's session that listens to dBus events and starts the app on  the one that happen when you insert that special stick. But as far as I know there is no ready made program for that so you need to do a little bit programming (shouldn't be much difficult in most languages that have bindings for DBus, like e.g. Python).

---

