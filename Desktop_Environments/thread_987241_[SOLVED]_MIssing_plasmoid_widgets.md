---
title: "[SOLVED] MIssing plasmoid widgets"
date: 2008-11-19
forum: Desktop Environments
---

### Post by nekoyokoshima on 2008-11-19
upgraded from ubuntu 8.04 to kubuntu 8.10 in the following way

I installed kubuntu-desktop. Then i did an apt-get dist-upgrade. All went fine.

However I notice that I have some plasmoid widget missing....namely the one which shows the desktop and the notes widget. I think something went wrong during the upgrade.

Can this be fixed?

---

### Post by nekoyokoshima on 2008-11-20
Bump

---

### Post by jacksaff on 2008-11-20
sudo apt-get install kdeplasma-addons

---

### Post by nekoyokoshima on 2008-11-20
will try it out once I get back to the office.

Cheers

---

### Post by nekoyokoshima on 2008-11-20
Duplicate

---

### Post by nekoyokoshima on 2008-11-20
installed kdeplasma-addons. Had a partial fix. However I could not add the folder view widget.

I added this to /etc/apt/sources.list

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```

Then did

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

Do this even if you have kubuntu already installed.
I then restarted the X server and voila the Folder View widget is there.

HTH other persons who hav similar problems as this is a documented bug it seems

---

