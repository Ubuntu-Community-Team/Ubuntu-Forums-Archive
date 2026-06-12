---
title: "XGL with Intel?"
date: 2006-10-07
forum: Desktop Environments
---

### Post by luckylucky on 2006-10-07
Hi everyone,

I have a handful of computers, but unfortunately every single one of them has an Intel video card.  All of this XGL & Compiz stuff is soo cool I'd love to have it running on my machines.  Somehow I've managed to get it working a couple of months ago with SuSe, but have since decided to stick with Ubuntu.  I've scoured the net looking for how to tips but everywhere I turn I end up with Nvida & ati specifics for XGL.  I've found just a couple of intel pages, but I tried the tutorials unsuccessfuly.

**Does anyone know of a good site to go to for people with intel video cards wanting to run XGL in Ubuntu?**

The next computer I buy will DEFINETELY have Nvidia inside.

Thanks for any directional pointers.

---

### Post by Buffalo Soldier on 2006-10-07
I followed the [Howto compiz + aiglx on edgy](http://gandalfn.wordpress.com/howto-compiz-aiglx-on-edgy/). And it works smoothly on my humble 855 Integrated Intel graphic card.

```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

---

### Post by luckylucky on 2006-10-07
Thank you!  I'll give it a try soon.

---

### Post by DarkN00b on 2006-10-07
> **Buffalo Soldier said:**
> I followed the [Howto compiz + aiglx on edgy](http://gandalfn.wordpress.com/howto-compiz-aiglx-on-edgy/). And it works smoothly on my humble 855 Integrated Intel graphic card.

```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

I have the same chipset-on Dapper. I followed the directions [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX") and ended up with a broken x session = no gui boot.  Twice. ](*,) :) 

I hear it is easier on Edgy.  I'm going to wait for the final release then try AIGLX/Beryl.

---

### Post by luckylucky on 2006-10-07
What are AIGLX/Beryl and how are they different than XGL/Compiz?  Why would you use them instead?

---

### Post by DarkN00b on 2006-10-07
I think I remember reading that they work better w/ Intel chipsets. They basically add the same features as XGL/Compiz.

Of course when I actually try to do this, I'll study up some more to make sure I get it right. :D

---

### Post by Buffalo Soldier on 2006-10-08
> **DarkN00b said:**
> I think I remember reading that they work better w/ Intel chipsets. They basically add the same features as XGL/Compiz.

Of course when I actually try to do this, I'll study up some more to make sure I get it right. :D

You forgot one more combination, "AIGLX/Official Compiz".

---

### Post by benjaminzsj on 2006-10-15
> **DarkN00b said:**
> I have the same chipset-on Dapper. I followed the directions [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX") and ended up with a broken x session = no gui boot.  Twice. ](*,) :) 

I hear it is easier on Edgy.  I'm going to wait for the final release then try AIGLX/Beryl.

Seems like my problem, every time I start beryl-manager, it stops X and takes me to login screen. Does yours run on a laptop?

---

