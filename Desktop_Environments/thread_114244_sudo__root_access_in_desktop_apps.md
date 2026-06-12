---
title: "sudo / root access in desktop apps"
date: 2006-01-08
forum: Desktop Environments
---

### Post by virtadept on 2006-01-08
Hi!

SInce I'm not that good at shell and since I don't know all commands available for editing and decompressing files I was wondering if it's possible to launch the file roller with sudo or something?

I Often find it frustating that I'm suppose to copy a file to a place which required root access and then edit the file or decompress it. Just recently I downloaded the Linux source with the Synaptic package manager. The source was placed under usr/src/ as a compressed file. I'm now attempting to deceompress the file so I can compile another project which requires access to the kernel source. Any good guidelines?

There isn't any built-in help for the shell and shell commands in Ubuntu?

Regards
VirtAdept

---

### Post by FarEast on 2006-01-08
It is not so difficult to decompress tarballs;) .
The kernel source probably has the extention '.tar.bz2'.
Then you have only to do the following:

$ sudo tar xjvf linux-source-2.6.*.tar.bz2

Note: If it is tiresome to type a long file name, hit [Tab] key
after entering some letters.

---

