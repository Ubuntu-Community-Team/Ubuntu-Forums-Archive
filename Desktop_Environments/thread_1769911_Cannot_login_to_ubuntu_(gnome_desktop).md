---
title: "Cannot login to ubuntu (gnome desktop)"
date: 2011-05-28
forum: Desktop Environments
---

### Post by NERJ on 2011-05-28
Hi,
I had ubuntu working fine, but then I started tinkering with the DISPLAY variable and maybe some other xserver setting, and now the system is stuck at the login screen.

If I type in my password and hit enter, it will go to a black screen, and then go back to the login screen.

When I enter console mode with control-alt-F1, I can login fine, but I cannot run any x-commands successfully. 

$ startx

gives the error:

xauth: error in locking authority file /home/system/.Xauthority
xauth: error in locking authority file /home/system/.Xauthority

Fatal server error:
Server is already active for display 0
      If this server is no longer running, remove /tmp/.X0-lock and start again

Please consult the The X.Org Foundation support
      at [http://wiki.x.org](http://wiki.x.org)
 for help

 ddxSigGiveUp: Closing log
No Protocol specified
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
xauth: error in locking authority file /home/system/.Xauthority 


I removed that file as directed, but it didn't fix anything

$ gdm

gives the error:


** (gdm-binary:1668 ): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.36" is not allowed to own the service  "org.gnome.DisplayManager: due to security policies in the configuration file

** (gdm-binary:1668 ): WARNING **: Could not acquire name; bailing out 


I've tried running the command: 

$ sudo dpkg-reconfigure xserver-xorg

but it didn't change anything

---

### Post by yo_bhan on 2011-05-28
maybe this will help
login to tty1 and run
> 
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start


---

### Post by NERJ on 2011-05-29
> **yo_bhan said:**
> maybe this will help
login to tty1 and run

That didn't work
It says to use the "service(8 ) utility e.g. service gdm start" or "start gdm"

When I use the command start gdm, I get the error:

start: Rejected start message, 1 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=1780 comm="start gdm") interface="com.ubuntu.Upstart0_6.Job" member"Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

---

### Post by NERJ on 2011-05-30
bump

---

### Post by NERJ on 2011-05-31
bump again

I really don't want to reinstall everything

---

### Post by NERJ on 2011-06-01
I solved this

But I don't understand why the fix worked. 
I removed:

     export DISPLAY
     DISPLAY="localhost:0.0"

from my .profile
This was in both my .bashrc and my .profile
but I left in my .bashrc
(also, my DISPLAY is in fact set to localhost:0.0)

Does this make any sense, or is this a bug?

---

### Post by NERJ on 2011-06-05
Come on

Are people here familiar with linux?

---

