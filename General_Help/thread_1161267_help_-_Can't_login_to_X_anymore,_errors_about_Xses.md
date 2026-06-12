---
title: "help - Can't login to X anymore, errors about Xsession"
date: 2009-05-16
forum: General Help
---

### Post by rcopper on 2009-05-16
I was testing the guest profile, and when I tried to switch back to the regular user account, by ending the guest session 
 
as a result I got a white screen, and when I was moving the mouse around I could see it.. throught the screen flickering.. 
so I restarted - 
 
now I can't login back to ubuntu - I get to the login screen - insert the login and password - but get an error saying smth about 
 
```

ending my previous session in less than 10 seconds 
and thus this should signify that there is an installation problem or there is not enough space on the disk

```but there is enough space.. 
then it suggests me to go to the limited gnome session and solve the issue... 
 
when I do so I get another error : 
 
```

 ... dsplay /.xsession-errors > 
- /etc/gdm/Xsession: Beginning session-setup
- settingIM through im-switch for locale = ro_RO
startIM through etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default
mkdtemp: private socketdir: permission denied

```as a result a black screen and the mousepointer.. :(
 
does someone have some ideas about that?
thanks in advance
 
 
**UPD**
I asked people on the IRC and someone suggested that I runned out of space on the partition.... Deleted some files, freed ~2 gigs, tried to login again - got the following error:
 
```

config server problem > usr/lib/libgconf2-4/gconf-sanity-check2 exited with state 256 ...

```rebooted
 
and got back again to those errors that I had at the very beginning... 
:(

---

### Post by Anzan on 2009-05-16
I cannot help with Xorg but if you have home on its own partition it might be quickest to just reinstall.

But if you don't mind waiting I'm sure that someone will come along.

Good luck.

---

### Post by rcopper on 2009-05-16
> **Anzan said:**
> I cannot help with Xorg but if you have home on its own partition it might be quickest to just reinstall.
 
But if you don't mind waiting I'm sure that someone will come along.
 
Good luck.
 
 
no, unfortunately I don't have a separate partition for home.. :( don't want to reinstall everything... took me forever to tune it, and especially to fix the graphics..

---

### Post by Brandon Williams on 2009-05-16
Is there anything else in your .xsession-errors file that might be useful? Maybe you should post the whole thing. 

For debugging purposes, you might want to create a ~/.xprofile that looks like this:
```
set -x
exec 2>&1
```

This will make a much bigger .xsession-errors file, but it should also allow you to see exactly what commands are being run, and hopefully isolate the specific command that is causing trouble for you.

---

### Post by rcopper on 2009-05-16
thanks everybody for the help, but I already fixed the problem, thanks to this post [http://ubuntuforums.org/showthread.php?t=288053](http://ubuntuforums.org/showthread.php?t=288053)

just enter the recovery mode > and type in the command line:

```

sudo chmod a+w /tmp

```

---

### Post by Anzan on 2009-05-17
Oh. That makes sense.

I'm glad it worked out.

---

