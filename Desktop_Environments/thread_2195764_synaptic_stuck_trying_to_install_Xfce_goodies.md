---
title: "synaptic stuck trying to install Xfce goodies"
date: 2013-12-26
forum: Desktop Environments
---

### Post by Buntu Bunny on 2013-12-26
I recently installed Xubuntu 12.04 on my old laptop. I'm currently trying to download and install Xfce Goodies from Synaptic package manager. For the past hour or so, the "Applying Changes" window has been "installing software." The activity bar is going back and forth but details have only shown "Preconfiguring packages" all this time. I tried to close the window but it won't close. Any way to un-stick this or do I just need to reboot the entire system and start over?

---

### Post by vasa1 on 2013-12-26
First open a terminal and kill Synaptic using top.

---

### Post by Buntu Bunny on 2013-12-26
> **vasa1 said:**
> First open a terminal and kill Synaptic using top.

Thanks for the quick reply vasa1. Maybe I didn't do this correctly:

```

$ kill -9 2217
bash: kill: (2217) - Operation not permitted
```

---

### Post by vasa1 on 2013-12-26
> **Buntu Bunny said:**
> Thanks for the quick reply vasa1. Maybe I didn't do this correctly:

```

$ kill -9 2217
bash: kill: (2217) - Operation not permitted
```
Maybe it's my mistake. Killing it may require "sudo" and I haven't done that before but wait awhile for someone to guide you before going the reboot route!

---

