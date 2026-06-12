---
title: "Desktop effect can't be enabled"
date: 2008-03-16
forum: Desktop Environments
---

### Post by kiroro on 2008-03-16
I have a Nividia 8800 GT and 4G memory. System is 7.10 64-bit fresh install.
When I go to system-appearance-visua effect, it tells me 'Desktop effect can't be enabled'. Am I missing something to make it work?

---

### Post by overdrank on 2008-03-16
> **kiroro said:**
> I have a Nividia 8800 GT and 4G memory. System is 7.10 64-bit fresh install.
When I go to system-appearance-visua effect, it tells me 'Desktop effect can't be enabled'. Am I missing something to make it work?

Hi and have you installed the drivers for the nvidia graphics card? May I suggest Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by kiroro on 2008-03-16
> **overdrank said:**
> Hi and have you installed the drivers for the nvidia graphics card? May I suggest Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Yes. I already installed the newerst driver from Nvidia website.

---

### Post by angry_johnnie on 2008-03-17
Has your graphics card been blacklisted?
If it has, there is a workaround.
open a terminal and type this:

```
SKIP_CHECKS=yes compiz --replace & disown
```

That will enable the desktop effects.

However, you must keep in mind that graphics cards get blacklisted for a reason, and the performance might not be optimal.

---

### Post by kiroro on 2008-03-19
> **angry_johnnie said:**
> Has your graphics card been blacklisted?
If it has, there is a workaround.
open a terminal and type this:

```
SKIP_CHECKS=yes compiz --replace & disown
```

That will enable the desktop effects.

However, you must keep in mind that graphics cards get blacklisted for a reason, and the performance might not be optimal.

How can I find out if my card is blacklisted? It's a Nvidia 8800GT.

---

### Post by angry_johnnie on 2008-03-23
> **kiroro said:**
> How can I find out if my card is blacklisted? It's a Nvidia 8800GT.


The only way I can think of is to run compiz from terminal and see what the output is.  There may be another way to find out, but that just beats me :-)  

There was  a sticky thread about this:

[http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112)


You could still try the SKIP_CHECKS thing just to see if it works.

---

