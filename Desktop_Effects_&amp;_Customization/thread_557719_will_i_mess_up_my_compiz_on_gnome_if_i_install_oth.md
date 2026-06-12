---
title: "will i mess up my compiz on gnome if i install other desktop environments?"
date: 2007-09-23
forum: Desktop Effects &amp; Customization
---

### Post by tim202 on 2007-09-23
Hey guys.

So i finally got compiz looking all hot on my Gnome desktop, and of course, i'm getting bored with it and want to fiddle around with Xfce and maybe fluxbox.  If i switch to another DE, i'm not going to screw up my current settings for compiz with Gnome, am I?  

Sorry if this is a dumb one, i just want to look before i leap :)

Thanks in advance as usual
TIM

---

### Post by HokeyFry on 2007-09-23
i dont think so. i installed enlightenment from the repos and i have no issues, though i havent exactly ran enlightenment yet. i highly doubt it would screw anything up though, because you should be able to choose which DE to load up once at the login screen via the sessions button

---

### Post by Forlong on 2007-09-23
> **tim202 said:**
> i'm getting bored with it and want to fiddle around with Xfce and maybe fluxbox. 
Xfce is a desktop environment and Fluxbox is a window manager - just like Compiz, so you can't use Fluxbox and Compiz at the same time.
> **tim202 said:**
> If i switch to another DE, i'm not going to screw up my current settings for compiz with Gnome, am I?
If you are using the gconf backend (that's definitely the case if you are not running Compiz Fusion) there's a tiny possibility for that. If you are using Compiz Fusion I recommend using the flat-file backend. This is totally DE-independent.

---

