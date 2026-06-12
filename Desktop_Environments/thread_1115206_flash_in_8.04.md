---
title: "flash in 8.04"
date: 2009-04-03
forum: Desktop Environments
---

### Post by andrea000 on 2009-04-03
I installed flash but ever time i go to watch a movie on hulu or utube 
nothing works could anyone tell me how to make it work or what i 
might be what i am doing wrong?

---

### Post by soomro on 2009-04-03
Can you please tell the process by which you are installing it?

---

### Post by taurus on 2009-04-03
How did you install flash-plugin?

---

### Post by andrea000 on 2009-04-03
the adobe web site then i picked the .deb for ubuntu 8.04 then
i installed it with the gkdeb installer

---

### Post by soomro on 2009-04-03
oh i installed the tar.gz version so i can't help you in that :(

and my version is 8.10 sorry did not see it D:

---

### Post by taurus on 2009-04-03
Which web browser are you using?  Have you restarted or even rebooted your machine?

---

### Post by andrea000 on 2009-04-03
I have  restarted and rebooted i also checked the start up
to see if there is a place in there but nothing.I am 
running firefox 3

---

### Post by Giblet5 on 2009-04-03
Is your 8.04 a 64-bit install?

Flash is 32-bit only. You'll need the compatibility libraries if you're running 64 bit.

If you're on 32-bit:

Are you using FlashBlock? I think it's broken. Disable it and try YouTube/anyvid.

---

### Post by andrea000 on 2009-04-03
I am not using FlashBlock I installed flash from adobe

---

### Post by Giblet5 on 2009-04-03
> **andrea000 said:**
> I am not using FlashBlock I installed flash from adobe

Then maybe you're using a 64-bit install.

What's the output of
```
uname -a
```

If there's a 64 in there, you can try following the directions [in this post]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html").

There's also a link on there for installing Flash 10 on 32-bit linux, and you might get what you need there.

I used the tarball from Adobe, and it just worked. At least, after I disabled FlashBlock...

You could remove the Debian package and try the tarball, too.

---

### Post by andrea000 on 2009-04-03
I have did everything and still can't get flash i even 
installed the tarball still i can't get it installed and 
everything is up to date when i go to you tube firefox 
just goes black and i have to force firefox to shutdown.
I guess i will just install the non free from the repo's.

---

### Post by Giblet5 on 2009-04-04
> **andrea000 said:**
> I have did everything and still can't get flash i even 
installed the tarball still i can't get it installed and 
everything is up to date when i go to you tube firefox 
just goes black and i have to force firefox to shutdown.
I guess i will just install the non free from the repo's.

I thought that would work...

Sorry.

---

### Post by andrea000 on 2009-04-04
> **Giblet5 said:**
> I thought that would work...

Sorry.

it's not your fault but thank you for trying

---

