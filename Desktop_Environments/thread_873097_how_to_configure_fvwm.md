---
title: "how to configure fvwm?"
date: 2008-07-28
forum: Desktop Environments
---

### Post by conphuzed on 2008-07-28
here are the instructions (this is for univac's config):

```
Default running on 1280x1024 resolution
Requires:
 imlib2
 imageshack(convert)
 urxvt
 trayer
 Patches(for fvwm: http://abdn.ac.uk/~u15dm4/fvwm/)

Put IMAPTalk.pm from misc in /etc/perl/Mail
Put Com.pm Cached.pm Simple.pm in /etc/perl/Weather
Conf uses fonts: Dejavu, Verdana, Arial, Aquafont
Set your variabled in fvwm2rc.variables
Change variables in scripts/weather.pl and scripts/weather-dock.pl
```

can someone help me out w/ this? what/where are all the .pm files? also what do the last 2 lines mean? thanks from a n00b!

---

### Post by PadreSol on 2008-07-30
Try installing fvwm-crystal

apt-get install fvwm-crystal

Then select fvwm-crystal for your session next time you login.

I am still trying to figure out how to set the volume and suspend the laptop, but the other stuff works well.

Also using mrxvt.

---

### Post by x1a4 on 2008-07-30
See the [FVWM Documentation]("http://fvwm.org/documentation/") including the [FAQ]("http://fvwm.org/documentation/faq/#3.") and the FVWM man page on how to configure FVWM.

*.pm files are usually PERL modules.

The last two lines mean that you should set your variables in files fvwm2rc.variables, scripts/weather.pl and scripts/weather-dock.pl


> **PadreSol said:**
> Try installing fvwm-crystal
FVWM-Crystal is **NOT** FVWM.  It's an entirely different GUI which used FVWM as its window manager when work on it began.  Since than FVWM-Crystal's window manager evolved to be quite different from FVWM.

---

### Post by PadreSol on 2008-07-30
> **x1a4 said:**
> 
FVWM-Crystal is **NOT** FVWM.  It's an entirely different GUI which used FVWM as its window manager when work on it began.  Since than FVWM-Crystal's window manager evolved to be quite different from FVWM.

I don't think that you meant to be wrong, but it seems like you are.

I see this (and others like this) from ps:

 /usr/lib/fvwm/2.5.24/FvwmCommandS 10 7 /usr/bin/../share/fvwm-crystal/fvwm/recipes/Default 0 8

I read the docs about fvwm-crystal and it's just some pre-configured fvwm stuff.  Saves lots of time fiddling around with fvwm setup.

---

### Post by Sorivenul on 2008-08-27
From my understanding, and this may also be incorrect, FVWM-Crystal is actually more or less a layer on top of FVWM.  FVWM is a dependency itself, so that makes FVWM's dependencies involved as well.  Crystal just adds some nice extra features and some eye-candy off the bat for a lightweight WM.  I suggest checking out the main website at [http://www.fvwm.org](http://www.fvwm.org) for getting started with configuration.  Also, I believe Linux News did a couple of articles on configuring FVWM.  I could be wrong on the source of those articles and will try to find them.

---

