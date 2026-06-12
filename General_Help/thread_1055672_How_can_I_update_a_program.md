---
title: "How can I update a program?"
date: 2009-01-30
forum: General Help
---

### Post by arsen13 on 2009-01-30
If I have a program already installed how can i update it, using terminal?
Also when I try to remove an application from add/remove applications, e.g. Python(v2.5) it says that it cannot remove the application because one or more applications are dependent on that(i think they are not). when i installed eclipse and tried to uninstall it after a minute i've got the same error. how can i handle that and should i use that add/remove applications tool or should i rely more on downloading and installing manually?

Thanks

---

### Post by agim on 2009-01-30
Quite a bit is dependent on python 2.5. I believe the gnome gui itself is written in python 2.5. I don't know what's going on with eclipse though.

I try to avoid add/remove programs and use Synaptic (System->Admin->Package Manager). Its much more powerful and informative.

To update from the command line.

sudo apt-get update && sudo apt-get upgrade

This will update your entire system, not just one program. Though you should update ALL of your software as often as it can be updated.

---

### Post by mb_webguy on 2009-01-31
Because Ubuntu has a stepped release schedule, the software in the repositories is locked at each official release, except for security updates and fixes.  The only ways to upgrade an individual application to a newer version between Ubuntu releases are to add a Launchpad PPA that provides that application (which allows you to install and update the software just as if it were in the official repositories), use a deb package, or (if a deb is unavailable) compile from source.

---

### Post by arsen13 on 2009-01-31
I update the whole system but it didn't work I want python 2.6 but the latest version that ubuntu offers is 2.5.2 which is installed on my computer and there is no 2.6 version in the package manager also. what can I do, i have downloaded the .tgz file from python website and i can install that, and I have question about that, how can I install the program that i can run just writing the name in the command prompt, i already know how to modify the $PATH file but in order to do that i need to modify it to include every directory where each program is that i've manually installed. And also I had the same problem with eclipse, they had the older version on the package manager, so I downloaded and put it in ~/bin/eclipse.
I think having links to the programs in ~/bin directory is a way to solve running from command prompt problem but i don't know how to create links and don't know if it's a good idea.
One more think, when i update software and there is a new kernel version it downloads new version but doesn't replace and every version appears in the GRUB screen to choose, is that something that I can try to fix or it's better to leave it that way?

Thank you very much

---

### Post by mb_webguy on 2009-01-31
As far as the kernel issue...  GRUB doesn't remove the old entries so that you have the option of booting using an old kernel if a new kernel causes problems on your system.  You can edit the /boot/grub/menu.lst file to specify how many kernels are shown by typing "gksu gedit /boot/grub/menu.lst" in the terminal.  Find the line that says "howmany=all" and change "all" to how many kernels you want listed, then save and exit.  To apply the changes, type "sudo update-grub".

---

