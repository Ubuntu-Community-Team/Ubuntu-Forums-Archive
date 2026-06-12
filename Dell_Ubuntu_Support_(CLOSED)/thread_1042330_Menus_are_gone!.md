---
title: "Menus are gone!"
date: 2009-01-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abscess on 2009-01-17
Hi there

Ok, bottom line, I have messed up Ubuntu 8.10! My Dell M1330 was originally with MS Vista, but I soon made a dualboot to Ubuntu.

And everthing has worked properly for half a year now, until today when I desided to uninstall mail client Evolution.....

I used the Package Manager, searched for Evolution and uninstalled a couple of packages used by Evolution.. I remember I got a question about dependencies, and I removed all of them without even reading what it was all about..

After reboot I get automatically logged in as usual, but there are no menus at all! I can right click the desktop, change wallpaper, switch between workspaces etc. It all seems to be working properly except.. Yes, no menus, no buttons anyware! All I have is the wallpaper.

Searching for a genious out there who can tell me what I might have uninstalled wich I should not, and how to get it right again?

---

### Post by Ben Webber on 2009-01-17
Evolution is really tied into the GNOME desktop. If you remove the packages evolution-data-server and evolution-data-server-common, you can essentially cripple GNOME.

When you boot up your machine, there should be a "recovery" option. Select that and you will boot into the terminal.

Once there, reinstall those two packages:

```
sudo apt-get update
sudo apt-get install evolution-data-server evolution-data-server-common
```

You should be able to get back to GNOME by typing **startx**.

---

### Post by abscess on 2009-01-17
I will try that right away! Thank you Ben Webber :)

---

### Post by abscess on 2009-01-17
I succesfully did as you wrote, no error messages or anything, but still, all I have is the wallpaper.. :confused:

Any other ideas?

---

### Post by Ben Webber on 2009-01-17
You removed only Evolution-related packages, correct?

Afterward, did you do an **apt-get autoremove**?

If you removed only Evolution-related packages, then didn't do an **autoremove**, I can't imagine why it didn't work for you.

---

### Post by abscess on 2009-01-17
Correct, only Evolution-related packages. As far as I know, that is. I dont know wich dependencies that got uninstalled with it.

I used the Package Manager, didnt run any commands manually. I searched for "Evolution" --> Uninstall and some dependecies got lost as well.

---

### Post by Ben Webber on 2009-01-17
Try doing the same thing I mentioned with Evolution Data Server, but with **gnome-panel**. I don't see why **gnome-panel** would be removed, but it is worth a shot!

```
sudo apt-get install gnome-panel
```

After that, I'm afraid I'm out of ideas :(.

---

### Post by abscess on 2009-01-17
I will try that later on. Thank you so much for the help, Ben Webber!

Hopefully it will be OK :)

---

### Post by abscess on 2009-01-17
"sudo apt-get install gnome-panel"

WORKED LIKE A CHARM! Everything is back to normal!

Thank you so much!! :P:):P

---

### Post by Ben Webber on 2009-01-17
No problem. I have a feeling it was still the Evolution packages, though. I think instead of just starting X Windows Server (the GNOME desktop) with **startx**, a full restart was required. Thus, the reappearance of your menus when you rebooted having installed **gnome-panel**.

Glad everything worked out.

---

### Post by WEdgemond on 2009-01-22
I am having the same problems with missing menus on the desk top. Also top and bottom panels are missing. I removed Evolution packages not realizing the consequences.:(

I have tried all of the above and still no luck. There is some error messages about US archives not being loaded and suggest running apt-get update, tried and no results. Anyone have any more ideas. I am new to Linux and Ubuntu.

Is there someway to get xterm with out the menus.

Dell installed Ubuntu 8.04 on Studio 1535.:(

---

