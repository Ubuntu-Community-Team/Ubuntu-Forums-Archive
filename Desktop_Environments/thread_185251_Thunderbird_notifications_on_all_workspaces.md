---
title: "Thunderbird notifications on all workspaces"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-05-31
How do I get thunderbird to display notifications of new email messages on whichever workspace I'm working in?  I have the option to show notification ticked in the preferences menu, but this doesn't work (it also doesn't play a sound, even though that box is ticked).

---

### Post by nanotube on 2006-05-31
[QUOTE=Lunar_Lamp]How do I get thunderbird to display notifications of new email messages on whichever workspace I'm working in?  I have the option to show notification ticked in the preferences menu, but this doesn't work (it also doesn't play a sound, even though that box is ticked).[/QUOTE]
for new email notification, install this extension:
[http://moztraybiff.mozdev.org/](http://moztraybiff.mozdev.org/)
it will put an icon in your systray/notification area that you have new mail.

for thunderbird, if you run it with "esddsp" i think that should give it sound... but that's on breezy, don't know what dapper's got :)

---

### Post by Lunar_Lamp on 2006-05-31
What do you mean by "run it with esddsp"?

---

### Post by nanotube on 2006-05-31
[QUOTE=Lunar_Lamp]What do you mean by "run it with esddsp"?[/QUOTE]

from a terminal, issue
```
esddsp thunderbird
```
(or maybe "esddsp mozilla-thunderbird", depending on what they call it on dapper)

---

### Post by Lunar_Lamp on 2006-05-31
[QUOTE=nanotube]from a terminal, issue
```
esddsp thunderbird
```
(or maybe "esddsp mozilla-thunderbird", depending on what they call it on dapper)[/QUOTE]

esddsp: command not found

running "esd mozilla-thunderbird" gives:
$ esd mozilla-thunderbird
unrecognized option: mozilla-thunderbird
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...

---

### Post by nanotube on 2006-05-31
[QUOTE=Lunar_Lamp]esddsp: command not found

running "esd mozilla-thunderbird" gives:
$ esd mozilla-thunderbird
unrecognized option: mozilla-thunderbird
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...[/QUOTE]

ah, sorry, first you have to install package esound-clients :)

---

### Post by Lunar_Lamp on 2006-06-01
[QUOTE=nanotube]ah, sorry, first you have to install package esound-clients :)[/QUOTE]


Ok, I did that and now:

$ esddsp mozilla-thunderbird
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131:  6355 Illegal instruction     "$prog" ${1+"$@"}

---

### Post by Lunar_Lamp on 2006-06-01
[QUOTE=Lunar_Lamp]Ok, I did that and now:

$ esddsp mozilla-thunderbird
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131:  6355 Illegal instruction     "$prog" ${1+"$@"}[/QUOTE]


Hmm, I have tried it when tbird is open, and it doesn't spew out an error message, but clicking on "preview sound" still doesn't play any sound.

---

### Post by nanotube on 2006-06-01
hm, in that case, you will probably have to look for another solution to the sound problem... anyone else have any ideas?

---

### Post by rutgerw on 2006-09-07
I think I have the solution to yout problem:

install alsaplayer-esd, it fixed the problem with me.

You will probably also need libesd-alsa0 for it to work.

```

sudo apt-get install libesd-alsa0 alsaplayer-esd
```

---

### Post by crossedout on 2006-09-07
If you use gdesklets you may want to consider looking at the mail desklets.  The desklets cross workspaces by default and may have a hide-away option to keep it non-intrusive.

-Xout

---

