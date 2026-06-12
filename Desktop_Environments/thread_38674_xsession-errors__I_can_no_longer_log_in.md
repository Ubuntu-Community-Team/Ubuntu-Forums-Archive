---
title: "xsession-errors / I can no longer log in"
date: 2005-06-01
forum: Desktop Environments
---

### Post by cinematography on 2005-06-01
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "me"
/etc/gdm/Xsession: Beginning session setup...

** (gnome-session:9735): WARNING **: Unable to read ICE authority file: /home/me/.ICEauthority

I accidentally closed something in the system monitor and now my user can't log in anymore. :( Ugg... Could someone please help me.

---

### Post by Mez on 2005-06-01
can you copy the output from this command to here please?

```
ls -la ~/.ICEauthority
```

---

### Post by cinematography on 2005-06-01
[QUOTE=Mez]can you copy the output from this command to here please?

```
ls -la ~/.ICEauthority
```[/QUOTE]
Sure. 

-rw------- 1 root root 831 2005-06-01 01:27 /home/me/.ICEauthority

---

### Post by Mez on 2005-06-01
yeah, I'm assuming you're not logged in as root

what you need to so is run the following command, but replace the word username with your username, all three times

```
sudo chown username:username ~username/.ICEauthority
```

for example, my username is mez, so I'd write

```
sudo chown mez:mez ~mez/.ICEauthority
```

This should fix your problem :D

---

### Post by cinematography on 2005-06-01
After entering the code I got a new error saying "could not read ICEauthority...". I used a little common sense and made the file readable also. The problem is now fixed. Thank you SO much for your time and help! :)

---

