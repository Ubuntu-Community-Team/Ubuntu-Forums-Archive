---
title: "How to stop Xserver after it started?"
date: 2006-09-22
forum: Desktop Environments
---

### Post by ryurhrt on 2006-09-22
to start the xserver, simply use "startx"
but to stop it? how? what are the steps?

:)

---

### Post by Qrk on 2006-09-22
```
sudo killall gdm
```

---

### Post by ryurhrt on 2006-09-22
wao... sudo killall gmd make my desktop left only wallpaper :p

the command i found should be:
sudo invoke-rc.d gmd stop

---

### Post by Qrk on 2006-09-22
hmm. thats funny. It killed mine all the way. I wonder why it would work on my system and not yours.

---

### Post by mssever on 2006-09-22
If you start with startx, then gdm isn't running (presumably).

Either: Hit Ctrl+Alt+Backspace; or Switch to a console and type ```
sudo killall Xorg
```

---

### Post by ntom-taylor on 2008-02-25
Or a simple..  

```
sudo /etc/init.d/gdm stop
```

---

### Post by HermanAB on 2008-02-25
I wonder how many ways there are to stop X?

Here is another:
sudo init 3

---

### Post by mssever on 2008-02-25
> **ntom-taylor said:**
> Or a simple..  

```
sudo /etc/init.d/gdm stop
```
Yes, but that won't work if you started X via startx, as in the OP.
> **HermanAB said:**
> I wonder how many ways there are to stop X?

Here is another:
sudo init 3

Depends on how your runlevels are set up. That won't work on a default Ubuntu desktop install. The only runlevels it works on in that case are 0, 1, and 6.

---

