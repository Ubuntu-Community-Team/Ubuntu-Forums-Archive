---
title: "Will KDE work without users in the sudo file? (bc it relies on kdesudo so much)"
date: 2009-11-01
forum: Desktop Environments
---

### Post by rma88 on 2009-11-01
Okay, so if I take my user out of the sudoers file because I don't my user having admin rights... thats for the admin.... Will KDE still work?

It seems like it should prompt me for the root password (which is what kdesudo supposedly does by default), but because I'm now reinstalling kubuntu bc it was freaking out about KDE sudo, I thought I would ask.

Does anyone NOT have their user in the /etc/sudoers file and run KDE just fine? If so, how does kdesudo work when you go to do administrative tasks from the GUI (i.e. change user accounts or do updates etc...)

thanks all, any help is really appreciated!

---

### Post by ltmon on 2009-11-01
kdesu can be configured to work in both SU and SUDO mode. It's in SUDO mode by default in kubuntu.

To change this, I'm pretty sure a ~/.kde/share/config/kdesurc file looking like the following will work (note: untested)

```

[super-user-command]
super-user-command=su

```

---

### Post by lovinglinux on 2009-11-01
I guess if you remove your user you will be locked out, even from gnome. 

Instead of removing your user, create a new one without administrative privileges and use if for normal stuff. Then you can login into your admin account just for administartive purposes. 

Without administrative rights I can't work properly. I do a lot of stuff on a regular basis that needs admin rights. I'm not sure if this is a bad behavior, since we still need sudo to perform those tasks.

---

### Post by rma88 on 2009-11-01
> **lovinglinux said:**
> 

Instead of removing your user, create a new one without administrative privileges and use if for normal stuff. Then you can login into your admin account just for administartive purposes. 


See, exactly! I want my root user to perform administrative tasks, and my user to perform basic stuff / regular day activities.

Okay...soooo, I sudo su root. Set the root's password. Then remove my user from the sudoers file. Now, how can I still get kdesudo to work correctly?

@ltmon   ->   I don't already have a  ~/.kde/share/config/kdesurc file. Just create it? See kdesudo says it default to asking for the password for the root. But when you do stuff through the GUI and kdesudo pops up, it clearly wants that users password and then checks the sudo file (so I believe). So changing it to do --user root (or whatever the switch is) might be the way to go. I'll try making that file with the command you specified though, we'll see what it does.

Thanks for the input guys, I really appreciate it.

---

### Post by rma88 on 2009-11-01
> **ltmon said:**
> kdesu can be configured to work in both SU and SUDO mode. It's in SUDO mode by default in kubuntu.

To change this, I'm pretty sure a ~/.kde/share/config/kdesurc file looking like the following will work (note: untested)

```

[super-user-command]
super-user-command=su

```

Okay so I created this file, and when I go to do administrative tasks through the GUI (like edit user accounts). It still prompts with kdesudo for the password :(

So really, EVERY person uses one account with sudo privileges to do everything they do? No one has a root account setup with a password that they su to and then perform administrative tasks? I find it really hard to believe that everyone types 'sudo' in front of all their admin tasks.

Please guys, any help is really appreciated!

---

### Post by ltmon on 2009-11-01
Maybe this will do what you want, but it's a bit old:
[http://consistencies.net/20051018/fixing-kdesu-problems-in-kubuntu/](http://consistencies.net/20051018/fixing-kdesu-problems-in-kubuntu/)

However we now have "kdesudo", not "kdesu" -- I don't know if it will act as you want, or is hard coded to "sudo". I seem to have a "kdesu_stub" binary hanging around, but I have no idea why -- in any case it doesn't seem to work.

Also, instead of activating the root account, or sudo-ing everything, it's quite possible to 
```

# sudo su -

```

to gain a root prompt for a string of admin tasks.

---

