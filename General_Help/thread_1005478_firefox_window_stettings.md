---
title: "firefox window stettings"
date: 2008-12-08
forum: General Help
---

### Post by jonaskn on 2008-12-08
Hi
My firefox browser has started to startup in some sort of semi fullscreen mode. When I start firefox it covers the taskbars and the "window head" is gone, it comes back to normal if I press F11 twice. I recently reinstalled Ubuntu, and at first it started up normally, but after a few weeks it started cover the taskbars.
Does anyone have an idea on how to change it back?

Jonas

---

### Post by gjoellee on 2008-12-08
> **jonaskn said:**
> Hi
My firefox browser has started to startup in some sort of semi fullscreen mode. When I start firefox it covers the taskbars and the "window head" is gone, it comes back to normal if I press F11 twice. I recently reinstalled Ubuntu, and at first it started up normally, but after a few weeks it started cover the taskbars.
Does anyone have an idea on how to change it back?

Jonas
this is a known bug by the Zippex Linux developers found with GDM (Gnome Display Manager), or GDM related packages. This does not happen with KDM (KDE Display Manager). (This [COLOR=Red]might [/COLOR]by Mozilla's fault and not GNOME)
[COLOR=Red]
[COLOR=Black]You can try this:[/COLOR]
[/COLOR]Installing KDM and enabeling it as default will solve this problem.

```
sudo apt-get install kdm
```while installing you will get question for if you want either GDM or KDM to be enabled by default choode KDM. After this do a reboot.

(The same will fix some fullscreen mode bugs in several games as well. Ex: Urban Terror)

---

### Post by flclvr8780 on 2008-12-08
is there something with this that would cause the text or video on a site to overlap as well.  it doesnt happen on all sites just some.  this site is an example. [http://www.aeroforcetech.com/](http://www.aeroforcetech.com/) top and bottom are overlapped as well as a lot of the other pages on it

---

### Post by caro on 2008-12-29
> **jonaskn said:**
> Hi
My firefox browser has started to startup in some sort of semi fullscreen mode. When I start firefox it covers the taskbars and the "window head" is gone, it comes back to normal if I press F11 twice. I recently reinstalled Ubuntu, and at first it started up normally, but after a few weeks it started cover the taskbars.
Does anyone have an idea on how to change it back?

Jonas

Firefox just started doing that for me too.  Very frustrating. I am on 8.10 and this has never happened before (since 7.04).  Anyone know how to fix it?

---

### Post by fooman on 2008-12-29
> **caro said:**
> Firefox just started doing that for me too.  Very frustrating. I am on 8.10 and this has never happened before (since 7.04).  Anyone know how to fix it?

press f11 to go fullscreen and f11 again to get to a normal size screen.

next click the unmaximize button.

close firefox.

reopen firefox.

maximize firefox.

done...should be fixed for good.

---

### Post by caro on 2008-12-29
> **fooman said:**
> press f11 to go fullscreen and f11 again to get to a normal size screen.

next click the unmaximize button.

close firefox.

reopen firefox.

maximize firefox.

done...should be fixed for good.

Thanks fooman!  I had tried just about everything else I could think of for the past 24 hours.  I had seen this once before and couldn't remember how to correct it.  :oops:

---

