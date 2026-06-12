---
title: "Installing VMWare Server - a slight snag..."
date: 2006-07-08
forum: Desktop Environments
---

### Post by elbowgeek on 2006-07-08
Hi all,

I am attempting to install VMWare Server, which is going well with the exception of a wee snag.  

It has taken me through all of the default settings which I've accepted.  However it has come to a prompt which asks:

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

However, as far as I can tell I don't have any relevant include directories on my system.  Is this the Ubuntu source code it's looking for?  If I don't have it on my system, which packages do I need to install it?

Many thanks for any help!

Cheers

Dennis

---

### Post by [S|G] on 2006-07-08
You need linux-kernel-headers

---

### Post by bohboh on 2006-07-08
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by elbowgeek on 2006-07-08
Thanks all, giving it a try now...

---

### Post by elbowgeek on 2006-07-08
Hmm.  I just entered that command and it said:
```

linux-headers-2.6.15-25-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So I seem to have it installed, but I'll be danged if I can find the directory that VMWare is asking for.

Any ideas, folks?

Again, appreciate all suggestions...

---

### Post by bohboh on 2006-07-08
Try /usr/src/linux

---

### Post by elbowgeek on 2006-07-08
> **bohboh said:**
> Try /usr/src/linux

That's my problem - the directory mentioned apparently doesn't exist, yet the files do live on my drive somewhere according to the installation command.

The above directory is the one that the VMWare installer is looking for by default, but it isn't in that location.

Again, any ideas?  Thanks...

---

### Post by bohboh on 2006-07-08
Do a /usr search:

```
sudo find /usr -name linux-headers-`uname -r`

```

---

### Post by elbowgeek on 2006-07-08
> **bohboh said:**
> Try /usr/src/linux

Ah finally did find the correct directory, it was under some rather odd name in the /usr/src directory.

However it bombed out at the point of doing something with VM Perl or something.  Back to the drawing board...

---

