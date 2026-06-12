---
title: "KDM not autostarting"
date: 2008-11-13
forum: Desktop Environments
---

### Post by Calash on 2008-11-13
Up to 8.10 I had a basic Ubuntu install using Gnome, with a second Fluxbox install just for kicks.  After updating to 8.10 I decided to try out KDE.  In installed kubuntu-desktop and played around with it, found I liked it, and removed as many of the gnome desktop parts as I could.

Now, when I reboot I get stuck with the terminal screen.  After logging in I can startx or sudo KDM and the gui comes right up, but it will not start without me interacting.

I tried the basics already, reconfiguring the package and it is set to KDM for the desktop manager.


Any ideas?

---

### Post by Calash on 2008-11-15
Anybody have any ideas?

---

### Post by vblanton on 2009-05-14
Bump, I am also having this problem.  I didn't delete any gnome bits that I can remember, but around 8.10 kdm no longer would autostart.  I have been "sudo kdm"ing every time I want to login from a fresh restart of the computer! Very annoying, thanks for the help!

---

### Post by micio on 2009-05-15
Have you try to put KDM in the correct runlevel?

```
sudo update-rc.d kdm defaults
```

---

### Post by vblanton on 2009-05-15
Hmm, no go. Here is the output:

```
vblanton@ubuntu:~$ sudo update-rc.d kdm defaults
[sudo] password for vblanton:
 System startup links for /etc/init.d/kdm already exist.
```

---

### Post by micio on 2009-05-15
can you post these logs files?
gdm.log, kdm.log and Xorg.0.log
You can find them in /var/log/

Please ensure that you have not gdm in your system.

---

### Post by vblanton on 2009-05-15
gdm.log and kdm.log are empty

Xorg.0.log is pasted here:
[http://pastebin.com/m744d1627]("http://pastebin.com/m744d1627")

I _do_ have gdm installed on my system. That shouldn't be an issue, but I'll try to see if removing it does anything right now.

thanks!

---

### Post by micio on 2009-05-15
try removing gdm from boot time with
```
sudo update-rc.d -f gdm remove
```

and then, please tell me if kdm starts with
```
sudo /etc/init.d/kdm start
```

Just a note, I don't know if kde4 require kdm to run, when I used kde, long times ago, I used gdm and simply changing the session to start, may you try this way.  
Thanks,

Micio

---

### Post by vblanton on 2009-05-15
"sudo update-rc.d -f gdm remove" worked, removing it in a number of places

"sudo /etc/init.d/kdm start" stated that it was not the default display manager.

I have removed gdm entirely (sudo apt-get remove gdm) and will shut down the computer.  Tomorrow, when I turn it back on, i'll see if kdm autostarts or not. Thanks a lot!

Vlad

---

### Post by micio on 2009-05-15
Nevermind, in order to set kdm as default login manager you can follow these instructions:

```
sudo dpkg-reconfigure kdm
```

click ok.... ( press enter )
it will give you option... gdm / kdm......
select kdm

It should work.):P):P

---

### Post by vblanton on 2009-05-16
Well, I've gone ahead and issued the command. I've done it before without any positive result, but interestingly it didn't ask me anything this time.  That is probably because I removed gdm from my system. Will restart my computer again after I finish some work and see if that did the trick!

---

### Post by biophysics on 2009-05-16
Sometimes I have found that the easiest way is to install xdm and get some form of login window.
1. purge kdm (instead of remove)
2. install kdm

---

### Post by vblanton on 2009-05-17
Thanks for both the replies.  Still no go, i've attempted to restart after both of the last suggestions and the same login prompt appeared. no kdm.

It appears to be that kdm is not set as the default, because when I issue 'sudo /etc/init.d/kdm start' it complains about it not being the default.
But, setting it as default (as suggested in a previous post) also does nothing.  strange, huh?

I'll continue mucking around and seeing what i can do to get rid of whatever setting or conflict caused this in the first place

---

### Post by vblanton on 2009-05-17
Well, I've figure it out. after looking in /etc/X11/default-display-manager ("sudo nano -w /etc/X11/default-display-manager") I noticed that the entry pointed to "/usr/sbin/kdm" which doesn't exist.  A quick switch to "/usr/bin/kdm" which is the correct directory fixed the issue.  Perhaps a directory switch happened somewhere along the upgrade path a year ago, but whatever the reason was -- everything starts up as it should now :)

Thanks for both of your help. glad this is fixed

---

