---
title: "Need the kernel source"
date: 2006-01-19
forum: Desktop Environments
---

### Post by SuspiciouS on 2006-01-19
i've been working with kubuntu for a month now on my new laptop, and it is running great. What a great distro, but you already new that :)

I've been trying to install VMWare, because i need to run a win32 program, and wine wouldn't work, to bad. But, the VMWare-install needs my kernel source.

I updated my kernel using apt-get, and currently i'm running 2.6.12-10-686. I tried installing kernel-source using apt-get, but the source (the one i need) isn't there. Do i need another repository?

I tried to compile my kernel manually (downloaded the newest kernel from kernel.org), but that wouldn't work. Gives me lots of errors...

So, the question is:
Where do i get my kernel source?

---

### Post by az on 2006-01-19
[QUOTE=SuspiciouS]i've been working with kubuntu for a month now on my new laptop, and it is running great. What a great distro, but you already new that :)

I've been trying to install VMWare, because i need to run a win32 program, and wine wouldn't work, to bad. But, the VMWare-install needs my kernel source.

I updated my kernel using apt-get, and currently i'm running 2.6.12-10-686. I tried installing kernel-source using apt-get, but the source (the one i need) isn't there. Do i need another repository?

I tried to compile my kernel manually (downloaded the newest kernel from kernel.org), but that wouldn't work. Gives me lots of errors...

So, the question is:
Where do i get my kernel source?[/QUOTE]

To use the kernel source to compile a module like that would mean you have configured the source to match your running kernel.  You also need to make it build the headers.

Forget about the source since this is lengthy and complicated.  Just install the linux-headers package which corresponds to your running kernel.

linux-headers-2.6.12-10-686

You also need the toolchain to compile stuff.  Install build-essential.

Build essential uses gcc-4.0 for everything except the kernel.  The kernel was not buildable with gcc-4.0 at the time of release.  You need to install gcc-3.4 as well.

so, install

sudo apt-get install linux-headers-2.6.12-10-686 build-essential gcc-3.4
(or use synaptic)

---

### Post by SuspiciouS on 2006-01-19
wheee, VMware up&running :) tnx for the help :)

---

