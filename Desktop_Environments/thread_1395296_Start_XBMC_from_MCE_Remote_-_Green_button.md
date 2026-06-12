---
title: "Start XBMC from MCE Remote - Green button"
date: 2010-01-31
forum: Desktop Environments
---

### Post by WallaceTech on 2010-01-31
Hi Guys.

I am running 64bit Ubuntu and have just installed XBMC and the install has gone great so far. Easy to set up and configure and all my media now works.

I have installed lircrc and my remote works when in XBMC.

I have created a file .lircrc in my home share and added the following

begin
        remote = mceusb
        button = Home
        prog   = irexec
        repeat = 0
        config = /usr/share/applications/XBMC Media Center
end

When i press the green button the remote it is not opening XBMC

Any ideas as to where i have gone wrong?

Thanks in advance

Craig

---

### Post by WallaceTech on 2010-01-31
Just to update.

It was my path that was wrong. it should have been

begin
        remote = mceusb
        button = Home
        prog   = irexec
        repeat = 0
        config = /usr/bin/xbmc
end

---

### Post by notti73 on 2010-04-26
Thanks for sharing, WallaceTech.

Mind if I ask what brand & model of the MCE remote control you're using for XBMC?

Cheers,

---

### Post by TheAbu on 2010-12-29
Nice tip, thank you :)

---

### Post by VTCop on 2012-11-25
Thankyou very much

---

### Post by nothingspecial on 2012-11-25
Old Thread.

Closed.

---

