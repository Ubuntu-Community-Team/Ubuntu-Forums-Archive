---
title: "[SOLVED] New Ubuntu 8.10 install, can't Activate restricted drivers."
date: 2009-01-10
forum: General Help
---

### Post by nerd0795 on 2009-01-10
Just installed Ubuntu 8.10 through Wubi (I did through Wubi, since incase Ubuntu doesn't work well on my new laptop).  The thing is, I need to install the restricted driver for graphics.  But it's not letting me.  I have two choices Nvidia accelerated graphics drivers 173 and 177.  I tried 177 by clicking on it then pressing activate.  But it says "Downloading 0%" then closed.  Not telling me anything else.  Can anyone help me.  My graphic card is a Nvidia Geforce 9100M G

---

### Post by Sherlock Holmes on 2009-01-10
I'm not quite familiar with wubi, but can you access internet from Ubuntu?

---

### Post by nerd0795 on 2009-01-10
> **Sherlock Holmes said:**
> I'm not quite familiar with wubi, but can you access internet from Ubuntu?

I can access the internet.  I checked the Synpatic Package Monitor and everything under the name "Nvidia" is installed.  Though I can't activate the driver.

---

### Post by Sherlock Holmes on 2009-01-10
Hm, I know that it usually comes up if you "sudo apt-get update"

---

### Post by nerd0795 on 2009-01-10
> **Sherlock Holmes said:**
> Hm, I know that it usually comes up if you "sudo apt-get update"

What do u mean by that?  I know it' s aterminal command but what do you want me to do?

---

### Post by Sherlock Holmes on 2009-01-10
open up terminal and type in "sudo apt-get update"

---

### Post by nerd0795 on 2009-01-10
> **Sherlock Holmes said:**
> open up terminal and type in "sudo apt-get update"

Hmm.. when it's done I think it's going to work.  I think when it installed it never set the repositories.

EDIT:  Ughh my internet's average speed on Ubuntu is about 30kb/s  it should be 70kb/s  maybe it's because the server's are busy

---

### Post by hotweiss on 2009-01-10
> **nerd0795 said:**
> Hmm.. when it's done I think it's going to work.  I think when it installed it never set the repositories.

EDIT:  Ughh my internet's average speed on Ubuntu is about 30kb/s  it should be 70kb/s  maybe it's because the server's are busy

Change to a different server. I use rafal.ca which is the fastest for me.

System -->  Administration --> Software Sources

---

### Post by nerd0795 on 2009-01-10
> **hotweiss said:**
> Change to a different server. I use rafal.ca which is the fastest for me.

System -->  Administration --> Software Sources

Yay, now it's faster too bad Ubuntu crashed D:

I need to get those drivers.

---

### Post by nerd0795 on 2009-01-10
It got a kernal panic on reboot.  Rebooted again it worked.  Now the window  saying downloading and installing stays open and stuck at 0%

---

### Post by domoso on 2009-01-10
Are you getting any error messages besides the stuck progress bar? What happens if you try to install something else, like an application? Does that progress?

---

### Post by Sherlock Holmes on 2009-01-10
I think he/she means the sudo apt-get update.

---

### Post by nerd0795 on 2009-01-10
I was able to install other applications.

EDIT:  I have enabled third party sources just to check

---

### Post by nerd0795 on 2009-01-10
Opened Nvidia settings under system > admin which was installed by default and this message appeared:

> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

---

### Post by nerd0795 on 2009-01-10
Whoa?  Now it say's it's activated.  Yet unfortunately, the graphics arn't working right.  I barely can handle that the screen has to refresh  just to change screens.   If it's still like this when I restart I'll uninstall it.

---

### Post by nerd0795 on 2009-01-10
Yay, now it stopped flickering, it's higher resolution and desktop effects work.  Weird.

---

### Post by domoso on 2009-01-10
The failed attempts could have hosed the installation with a partial install. You could try apt-get install -f to fix dependency issues. You could try dpkg --purge <package name> to remove the package and configuration files. And then try to install it again. You could try dnloading the package manually and installing it by hand (double clicking it should bring up the gnome package manager and install it).

---

### Post by hotweiss on 2009-01-10
> **nerd0795 said:**
> It got a kernal panic on reboot.  Rebooted again it worked.  Now the window  saying downloading and installing stays open and stuck at 0%

sudo apt-get update

---

### Post by nerd0795 on 2009-01-10
I did the sudo apt-get.  After I went to the restricted drivers and pressed activate selecting the newest one and left it on that screen for a while.  Then it said it activated.  Now my drivers is working.  Yay 3D cube.

---

