---
title: "X server /tmp files blown away."
date: 2005-09-19
forum: Desktop Environments
---

### Post by supine on 2005-09-19
After a period of use I can no longer open anything within X. The error is:

```
unable to open display ":0.0"
``` 

and my /tmp directory looks like this:

```
 ls -la /tmp/
total 12
drwxrwxrwx   2 root root 8192 2005-09-19 14:32 .
drwxr-xr-x  22 root root 4096 2005-04-18 14:46 ..
-rw-r--r--   1 root root    0 2005-09-19 10:15 .clean
```

I've search /etc/cron* and /var/spool/cron/* for anything that touches /tmp to no avail.

Any ideas?

---

### Post by skoal on 2005-09-19
What is the value of '/etc/default/rcS' TMPTIME variable?

mine (default):
TMPTIME=0

What are the permissions on your /tmp folder?  Any accidental changes to it, like recreating to it (or chmod/chown)?

mine (default):
skoal@morpheus:///tmp $ ls -ld /tmp/
drwxrwxrwt  14 root root 656 2005-09-19 02:53 /tmp/

Does this occur at random while running Gnome, for example? And then your Xserver dies unexpectadly? Or are there any particular apps you run routinely which seem to trigger it? Any apps you run as root?

\\//_

---

### Post by supine on 2005-09-19
[QUOTE=skoal]What is the value of '/etc/default/rcS' TMPTIME variable?

mine (default):
TMPTIME=0[/QUOTE]

same here:
TMPTIME=0


> What are the permissions on your /tmp folder?  Any accidental changes to it, like recreating to it (or chmod/chown)?

mine (default):
skoal@morpheus:///tmp $ ls -ld /tmp/
drwxrwxrwt  14 root root 656 2005-09-19 02:53 /tmp/

ls -ld /tmp/
drwxrwxrwx  2 root root 8192 2005-09-19 14:32 /tmp/


> Does this occur at random while running Gnome, for example?

I'm running Gnome.


> And then your Xserver dies unexpectadly?

The X-server doesn't die but you can't open any more apps that need to open a connection to the X-server.

```
 7511 ?        Ss     0:00 /usr/bin/gdm
 7541 ?        S      0:00  \_ /usr/bin/gdm
 7576 ?        S    398:23      \_ /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 8863 ?        Ss     0:05      \_ x-session-manager
 8914 ?        Ss     0:00          \_ /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager

```

> Or are there any particular apps you run routinely which seem to trigger it?

Doesn't seem to be anything in particular although it is happening on both my laptop and my desktop which having almost identical --get-selections

> Any apps you run as root?

None.

---

### Post by [pl]ice on 2005-09-19
apt-get clean worked for me, but that was because i almost made full hd ; try it ...

---

### Post by skoal on 2005-09-19
[QUOTE=supine]ls -ld /tmp/
drwxrwxrwx  2 root root 8192 2005-09-19 14:32 /tmp/[/QUOTE]
My best guess would be that somehow your "sticky" bit on your /tmp directory was changed.  Notice the "t" missing from yours and the original I posted of mine.

I do not recall the exact steps of X server initialization, but the .X0-lock file is owned by root (not your normal user).  There's a lot of voodoo which goes on with GDM, PAM, /var/lock and such when the X server initializes.  It may very well be that some other app you run, or just some random proc testing for an X server running, checks that .X0-lock file (since you happily have it world writable, at present) and removes it.  I dunno.  Countless possibilities here.  At least fix your /tmp directory like this:

sudo chmod 1777 /tmp

...that should at least remove that possible cause.

\\//_

---

