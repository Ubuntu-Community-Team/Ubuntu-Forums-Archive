---
title: "How to get steam games up and going?"
date: 2017-12-22
forum: Gaming &amp; Leisure
---

### Post by michael14 on 2017-12-22
I tried Ubuntu in a Virtual Box the other day, and installed everything correctly, went to software centre and downloaded the steam installer, I then opened a terminal and typed
```
sudo steam
```
I went through the installation process, signed into my account tried to download undertale to see if it works on Ubuntu like it does in Windows.. Upon launch it just closed instantly.. Is there any packages that I should install to get them all working? Any ideas?

---

### Post by DuckHook on 2017-12-22
Your first and biggest mistake was launching steam with sudo. ***You must not run steam in the root account.*** This is just begging for trouble. In general, stop the atrocious Windows habit of elevating to superuser privileges every time something doesn't immediately work. This habit is one of the many reasons that Windows is such a malware gong show. In the Linux-sphere, it is almost never necessary to run anything with sudo except maintenance and system commands. Games and apps: never.

Your second mistake is trying to run steam inside a VM. A VM is a very resource-challenged environment that has trouble running the basic Ubuntu desktop alone, never mind an app as resource-intensive as most games are these days.

If you must have Windows installed, and also want to use Steam under Ubuntu, then the best solution is to dual boot. Steam needs to run on a true bare metal environment under Ubuntu. It's no surprise that a VM will kill it. I suppose that it's possible to configure the VM with all sorts of pass-throughs, but now we're talking about serious wizardry and I wouldn't have a clue how to do that in Windows anyway. You would have better luck finding out on some Windows forum.

You might want to start your troubleshooting by just launching steam ***(without sudo!)***. I really don't know what the point is in trying this, but it may prove academically interesting. Even if it launches, don't expect to be gaming. At best, things will run like molasses. At worst, you will just crash the VM.

---

### Post by tenshinoneko2 on 2017-12-24
I dunno which version is the one officially supported by Steam but it must likely be 16.04 since it's an LTS release.

Have you tried running that one?

---

