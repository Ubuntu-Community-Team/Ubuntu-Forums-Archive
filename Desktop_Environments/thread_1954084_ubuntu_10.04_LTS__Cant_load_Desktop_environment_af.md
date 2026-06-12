---
title: "ubuntu 10.04 LTS : Cant load Desktop environment after fsck"
date: 2012-04-07
forum: Desktop Environments
---

### Post by celebratinglife on 2012-04-07
I am using ubuntu for the past six years. I am a medico not a techno guy but  I love Ubuntu. This is for the first time I am stuck with something that I am unable get rid of even after extensive searching in forums.

I am using ubuntu 10.04 LTS. Everything was going well till three days back (except some minor glitches that I was able to solve with 5-10 min searching in this forum).

Three days ago when I clicked shutdown to put off the system, there appeared the shutdown option window but instead of the usual options of cancel and shutdown...it was blank. It remained as such for half a minute. I canceled it and then clicked shutdown again and  the same happened. As I was feeling very sleepy I just put off the system by directly  powering off.

When I started the system next day I was unable to boot in and got the **error: No init found. Try passing init=bootarg** and got the Busybox built in shell with  **(initramfs)_**
As per the solution suggested in ubuntu forum I ran **fsck using a Live usb**.

After fsck I was able to boot into the system but only into CLI. When I boot in it shows the ubuntu logo as usual and then instead of login window it shows tty1.
After logging in through tty1 when I run **sudo start gdm** the screen turns black. From this black screen I cant even go back to CLI using alt+ctrl+F(1-6) and I have to power off the system to restart. When I type **startx** in tty after login it shows **error in configuration server: (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)**

when I type s**udo gdm start** in tty after login it shows the **error: unable to connect to sytem bus: Failed to connect to socket /var/run/dbus/system_bus_socket: no such file or directory**

Its when I type** sudo start gdm** screen goes black.
When I type **sudo gdm start** it shows the [B]error: unable to connect to sytem bus: Failed to connect to socket /var/run/dbus/system_bus_socket: no such file or directory
[/B]
I have tried everything suggested in forums but with no success at all. Please help me to get my Desktop environment back so that I can use the system at least till the final version of 12.04 LTS arrives. I don't want to install the OS two times within a month.

Thanx

---

### Post by celebratinglife on 2012-04-08
Somebody plz help!

---

### Post by winh8r on 2012-04-08
Have you tried dropping into recovery mode and running "fix broken packages"?

Then try 

```
sudo apt-get update && sudo apt-get upgrade
```

* this will not upgrade the distribution from 10.04 to 12.04 it will merely upgrade the packages already installed on your system.

---

### Post by celebratinglife on 2012-04-09
> **winh8r said:**
> Have you tried dropping into recovery mode and running "fix broken packages"?

Then try 

```
sudo apt-get update && sudo apt-get upgrade
```

* this will not upgrade the distribution from 10.04 to 12.04 it will merely upgrade the packages already installed on your system.

thanx for the reply bro! At least someone replied!
To run the updates I need to run the netwrk manager first as I am using 3g data card for internet.  I havent run it before using command line. How can I run it?

---

### Post by westie457 on 2012-04-09
This will either start or tell you if already running.
```
sudo NetworkManager
```

---

### Post by celebratinglife on 2012-04-09
On typing the code:
sudo NetworkManager

it shows the warning-
state file /var/lib/NetworkManager/NetworkManager.state parsing failed: (2) Error creating state directory /var/lib/NetworkManager: 2

---

### Post by winh8r on 2012-04-09
The only thing i have seen so far that resolves the "sanity error 256 in gconf) is running this command once you have logged in to tty1



```
sudo mkdir -p /usr/local/etc/gconf/gconf.xml.defaults
```

seems to have been an issue a while back on 10.04 but never really got a proper solution as far as launchpad goes:

see here:

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/577545]("https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/577545")


edit: just noticed the above command is listed as a solution at post #16 in the above link.

Hope it helps you.

---

### Post by celebratinglife on 2012-04-10
Thanx to u all but I have already tried every solution provided above... No success at all.  It shows the same errors and warnings.
The only thing I have'nt tried is to run updates which I am unable to do because of errors in Network Manager as stated above.

---

