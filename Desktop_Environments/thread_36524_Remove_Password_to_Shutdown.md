---
title: "Remove Password to Shutdown?"
date: 2005-05-23
forum: Desktop Environments
---

### Post by sebflipper on 2005-05-23
Currently I don't have any need for the password features, as all I want is basic surfing, IM and word processing machine, which can be turned on and off without any passwords.

I have installed Ubuntu base files (using the server setup) and I have the Xfce4 desktop installed. I have set gdmsetup to auto logon the default user, but when I try to shutdown or reboot I am prompted for my password, is there any way of disabling this?

---

### Post by JonahRowley on 2005-05-23
You can do this with sudo.  First, open up your sudoers file:
```
sudo visudo
```
Add a line that will allow your user to run the shutdown (or whatever command xfce needs to run to shut down) without a password.  The line would look something like this:
```
%admin  ALL=NOPASSWD: /sbin/shutdown
```
That will give everyone in the admin group the ability to shut down the machine via sudo without entering a password.

Hope this helps.

---

### Post by sebflipper on 2005-05-23
Humm I have just added that to my sudoers file and restarted (with password), but I am still prompted for a password when Ubuntu loads back up again.

I have tried changing **%admin** to **%user** and even **%gdm**, but I am still constantly prompted for a password to shutdown.

Any idea what to use to allow any user or guest to shutdown/reboot?

---

### Post by JonahRowley on 2005-05-23
Wait, do you want to do this from XFCE or GDM?

---

### Post by sebflipper on 2005-05-24
[QUOTE=JonahRowley]Wait, do you want to do this from XFCE or GDM?[/QUOTE]
I am trying to shutdown from XFCE4, using the little shutdown icon in the bottom right menu.

Also because the machine just boots up and automatically logs on without a password, what group do they get assigned to?

---

### Post by Burgundavia on 2005-05-24
Can you file a bug report about that here:
[https://launchpad.ubuntu.com/distros/ubuntu/+bugs](https://launchpad.ubuntu.com/distros/ubuntu/+bugs)

Corey

---

