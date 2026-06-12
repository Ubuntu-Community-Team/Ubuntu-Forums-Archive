---
title: "Best eye candies for those who can't run Beryl and Compiz?"
date: 2007-04-12
forum: Desktop Effects &amp; Customization
---

### Post by wersdaluv on 2007-04-12
My laptop, as well as many other laptops, can't run Beryl and Compiz.

```
glxinfo | grep render
libGL warning: 3D driver claims to not support visual 0x46
direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome (PM8x0/CN400) 20060710

```

Now, if we want a fancy desktop, what are the best things we can do?

---

### Post by kelbizzle on 2007-04-12
I use enlightenment on my laptop it looks really good.
[http://www.enlightenment.org/](http://www.enlightenment.org/)

---

### Post by kerry_s on 2007-04-12
Can you use transparency?
Have you tried 3ddesktop?
Try looking through-> [http://www.kde-look.org/](http://www.kde-look.org/) <-For ideas

---

### Post by wersdaluv on 2007-04-12
> **kelbizzle said:**
> I use enlightenment on my laptop it looks really good.
[http://www.enlightenment.org/](http://www.enlightenment.org/)

That's a good option for those who want eye candies but can't run Beryl or Compiz. Thanks for sharing.

It's just that, in my case, I want to use only GNOME or KDE.

---

### Post by wersdaluv on 2007-04-12
Thanks for mentioning 3ddesktop.

I found [this howto]("http://ubuntuforums.org/showthread.php?t=59461") for that.

Is there a more updated thing like this? I presume, 3ddesktop is an old app.

Also, how can I enable transparency without Compiz or Beryl?

---

### Post by kerry_s on 2007-04-12
Eye candy existed before compiz and beryl you just got to look around.

I believe back in the day we used xcompmgr for transparency.

I wouldn't worry about transparency, it has always been slow anyway.

There were many old school ways to make your desktop look good. I just can't remember. Sorry, brain damage(work related, fell 3 stories).

You might also want to look at skippy.

also just to let you know, everything i mention will be in the repos, so you can use synaptic or apt-get to install it, that way if you don't like it you can easily remove it.

---

### Post by lsutiger on 2007-04-12
I installed 3d desktop but I get an error when I run in terminal:
```
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

```
And nothing happens...How to I configure hardware acceleration?
Thanx in Advance!

---

### Post by FuturePilot on 2007-04-13
You could also try out the XFCE desktop. It has a built in compositor. It will give you simple eye candy. You can get transparencies as well as some simple drop shadows.

---

### Post by Death_Sargent on 2007-04-13
Yo might also want to try installing propreitary drivers 

Beryl has a walkthrough for this

Mesa will only work with AIGXL ands thats only on certain ATI cards.

Your best bet is to properly install proprietary drivers and make an xgl session.

---

### Post by wersdaluv on 2007-04-13
> **Death_Sargent said:**
> Yo might also want to try installing propreitary drivers 

Beryl has a walkthrough for this

Mesa will only work with AIGXL ands thats only on certain ATI cards.

Your best bet is to properly install proprietary drivers and make an xgl session.

The problem is, my video card is VIA Unichrome S3 and it can never run beryl or compiz.

Also, laptops like mine, it's impractical to use most eye candies because they make our laptops run real slow so we really need to pick the simplest eye candies. Imagine- even 3D Desktop makes my laptop hang!

---

### Post by themtx on 2007-04-13
2nded on that.  My work machine has an onboard intel 915G (w/a whopping 8MB of RAM) and will only do Beryl at 1024x768 w/mergedfb - as I have 2 panels.

XFCE w/compositor / transparency / shadows runs really well on 2 panels at 1280x1024 (2560x1024 virtual).  So, I'll live without a cube but better resolution and performance...

---