### Post by vasa1 on 2013-12-26
Take a look at this: [http://unix.stackexchange.com/questions/89316/how-to-kill-a-process-that-says-operation-not-permitted-when-attempted](http://unix.stackexchange.com/questions/89316/how-to-kill-a-process-that-says-operation-not-permitted-when-attempted)
Sounds promising.

---

### Post by vasa1 on 2013-12-26
I don't have Synaptic installed now, but you could use
```
pgrep synaptic
```
to get the process ID and then 
```
sudo kill PID
```
and if that doesn't work then
```
sudo kill -9 PID
```
where **PID** is the output of the pgrep command.

---

### Post by Buntu Bunny on 2013-12-26
> **vasa1 said:**
> Maybe it's my mistake. Killing it may require "sudo" and I haven't done that before but wait awhile for someone to guide you before going the reboot route!

Thanks vasa1! All your input is very helpful. Sudo worked. You'd think by now I'd know to do that, LOL

I'll try it again and report what happens.

---

### Post by Buntu Bunny on 2013-12-26
Well, I got farther this time but still ran into problems.

```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously unselected package libfam0.
(Reading database ... 156303 files and directories currently installed.)
Unpacking libfam0 (from .../libfam0_2.7.0-17_i386.deb) ...
Selecting previously unselected package libhal1.
Unpacking libhal1 (from .../libhal1_0.5.14-8_i386.deb) ...
Selecting previously unselected package libhal-storage1.
Unpacking libhal-storage1 (from .../libhal-storage1_0.5.14-8_i386.deb) ...
Selecting previously unselected package libthunar-vfs-1-common.
Unpacking libthunar-vfs-1-common (from .../libthunar-vfs-1-common_1.2.0-3build1_all.deb) ...
Selecting previously unselected package libthunar-vfs-1-2.
Unpacking libthunar-vfs-1-2 (from .../libthunar-vfs-1-2_1.2.0-3build1_i386.deb) ...
Selecting previously unselected package squeeze.
Unpacking squeeze (from .../squeeze_0.2.3-12_i386.deb) ...
Selecting previously unselected package mousepad.
Unpacking mousepad (from .../mousepad_0.2.16-5ubuntu1_i386.deb) ...
Selecting previously unselected package xfce4-artwork.
Unpacking xfce4-artwork (from .../xfce4-artwork_0.1.1a~git+20110420-1_all.deb) ...
Selecting previously unselected package xfce4-battery-plugin.
Unpacking xfce4-battery-plugin (from .../xfce4-battery-plugin_1.0.0-3_i386.deb) ...
Selecting previously unselected package xfce4-clipman.
Unpacking xfce4-clipman (from .../xfce4-clipman_2%3a1.2.2-1_i386.deb) ...
Selecting previously unselected package xfce4-clipman-plugin.
Unpacking xfce4-clipman-plugin (from .../xfce4-clipman-plugin_2%3a1.2.2-1_i386.deb) ...
Selecting previously unselected package xfce4-cpufreq-plugin.
Unpacking xfce4-cpufreq-plugin (from .../xfce4-cpufreq-plugin_1.0.0-4_i386.deb) ...
Selecting previously unselected package xfce4-diskperf-plugin.
Unpacking xfce4-diskperf-plugin (from .../xfce4-diskperf-plugin_2.3.0-2_i386.deb) ...
Selecting previously unselected package xfce4-fsguard-plugin.
Unpacking xfce4-fsguard-plugin (from .../xfce4-fsguard-plugin_1.0.0-3_i386.deb) ...
Selecting previously unselected package xfce4-genmon-plugin.
Unpacking xfce4-genmon-plugin (from .../xfce4-genmon-plugin_3.3.1-1_i386.deb) ...
Selecting previously unselected package xfce4-mount-plugin.
Unpacking xfce4-mount-plugin (from .../xfce4-mount-plugin_0.5.5-2_i386.deb) ...
Selecting previously unselected package xfce4-sensors-plugin.
Unpacking xfce4-sensors-plugin (from .../xfce4-sensors-plugin_1.2.3-2_i386.deb) ...
Selecting previously unselected package xfce4-smartbookmark-plugin.
Unpacking xfce4-smartbookmark-plugin (from .../xfce4-smartbookmark-plugin_0.4.4-1ubuntu1_i386.deb) ...
Selecting previously unselected package xfce4-timer-plugin.
Unpacking xfce4-timer-plugin (from .../xfce4-timer-plugin_0.6.3-1ubuntu1_i386.deb) ...
Selecting previously unselected package xfce4-wavelan-plugin.
Unpacking xfce4-wavelan-plugin (from .../xfce4-wavelan-plugin_0.5.6-1_i386.deb) ...
Selecting previously unselected package xfce4-goodies.
Unpacking xfce4-goodies (from .../xfce4-goodies_4.8.2_i386.deb) ...
Selecting previously unselected package hddtemp.
Unpacking hddtemp (from .../hddtemp_0.3-beta15-51_i386.deb) ...
Selecting previously unselected package lm-sensors.
Unpacking lm-sensors (from .../lm-sensors_1%3a3.3.1-2ubuntu1_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 man-db
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libthunar-vfs-1-common (1.2.0-3build1) ...
Setting up xfce4-battery-plugin (1.0.0-3) ...
Setting up hddtemp (0.3-beta15-51) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing hddtemp (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.6.1-2ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up xfce4-fsguard-plugin (1.0.0-3) ...
Setting up xfce4-sensors-plugin (1.2.3-2) ...
Setting up xfce4-diskperf-plugin (2.3.0-2) ...
Setting up xfce4-timer-plugin (0.6.3-1ubuntu1) ...
Setting up libhal1 (0.5.14-8) ...
Setting up xfce4-wavelan-plugin (0.5.6-1) ...
Setting up xfce4-clipman (2:1.2.2-1) ...
Setting up xfce4-smartbookmark-plugin (0.4.4-1ubuntu1) ...
Setting up lm-sensors (1:3.3.1-2ubuntu1) ...
Setting up xfce4-genmon-plugin (3.3.1-1) ...
Setting up mousepad (0.2.16-5ubuntu1) ...
Setting up xfce4-cpufreq-plugin (1.0.0-4) ...
Setting up xfce4-mount-plugin (0.5.5-2) ...
Setting up libfam0 (2.7.0-17) ...
Setting up xfce4-artwork (0.1.1a~git+20110420-1) ...
Setting up xfce4-clipman-plugin (2:1.2.2-1) ...
Setting up libhal-storage1 (0.5.14-8) ...
Setting up libthunar-vfs-1-2 (1.2.0-3build1) ...
Setting up squeeze (0.2.3-12) ...
Setting up xfce4-goodies (4.8.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 hddtemp
 man-db
```

---

### Post by vasa1 on 2013-12-26
> **Buntu Bunny said:**
> Well, I got farther this time but still ran into problems.
...
/var/cache/debconf/config.dat is locked by another process ...

I googled for "/var/cache/debconf/config.dat is locked by another process"
and found this: [http://askubuntu.com/a/232919/25656](http://askubuntu.com/a/232919/25656)

Edit: you can read about "fuser" with **man fuser**.

---

### Post by Buntu Bunny on 2013-12-26
> **vasa1 said:**
> I googled for "/var/cache/debconf/config.dat is locked by another process"
and found this: [http://askubuntu.com/a/232919/25656](http://askubuntu.com/a/232919/25656)

Edit: you can read about "fuser" with **man fuser**.

Now it's getting complicated (which seems to be the story of my 'buntu life)

```
buntu bunny@buntu bunny-700m:~$ sudo fuser -k /var/cache/debconf/config.dat
[sudo] password for buntu bunny: 
/var/cache/debconf/config.dat:  2243
buntu bunny@buntu bunny-Inspiron-700m:~$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Unfortunately I have to go now. Help still much needed and appreciated, but it may be a bit before I can get back to this and respond.

---

### Post by vasa1 on 2013-12-26
Well, I hope someone more knowledgeable chimes in! But for extra reading there is this: [http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem](http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem).

---

### Post by Buntu Bunny on 2013-12-26
Well, it was awhile before I could get back to try this. This time, Synaptic indicated that Xfce goodies was already installed. I did find the goodies extra artwork under desktop settings, so I reckon it's true. I'm not sure what effects the error messages will have, but if there is a glitch somewhere I will start a new thread and will mark this one solved in the meantime.

---

### Post by Buntu Bunny on 2013-12-27
FOLLOW-UP: info update

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/)
```

I had a repeat of this error message when I tried to install Conky Manager. I researched and learned that this error message occurs if a package manager is already open. In my case, I had not closed out Synaptic, hence the problem. After I closed it, I was able to proceed error free.

---

