---
title: "Exiting vim freezes compiz"
date: 2011-05-01
forum: Desktop Environments
---

### Post by AndreasZ on 2011-05-01
Hi everyone.

I read a lot of people warning others about upgrading to 11.04, because of the more or less beta unity environment, but since I'm on LXDE/Compiz, this stuff wasn't supposed to affect me in any way.

But now there are some very weird bugs going on. Exiting vim in a terminal freezes my compiz. It gets stuck at 100% cpu load. I can still switch to TTY1 and kill compiz and restart gdm along with it and it works again, but this kind of a bug is really creepy. To rule out any sort of lxde-terminal related error, I installed vim-gtk and played around with it. :q results in a complete Desktop Environment freeze.

I can however use vim on TTY without any sort of weird behavior, also with compiz running in the back. Being used to vim, I don't want to switch to gedit or any sort of other moronic editor, so please spare me with those sorts of suggestions.

After all, this release seems to me a lot more beta than all the others i experienced so far. It messed up a lot of my config files without even asking, I had to reconfigure usbmount, get enhanced zoom desktop, and more importantly, mouse-zooming reactivated, which has for some reason been deactivated, and so on.

But one thing after another. Can anybody confirm this bug?

Using LXDE/Compiz on a 64bit quadcore, 11.04, nVidia 9800 GT something.

As I said... Everyhting works, just :q and :q!, :wq ... Everything that causes the terminal window to go back to where it was before and exit vim causes compiz to freeze.

In short: wtf?! :)

Could anybody confirm that behavior or, even better, provide a solution? If you guys need any sort of logfile output, just let me know.

Thanks in advance.

Andreas

---

### Post by erlenddavidson on 2011-05-02
I get this too, very annoying (and strange).

---

### Post by originofstorms on 2011-05-16
I'm experiencing this behavior as well. BTW, quitting via ZZ also triggers it, and I'm using Xfce's terminal with the classic Gnome setup.

---

### Post by originofstorms on 2011-05-16
Happens when exiting the mysql command line client, too.

---

### Post by originofstorms on 2011-05-18
I've worked around this issue by disabling all of the plugins via CCSM, and re-enabling them one at a time, as I needed them. Apparently whichever plugin is causing this issue is one I don't need, because its working now.

---

### Post by com4 on 2011-06-08
For what it's worth future googlers, I think it's the File Watcher plugin.

---

### Post by AndreasZ on 2011-08-12
I can confirm that... After working around all that for a while now (without checking the forum of course) I figured it had to be something compizzy, because in every other WM it works just fine.

Later on, I figured out that this only happens when I write something to my home directory root. Any sub-directory is fine, but saving something in home root will cause trouble.

Just adding this information to the google index ;) so. write operations in your home directory cause trouble!

vim does that, libreoffice (openoffice) does that, they look for their temp files their and write stuff to ~/.configblayallah

Disabling the FileWatcher will freeze compiz, probably because it writes this information to your home directory for one last time, then this is going to be gone :)

Andreas

---

### Post by brteag00 on 2011-10-08
The Launchpad bug report is here: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/773564](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/773564)

---

### Post by drofart on 2011-10-08
> **AndreasZ said:**
> Hi everyone.

I read a lot of people warning others about upgrading to 11.04, because of the more or less beta unity environment, but since I'm on LXDE/Compiz, this stuff wasn't supposed to affect me in any way.

But now there are some very weird bugs going on. Exiting vim in a terminal freezes my compiz. It gets stuck at 100% cpu load. I can still switch to TTY1 and kill compiz and restart gdm along with it and it works again, but this kind of a bug is really creepy. To rule out any sort of lxde-terminal related error, I installed vim-gtk and played around with it. :q results in a complete Desktop Environment freeze.

I can however use vim on TTY without any sort of weird behavior, also with compiz running in the back. Being used to vim, I don't want to switch to gedit or any sort of other moronic editor, so please spare me with those sorts of suggestions.

After all, this release seems to me a lot more beta than all the others i experienced so far. It messed up a lot of my config files without even asking, I had to reconfigure usbmount, get enhanced zoom desktop, and more importantly, mouse-zooming reactivated, which has for some reason been deactivated, and so on.

But one thing after another. Can anybody confirm this bug?

Using LXDE/Compiz on a 64bit quadcore, 11.04, nVidia 9800 GT something.

As I said... Everyhting works, just :q and :q!, :wq ... Everything that causes the terminal window to go back to where it was before and exit vim causes compiz to freeze.

In short: wtf?! :)

Could anybody confirm that behavior or, even better, provide a solution? If you guys need any sort of logfile output, just let me know.

Thanks in advance.

Andreas
1.) Add the kernel ppa and update your system:
 sudo add-apt-repository ppa:kernel-ppa/ppa  sudo apt-get update 
2.) Check available kernels with the command:
 apt-cache showpkg linux-headers
Now install latest one
sudo apt-get install (latest one)

---

