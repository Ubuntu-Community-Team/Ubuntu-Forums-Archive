---
title: "Installaing Virtualbox"
date: 2010-03-05
forum: Desktop Environments
---

### Post by motorhead_1 on 2010-03-05
I've tried to follow this guide: [http://kotakomputer.blogspot.com/2010/02/virtualbox-3-on-ubuntu-910-installation.html](http://kotakomputer.blogspot.com/2010/02/virtualbox-3-on-ubuntu-910-installation.html)

fine till the point 
```
#apt-get install virtualbox-3.1
```[I]Just take a cup of coffee because the installation file around 411 MB
Note: you don't need to install dkms because above command automatically install dkms[/I]

when I read this in the terminal: 

```
daitarn@daitarn-laptop:~$ sudo #apt-get install virtualbox-3.1
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...

```:confused:


via virtualbox site I've this:
[[IMG]http://img97.imageshack.us/img97/714/screenshotdf.th.png[/IMG]]("http://img97.imageshack.us/i/screenshotdf.png/")

---

### Post by sebastianabate on 2010-03-05
> **motorhead_1 said:**
> I've tried to follow this guide: [http://kotakomputer.blogspot.com/2010/02/virtualbox-3-on-ubuntu-910-installation.html](http://kotakomputer.blogspot.com/2010/02/virtualbox-3-on-ubuntu-910-installation.html)

fine till the point 
```
#apt-get install virtualbox-3.1
```[I]Just take a cup of coffee because the installation file around 411 MB
Note: you don't need to install dkms because above command automatically install dkms[/I]

when I read this in the terminal: 

```
daitarn@daitarn-laptop:~$ sudo #apt-get install virtualbox-3.1
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...

```:confused:

Try the same command without #. In a command line the initial # means that you must have root permissions to execute it (for example using sudo, like you are doing); if the command is going to be executed by a regular user, the command line must start with a $.
> 
via virtualbox site I've this:
[[IMG]http://img97.imageshack.us/img97/714/screenshotdf.th.png[/IMG]]("http://img97.imageshack.us/i/screenshotdf.png/")
gdebi tells you that there is a conflicting package that prevents the installation, in this case virtualbox-ose-source. You must uninstall this package with
```
sudo apt-get purge virtualbox-ose-source
```and try the installation again.

---

### Post by motorhead_1 on 2010-03-05
perfect, worked as you said. gracias!

---

### Post by motorhead_1 on 2010-03-05
mmm now this..

[I]Then VirtualBox may says that "Unable to find a precompiled module for the current kernel!". Install vboxdrv when the installation asked it. You can later doing this by executing:

[/I]  [INDENT]*/etc/init.d/vboxdrv setup*[/INDENT]*This step may make you confuse, because VirtualBox just jump to command line mode with only a blinking cursor! Just wait for 2-5 minutes then the kernel compilation will be done.*


and my result

```
daitarn@daitarn-laptop:~$ /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netadp kernel module                                  *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                         /etc/init.d/vboxdrv: 382: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong
daitarn@daitarn-laptop:~$ 
```

---

### Post by sebastianabate on 2010-03-05
Glad to help.

One thing that i forgot to mention is that the ose version of virtualbox do not have usb support nor RDP connection. So, if you need to use any usb device inside your virtual machines, or you need to access it from a remote place, you need to install the deb from virtualbox site.

---

### Post by sebastianabate on 2010-03-05
> **motorhead_1 said:**
> mmm now this..

[I]Then VirtualBox may says that "Unable to find a precompiled module for the current kernel!". Install vboxdrv when the installation asked it. You can later doing this by executing:

[/I][INDENT]*/etc/init.d/vboxdrv setup*[/INDENT]*This step may make you confuse, because VirtualBox just jump to command line mode with only a blinking cursor! Just wait for 2-5 minutes then the kernel compilation will be done.*


and my result

```
daitarn@daitarn-laptop:~$ /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox netadp kernel module                                  *  done.
 * Removing old VirtualBox netflt kernel module                                  *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                         /etc/init.d/vboxdrv: 382: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong
daitarn@daitarn-laptop:~$ 
```

You must execute it with root permissions (with sudo for example). Also you possibly need a compiler and the kernel headers (if the package don't have a modules for your kernel version), you can install the necesary packages with the command

```
sudo apt-get install build-essential
```

Another step to use VirtualBox is add your user to the group vboxusers, and the command to do this is

```
sudo usermod -aG vboxusers your_username
```

After that you must logout/login for the changes to take effect.

---

### Post by motorhead_1 on 2010-03-05
it's now installed! muchas gracias again!

---

