---
title: "How to get vnc access to my current desktop?"
date: 2006-07-20
forum: Desktop Environments
---

### Post by revoohc on 2006-07-20
How can I setup my current kde desktop to be accessible by vnc?  I would like to be able to take over my desktop when I connect from home via our companies  vpn.  Is this possible?

Thanks,

revoohc

---

### Post by Paerez on 2006-07-20
It is possible, but I don't know if you can grab the current session and pipe it over vnc. I know how to create a new screen that is a vnc screen. First, get a vnc client/server. I like tightvnc. Then, on your computer, type:
```
vncserver :1
```
to create a screen on :1 (you could also pick a different number)
now vnc is being broadcast 5901 (or 5902 etc). Then from another computer, use a vnc client (there are some for windows and linux) and type:
```
vncviewer yourcomputer:1
```
where "yourcomputer" is the hostname of your computer at home. Or IP. However you connect.

---

