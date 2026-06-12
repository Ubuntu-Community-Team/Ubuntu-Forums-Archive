---
title: "High CPU when scrolling in Opera, Firefox and others"
date: 2008-06-02
forum: Desktop Environments
---

### Post by miggols99 on 2008-06-02
My laptop is getting really hot and uncomforable to keep on my lap when I start scrolling in any web browser. That means Firefox, Opera and Konqueror for me. Xorg starts using around 40% CPU which is quite high. When I stop scrolling Xorg goes back to being around 2% CPU. The problem persists even if I turn off smooth scrolling. I don't want my laptop to be burning my lap every time I use my web browser! Is there any way I can fix this?

I have an integrated Intel graphics card and Intel Core 2 Duo 1.5GHz processor with 1GB memory running 64bit. Surely it should work fine on a modern system like mine?

---

### Post by xfceuser on 2008-06-02
sometimes this because of your graphics card is not configured properly, so not having "direct rendering" and all the graphics load is on the cpu. to check this type this command:
```

glxinfo | grep "direct rendering"

```

---

### Post by miggols99 on 2008-06-02
```
michael@michael-laptop:~$ glxinfo | grep "direct rendering"
direct rendering: Yes
```

---

### Post by xfceuser on 2008-06-02
ok, try this command and see how much frame rate you get ...
```

glxgears

```

---

### Post by miggols99 on 2008-06-02
I'm getting about 841 FPS...

---

### Post by xfceuser on 2008-06-03
so your direct rendering works fine ...

---

### Post by imneo on 2008-06-03
this is a known problem , i found the solution here:

[http://scripts-net.com/viewtopic.php?f=17&t=64#p81](http://scripts-net.com/viewtopic.php?f=17&t=64#p81)

tell us if it helped you.

---

### Post by miggols99 on 2008-06-03
> **imneo said:**
> this is a known problem , i found the solution here:

[http://scripts-net.com/viewtopic.php?f=17&t=64#p81](http://scripts-net.com/viewtopic.php?f=17&t=64#p81)

tell us if it helped you.
Can you copy the solution here? I don't want to sign up to another forum...

---

### Post by imneo on 2008-06-03
sorry but it would not be fair...

---

### Post by miggols99 on 2008-06-04
That doesn't seem to have worked...

---

### Post by unimatrix on 2009-02-07
That link has nothing to do with scrolling. And it's ATI-specific. I've got the same problem on nVidia.

Any solutions? How can simple scrolling be such a problem? It works perfectly on Windows.

---

### Post by blackgr on 2009-02-10
Maybe you should try the 32bit version.

---

### Post by sugardeath on 2009-05-07
I am using the 32-bit version.  It lags X like crazy...

---

### Post by roderikk on 2009-11-25
Hm, I got 6000FPS with glxgears and nvidia 6600. Upon opening big pages though scrolling on Karmic was really slow so I put in the options into my Xorg and logged out and logged in and it seems to work better now. Much better actually. So these options don't seem to be ati specific, or something else is at work.

---

### Post by Usufruct on 2009-11-25
I have been trying to reproduce this issue for some time, and I haven't been able to do it.

---

