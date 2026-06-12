---
title: "After security updates Unity will not launch"
date: 2012-11-05
forum: Desktop Environments
---

### Post by Mogen317 on 2012-11-05
Hi.  I'm on Ubuntu 12.10.  Ten min ago software updater popped up and asked me to install some security updates and reboot.  After doing so unity will not launch and I'm left with a blank desktop after logging in.  Running "compiz --replace" and "unity" in terminal fails.

How can I check to see what I just installed and figure out what's causing this problem?

---

### Post by stinkeye on 2012-11-05
Try to reset compiz with...
```
dconf reset -f /org/compiz/
```


Then reload with...
```
setsid unity
```

---

### Post by Mogen317 on 2012-11-05
Sadly, that did not work either.  Here is the console output:

```
mike@mike-ThinkPad-X120e:~$ dconf reset -f /org/compiz
mike@mike-ThinkPad-X120e:~$ setsid unity
mike@mike-ThinkPad-X120e:~$ unity-panel-service: no process found
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  23
  Current serial number in output stream:  23
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Error: Plugin initScreen failed: opengl
compiz (core) - Error: Failed to start plugin: opengl
compiz (core) - Info: Unloading plugin: opengl
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: scale
compiz (core) - Error: Failed to start plugin: scale
compiz (core) - Info: Unloading plugin: scale
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng


```

What's curious to me is the ```
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
```

I have been runing unity using hardware accelerated effects and the 12.11 catalyst drivers for my ATI Radeon GPU.  I did ```
sudo apt-get purge fglrx*
``` and rebooted, but same problem.

---

### Post by stinkeye on 2012-11-05
Try purging your proprietary drivers and then install linux-headers-generic and reinstall drivers.

eg [**_[COLOR="DarkRed"]THIS[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12338523&postcount=2") solved my nvidia install.

[**_[COLOR="DarkRed"]Bug #1068488[/COLOR]_**]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488")

---

### Post by Mogen317 on 2012-11-05
Found the packages that got installed they were:
```
linux-image-3.5.0-18-generic:amd64 <none> 3.5.0-18.29
linux-headers-3.5.0-18:all <none> 3.5.0-18.29
linux-headers-3.5.0-18-generic:amd64 <none> 3.5.0-18.29
linux-image-extra-3.5.0-18-generic:and <none> 3.5.0-18.29
```

So I'm assuming that my graphics driver is incompatible with linux kernel 3.5.0-18.29

I'm using the latest driver from AMD, does anyone know how to downgrade the kernel?  What will happen if I do apt-get remove to all that stuff?

---

### Post by black veils on 2012-11-07
when booting, press and hold the **shift** key until grub menu shows.

for now at least, you can manually boot into the previous kernel from here, see if that allows things to work.

---

