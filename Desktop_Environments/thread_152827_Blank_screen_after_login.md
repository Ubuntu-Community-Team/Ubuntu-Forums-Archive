---
title: "Blank screen after login"
date: 2006-03-30
forum: Desktop Environments
---

### Post by AndrewJ on 2006-03-30
Hi there,

When I log into Breezy, the gnome desktop does not seem to start and I am left with a brown screen and a mouse.

How it began:
Initially I was having errors about my permissions on ~/.dmrc (which I think I fixed with sudo chmod 740 ~ and sudo chmod 644 ~/.dmrc)
These permission errors first started to pop up after I installed Cedega.

I have tried removing Cedega, I tried a dpkg-reconfigure on gdm also.

I'm running out of ideas ](*,) Any help appreciated.

---

### Post by AdotB on 2006-03-31
Are you using a video card?

I had the same problem and when i dpkg-reconfigured, the driver i needed wasn't the default, i had to select it from the list (after finally figuring out which on i needed and installing it). That worked for me.

---

