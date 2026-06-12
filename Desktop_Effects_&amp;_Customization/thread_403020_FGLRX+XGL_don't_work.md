---
title: "FGLRX+XGL don't work"
date: 2007-04-06
forum: Desktop Effects &amp; Customization
---

### Post by Elv13 on 2007-04-06
Hi, recently i tried to install beryl on my desktop. I have a radeon 9200, fglrx .28 (last with the support for my card), gentoo and radeon 7.1 (last with the support for .28 version of fglrx). When i tried to to install XGL, everything was fine, but when i tried to run it in full screen, a widows like kcontrol was taking more then 1 minute to draw!!!. On the top of that, screensaver like flurry was working perfectly! 50 fps on screensaver and 3d game but 1/60 of fps on the desktop. Of cource, beryl did not load on that. AIGLX and Composite are disable. It is not a big problem, i switched to open source driver and made a separate session with an other xorg.conf for game and mythtv.

But yesterday, i installed Ubuntu Edgy 32bit on my firend computer (dell inspirion, core 2 duo, radeon x1400) and it did perfectly the same thing. I followed the official guide from ubuntu fr doc. Same thing, windows took enormous amount of fps to draw, even the mouse was lagging. I am asking now why? How can i fix that (i can not use open source driver on a x1400)?

---

### Post by Paerez on 2007-04-06
Your problem is that XGL is working fine on fglrx, but Beryl is not controlling the desktop. If you don't use a compositing manager on a compositing X server, then it runs really slow (for general applications).

Run "beryl-manager" in the terminal and enable beryl using the Tray Icon, then post what happens in the terminal.

---

### Post by Elv13 on 2007-04-06
i get error like no texture extension, no glx found and thinks like that

---

### Post by Elv13 on 2007-04-07
bump...

---

### Post by slavik on 2007-04-07
try running beryl-xgl :)

---

### Post by phoenixfirebird on 2007-04-08
I'm having problems with beryl in xgl as well, but when I type "beryl-xgl" I get a bash error.  When I type "beryl" I get:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

and then I lose all the desktop effects.  Now, I never had the cube, but now I lose everything else.

---

### Post by Elv13 on 2007-04-08
it is was i get too

---

### Post by bdogg64 on 2007-04-09
beryl from the repos does not include beryl-xgl, so you will need to downgrade your version of beryl to 0.2.0 and run

```
beryl --use-copy
```

---

### Post by Elv13 on 2007-04-09
What about compiz, will it work?

---

### Post by bdogg64 on 2007-04-09
> **Elv13 said:**
> What about compiz, will it work?

I got compiz working under XGL, but something was wrong with my titlebars and I didn't mess with it enough to fix that, so I just stuck with beryl once I got it working.

---

