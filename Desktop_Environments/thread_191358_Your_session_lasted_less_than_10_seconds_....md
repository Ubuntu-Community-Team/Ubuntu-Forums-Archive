---
title: "Your session lasted less than 10 seconds ..."
date: 2006-06-07
forum: Desktop Environments
---

### Post by juliocesargarcia on 2006-06-07
I am sorry about asking this again. I have seen a few posts on this topic, but none has helped this anoying problem. I'm sure I have inadvertently screwed up my config somwhere, but I do not know where. When I try to log in, I get an error window with the text

```
Your session only lasted less than 10 seconds. If you ...
```

My .xsession-errors file has nothing useful:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /v
ar/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "julio"
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession
```

The ownership of my .ICEauthority is OK.

I have not had login problems with ssh or running a vnc server. Any ideas as to what I should look into?

---

### Post by effoff on 2006-06-07
Just delete ~/.ICEauthority from "safe mode" with the rm command and all will be normal on the next boot when a new fresh one without errors will be created...
Just take more than ten seconds doing it :)

shutdown with sudo shutdown now

---

### Post by mlho on 2006-06-07
I'm getting the same message, but slightly different outut in my .xsession-error. Can login as tty, but not with ctrl-alt-F7.
 
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mark"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: No space left on device
```

---

### Post by juliocesargarcia on 2006-06-07
[QUOTE=effoff]Just delete ~/.ICEauthority from "safe mode" with the rm command and all will be normal on the next boot when a new fresh one without errors will be created...
Just take more than ten seconds doing it :)

shutdown with sudo shutdown now[/QUOTE]

I had done this, but I tried it again and made sure to take at least 20 seconds :-D. It does not even create an .ICEauthority file when I try to login from the console.

Now, my home directory is NFS mounted, but local root has root access to the remote NFS directory. I made sure of that, although it would not seem to matter.

So, no luck.:confused:

---

