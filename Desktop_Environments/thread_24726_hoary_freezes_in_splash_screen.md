---
title: "hoary freezes in splash screen"
date: 2005-04-08
forum: Desktop Environments
---

### Post by nalle on 2005-04-08
I have sent the following to bugzilla and decided to add it here in case anybody has the solution/same problem.

I looked through the forums and even though there were similar freezes, none had exact same things happening. And by looking I mean first searching with about 10 different keywords, then going through the hoary installation and desktop areas.

With Warty to Hoary upgrade and Hoary fresh install, after login, the ubuntu
loader screen shows (but doesn't load any programs) and after a while the whole
system freezes: no mouse, no keyboard and after a while longer the computer
starts to wheeze as if it is trying to find something on the hardrive (but a bit
more sound than normal).
I have updated the system and when I first just upgraded from warty, I fixed
xorg configuration and blacklisted modules that were giving error messages, but
that didn't help. With the fresh install, there have been no such problems. Just
the computer freezing.
I can login using ctrl+alt+F1 from the login screen, so loading the desktop
programs seems to be the problem. And it is a problem with Hoary, since warty
worked fine.
The computer has
Asus motherboard P5GD1-VM with built in sound (doesn't work) and ethernet
Intel Celeron D processor
Ati Radeon X600

Almost forgot: I'm using Hoary 5.04 with 2.6.10 kernel

======= ](*,) 
[COLOR=Teal]Life is hard[/COLOR]

---

### Post by Amaranth on 2005-04-08
Are you using the 2.6.11 kernel? If so you should switch back to 2.6.10 unless you have a very good reason for using 2.6.11 (drivers). The version of 2.6.11 that comes with hoary is very unstable, that's why it's only in universe.

---

### Post by nalle on 2005-04-08
With updgrade from Warty,  the kernels I tried were  2.6.8 and 2.6.10. Neither worked.
with clean install I used 2.6.10, I think, since I didn't make changes to the repositories before updating.

---

### Post by gylf on 2005-04-08
[QUOTE=nalle]I have sent the following to bugzilla and decided to add it here in case anybody has the solution/same problem.

I looked through the forums and even though there were similar freezes, none had exact same things happening. And by looking I mean first searching with about 10 different keywords, then going through the hoary installation and desktop areas.

With Warty to Hoary upgrade and Hoary fresh install, after login, the ubuntu
loader screen shows (but doesn't load any programs) and after a while the whole
system freezes: no mouse, no keyboard and after a while longer the computer
starts to wheeze as if it is trying to find something on the hardrive (but a bit
more sound than normal).
I have updated the system and when I first just upgraded from warty, I fixed
xorg configuration and blacklisted modules that were giving error messages, but
that didn't help. With the fresh install, there have been no such problems. Just
the computer freezing.
I can login using ctrl+alt+F1 from the login screen, so loading the desktop
programs seems to be the problem. And it is a problem with Hoary, since warty
worked fine.
The computer has
Asus motherboard P5GD1-VM with built in sound (doesn't work) and ethernet
Intel Celeron D processor
Ati Radeon X600

Almost forgot: I'm using Hoary 5.04 with 2.6.10 kernel

======= ](*,) 
[COLOR=Teal]Life is hard[/COLOR][/QUOTE]


On my MSI board I had almost the same problem.  I just disabled USB 2.0 in the BIOS and it resolved the problem.  Might give that a try.

---

### Post by nalle on 2005-04-10
I fixed it with the fglrx drivers and editing xorg.conf to fit my monitor better.
- in warty I had xorg, since xf86 didn't work at all, so I hadn't thought that I'd need to redo my confs when upgrading

I think the problem was the same as some nvidia cards seemed to have with xorg overworking itself

---

