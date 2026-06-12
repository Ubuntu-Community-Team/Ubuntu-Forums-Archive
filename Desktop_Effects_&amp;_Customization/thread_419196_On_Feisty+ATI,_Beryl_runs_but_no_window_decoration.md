---
title: "On Feisty+ATI, Beryl runs but no window decorations"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by djrobthaman on 2007-04-22
Hi,

Just installed feisty fresh.  Got beryl working on edgy without too much fuss, so thought it would go as well on feisty, but it doesn't seem to be working that way.  Most of beryl's features are working (the only thing I can complain about really so far when it comes to beryl is that I can't get the window previews to work).

I think I'm having a problem with emerald.  I uploaded a screenshot that shows what my windows look like.  For some reason I get the corners around the windows but not the "meat" of the border.  A weird thing is I can grab a hold of where the top border should be and mover the windows around as if it were there anyway.

Anybody know what I can do to fix it?

Thanks a lot,
Douglas

---

### Post by phibonoacci on 2007-04-23
Having same problem...

---

### Post by Stickymaddness on 2007-04-23
I've got an nvidia card and have the same problem! Also terminal opens as a white block!!

---

### Post by kostkon on 2007-04-23
The solution is simple:

Go to terminal and open the *xorg.conf* file:

```
gksudo gedit /etc/X11/xorg.conf
```

and add this line to the *Section "Device"* or the *Section "Screen"*:

```
Option         "AddARGBGLXVisuals"        "true"
```

and save the file.

This will solve your problem. Restart the X server with ALT+CTRL+BACKSPACE and you will be OK.

Additionally, you can add these two lines, they will improve the perfomance of your desktop:

```
Option         "DisableGLXRootClipping"   "true"
Option         "DamageEvents"             "true"
```


Also, you can add this line, but it is somewhat experimental and maybe you'll experience lockups:

```
Option         "RenderAccel"               "true"
```

---

### Post by kostkon on 2007-04-23
Sorry, I have to add that, **djrobthaman** I assumed that you have an nvidia graphics card.

But it will solve this problem for **Stickymaddness**.

---

### Post by djrobthaman on 2007-04-23
Hi there,

I saw that workaround and it looks like a lot of people have got it to work for them.  I guess I should have been a bit more specific in my subject.  I have an ATI X1300.  Is there anything I can do for that setup?

THanks

---

### Post by Stickymaddness on 2007-04-23
> **kostkon said:**
> 
But it will solve this problem for **Stickymaddness**.

Awesome!! Thank you!! You solved something that's been bugging me allot!! 

Quick n00b question, what exactly do those lines do? Besides fixing everything :p

---

