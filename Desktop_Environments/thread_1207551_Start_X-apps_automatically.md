---
title: "Start X-apps automatically"
date: 2009-07-08
forum: Desktop Environments
---

### Post by Jonnox on 2009-07-08
Does anyone know how to start an X-Window app using a script at startup. Here is my situation:

I am using blackbox as my wm, and I want to start fbpanel and nautilus after blackbox loads. I am using this on a live cd format. I have tried creating a python script that waits until blackbox is loaded then tries to open them:

```
su <user> -c 'fbpanel &'
```

but it just returns "Cannot open display" (even though I am logged in and using blackbox).

Any ideas? Thanks in advance!

---

### Post by anystupidname on 2009-07-08
> **Jonnox said:**
> Does anyone know how to start an X-Window app using a script at startup. Here is my situation:

I am using blackbox as my wm, and I want to start fbpanel and nautilus after blackbox loads. I am using this on a live cd format. I have tried creating a python script that waits until blackbox is loaded then tries to open them:

```
su <user> -c 'fbpanel &'
```

but it just returns "Cannot open display" (even though I am logged in and using blackbox).

Any ideas? Thanks in advance!

[http://blackboxwm.sourceforge.net/BlackboxFAQ/StartupAndShutdown#HowToRunAnApplicationegXMMSEverytimeBlackboxIsStarted](http://blackboxwm.sourceforge.net/BlackboxFAQ/StartupAndShutdown#HowToRunAnApplicationegXMMSEverytimeBlackboxIsStarted)

---

### Post by Jonnox on 2009-07-08
Thanks for the prompt reply, in the live cd as well as my ubuntu version (8.04 Hardy Heron), there appears to be no

~/.Xclients
~/.xinitrc
~/.Xsession

---

