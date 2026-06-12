---
title: "clock syncro at boot"
date: 2005-11-15
forum: Desktop Environments
---

### Post by pirozzi on 2005-11-15
my boot process is slowed down because it try to syncronize the clock via web, but since the connection is not active it lose time before giving back "failed" as a result. how can i jump this step of booting?

---

### Post by sambler on 2005-11-15
The following should work:

System > Administration > Services

Uncheck the box next to "Clock synchronizaton service (ntpdate)".

Hope this helps.

---

### Post by pirozzi on 2005-11-15
ok, i'll try and come back to you. thanks

---

### Post by pirozzi on 2005-11-16
i've checked and i've found out that nptdate service is already not active. i'm supposed to remove the package to solve the problem? this removal migth cause other issue?

---

### Post by Lambert on 2005-11-16
I can't remember exactly and I'm not at my box to look this up. You can search for update-rc.d or _rc.d.

To find the exact command you can type in the terminal

apropos update

For more info on it look at the manpages also [COLOR="Sienna"]man updatexxxx[/COLOR]

The basic command will be something like

sudo update-rc.d <option> ntpdate

Look at the manpage for the option. It's going to be -r or remove or ?

This doesn't delete ntpdate from the system, it just removes the link which starts up the ntpdate script during boot.

---

### Post by pirozzi on 2005-11-16
someone suggest me to do: apt-get remove ntpdate. is it a good advice?

---

### Post by pirozzi on 2005-11-17
i've followed your indication. it works fine and the boot is ok now. thanks

---

