---
title: "VMWare Console has gone gobbly-gook?"
date: 2006-08-03
forum: Desktop Environments
---

### Post by rth on 2006-08-03
I installed the updates to Ubuntu this morning, they included GTK stuff IIRC. When I opened up my VMWare Console afterwards, all of the text has turned into those boxes (they look like: []).

[Screenshot]("http://www.rthn.com/media/VMWareConsole0.png")

I'm using 64 bit Ubuntu... Any ideas?

---

### Post by hainesr on 2006-08-03
Yes, this has happened to me too. I wasn't initially that bothered as I can find my way round vmware to boot OSs, but I've just tried to save something from Firefox and the save box is all messed up too.

I'm also using 64bit dapper...

This is a real show stopper. I even tried restarting gnome, but to no avail.

Can I roll-back this morning's update somehow?

Cheers,
Rob

---

### Post by thingy on 2006-08-03
Its using a weird font.

Are any other applications displaying this behaviour...

Odd that only vmware would be affected.

See if there are any .gtk* files in your ~

Move those to another directory temporarily and try launching vmware

Rule out vmware config files as well using the same method...

jin

---

### Post by miasma on 2006-08-03
Realplayer and OpenOffice.org (Open File-Dialog) are affected too.
I'm also using 64bit dapper.
It's caused by the recent update of ia32-libs-gtk. You can revert to version 16 via "Force version" in Synaptic.

jue

---

### Post by rth on 2006-08-03
That's good that I'm not the only one... I didn't check other applications as Firefox, Thunderbird, GAIM, and my usual ones are OK.

I'll look at rolling back, but I may also just wait for this to be fixed and a new file becomes available.

---

### Post by magian on 2006-08-03
Hi all.

I too am having the problem after an update via Synaptic.

Can someone explain how it is possible to rollback like that?

Oops!  Nevermind.  RTFI and figured it out.  Works fine now.
I hope this gets resolved soon for 64bit installs.

---

### Post by rth on 2006-08-03
Anyone know if a bug has been logged?

---

### Post by g00fy on 2006-08-04
[https://launchpad.net/distros/ubuntu/+source/ia32-libs-gtk/+bug/55093](https://launchpad.net/distros/ubuntu/+source/ia32-libs-gtk/+bug/55093)

---

### Post by rth on 2006-08-05
ia32-libs-gtk 16.2 is out. All is well again, run Update Manager to get it (or your favourite way of getting updates).

---

