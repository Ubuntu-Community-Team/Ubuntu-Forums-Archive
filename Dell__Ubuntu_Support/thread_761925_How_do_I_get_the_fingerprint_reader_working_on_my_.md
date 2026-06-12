---
title: "How do I get the fingerprint reader working on my XPS M1530?"
date: 2008-04-21
forum: Dell  Ubuntu Support
---

### Post by jespdj on 2008-04-21
So far, Ubuntu 8.04 (64-bit) [works great]("http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530") on my XPS M1530.

However, I have not yet gotten the fingerprint reader to work for logging in. I read the [page about thinkfinger]("https://wiki.ubuntu.com/ThinkFinger") in the Ubuntu wiki, and installed the package thinkfinger-tools and edited /etc/pam.d/common-auth as described there.

However, on the GDM login screen nothing happens when I swipe my finger when it asks for the password. The GDM screen also just says "Password:" and not "Password or swipe finger:" (as I think it's supposed to say).

The test (with sudo tf-tool --acquire) works without problems.

What do I have to do to get the fingerprint reader working?

---

### Post by jespdj on 2008-04-22
Bump! Does this get my post back in the new forum?

Is nobody using the fingerprint reader on their M1530?

---

### Post by jbeynon on 2008-04-22
hi jespdj....

i can't answer your question but i notice in your footer you list you're running ubuntu 8.04 64 bit on your XPS1530 - I have the same spec machine - is it really 64 bit capable?

---

### Post by adw on 2008-04-22
Hi, 
i've got the m1330 with the finger reader.
Im not sure if its the same on the 1530, but im going to assume thats the case.
When i last installed 8.04, i didnt get the "swipe finger" in login either, but it was there after a complete reboot- so unless you've done that( and then im sorry i couldnt help), it should be there upon a fresh login.

(P.S. restarting just x did not cut it...)

---

### Post by jdelaros1 on 2008-04-23
Try the following:

#
# /etc/pam.d/common-auth 
#
#auth   requisite       pam_unix.so nullok_secure
auth    sufficient      pam_thinkfinger.so
auth    required        pam_unix.so try_first_pass nullok_secure
auth    optional        pam_smbpass.so migrate

---

### Post by thecure on 2008-04-23
Would this be any help?

[tp://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html]("http://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html")

[URL="http://reactivated.net/fprint/wiki/Main_Page"]
http://reactivated.net/fprint/wiki/Main_Page[/URL]

---

### Post by zzottt on 2008-04-28
> **thecure said:**
> Would this be any help?

[tp://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html]("http://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html")

[URL="http://reactivated.net/fprint/wiki/Main_Page"]
http://reactivated.net/fprint/wiki/Main_Page[/URL]

thanks man that works great on my HP/Compaq 6910p

:KS

---

