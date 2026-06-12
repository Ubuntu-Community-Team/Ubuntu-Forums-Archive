---
title: "Beryl installed, no effects at all"
date: 2007-05-22
forum: Desktop Effects &amp; Customization
---

### Post by the_axiom on 2007-05-22
Hi, I followed this guide [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html) but still beryl wont work. The only thing I did different from the guide was that I used other repositories for fiesty.
Desktop Effects is activated, beryl-manager is on. Graphics drivers on. But there are no Beryl effects at all.
Anyone know whats the matter, please tell me? :D

---

### Post by Ateo on 2007-05-22
Try turrning desktop effects off since that runs Compiz and you're running Beryl. Might be some conflict there. If I remember correctly (from my gnome days), it's one or the other but not both.

---

### Post by the_axiom on 2007-05-22
> **Ateo said:**
> Try turrning desktop effects off since that runs Compiz and you're running Beryl. Might be some conflict there. If I remember correctly (from my gnome days), it's one or the other but not both.
I've tried and restarted, that didn't work.
Any suggestions?

---

### Post by the_axiom on 2007-05-23
bump

---

### Post by gamer_pro_2000 on 2007-05-23
If you're using an ATI video card, Beryl won't work.  I have an ATI card and I had similar problems.  What brand are you using?

---

### Post by the_axiom on 2007-05-23
I have ati radeon x1950xt. Yes it will work becouse I had it working about 1 week ago but I lost the guide I used...

---

### Post by eks on 2007-05-23
Beryl is more unstable with ATI, you need to run it over Xgl, and it need to be version 2.0, not 2.1 that is on the repositories.

And the ATI drivers don't support Xgl over two monitors.

If you are stuck with an ATI and you want effects I would recommend to stay just with compiz...



eks

---

### Post by the_axiom on 2007-05-24
Man you gotta be kidding, _**I just said I got it to work a week ago**_!!!!!!!

---

### Post by Ub1476 on 2007-05-24
Type in the terminal:

```
beryl
```

and show here what you get

---

### Post by ninja_in_pajamas on 2007-05-31
I'm having the exact same issue.  Using beryl/compiz and getting no effects.  Tried typing beryl in the terminal to see what I got, here's what it spit out.

[B]* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
[/B]

Any suggestions?

---

### Post by 213374U on 2007-05-31
Same problem here. ATI card. Have it active in the Restricted Device Manager. But no effects with Beryl. Fully installed and can access the manager and settings but no effects. Frustrating.

---

