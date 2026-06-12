---
title: "beryl not working"
date: 2007-02-14
forum: Desktop Environments
---

### Post by error404 on 2007-02-14
Hello, I follow one of those guides to install beryl in a pc (ati)... but it's not working

this is what get:

desktop:~$ beryl
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

any ideas?

---

### Post by aliyanage on 2007-02-14
I had a problem when starting beryl as well, after the installation that is. I don't really know whether it will solve anything but it's worth trying.

Instead of typing

```
beryl
```

to start, I used

```
beryl-manager
```

which made it work...

---

### Post by error404 on 2007-02-14
beryl starts but it seems that it can't handle the graphics so it goes back to gnome

---

### Post by darkfame on 2007-02-14
It sounds like you're missing this in your xorg.conf file:

Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by bvanaerde on 2007-02-14
> **error404 said:**
> Detected xserver                                : AIGLX

ATI doesn't work (well) with AIGLX. You should use XGL instead.
Instead of using *some* guide, you should use *[the]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu")* guide for installing Beryl ;-)

---

### Post by satchelpig on 2007-02-24
> ATI doesn't work (well) with AIGLX. You should use XGL instead.
Instead of using some guide, you should use the guide for installing Beryl 

Well, here's the thing -- I am having this exact same problem and am having it AFTER I have installed XGL.  Is there something I have to do to disable AIGLX in favor of XGL?

By the way, I am using that exact guide you linked to.  What gives?

---

