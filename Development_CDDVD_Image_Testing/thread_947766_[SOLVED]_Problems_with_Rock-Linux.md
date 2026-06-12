---
title: "[SOLVED] Problems with Rock-Linux"
date: 2008-10-14
forum: Development CD/DVD Image Testing
---

### Post by JeyPeyy on 2008-10-14
So, I'm trying to do my own linux-distro as a project for school. I found rock-linux, so I wanted to give it a try. I downloaded the source and tried to do as described on [http://www.rocklinux.org/wiki/Building](http://www.rocklinux.org/wiki/Building) : I "cd" to the source-directory and ran 
> ./scripts/Config -cfg mydistribution

And I got the message 
> Creating configuration script.
But there it hangs, so I "ctrl+c" to stop it, and then I get the message
> Running ROCK Linux TRUNK configuration ...
./scripts/Config: line 143: enable: cannot open shared object src/config_helper.so: src/config_helper.so: wrong ELF class: ELFCLASS64
4


I've tried this on openSUSE too, and it worked fine. But I think Ubuntu is a far better distro otherwise. So please, help me with this one!

---

### Post by JeyPeyy on 2008-10-19
Bump!

---

### Post by JeyPeyy on 2008-10-21
Anyone? Please

---

### Post by gmclachl on 2008-10-23
Are you running 64-bit ubuntu?

---

### Post by JeyPeyy on 2008-10-24
> **gmclachl said:**
> Are you running 64-bit ubuntu?

I did, but I changed to 32 because I also thought that was the problem. But apparently it didn't do it.

---

