---
title: "indicator-sound-service won't run in user account"
date: 2011-06-22
forum: Desktop Environments
---

### Post by fmouse on 2011-06-22
I have a user account on my laptop which does not display the sound-service icon in my notification area applet (Ubuntu 11.04).  If I try to start /usr/lib/indicator-sound/indicator-sound-service manually, I get the following error

```
libindicator-WARNING **: No watchers, service timing out.
** (process:5612): DEBUG: Service shutdown !
```

In the many months I've had this account on this box, and as a result of the many minor mods I've made to the account, I've somehow bollixed something in the account setup which interferes with the startup of the service.

I created a new account on the system, and the sound service icon displays properly, so I know it's not a system problem.  Both the new, bare account and my personal account are in the audio group.

As a work-around, I have an icon for gnome-volume-control on my top panel, which works pretty well, but I'd like to fix the problem with indicator-sound-service if someone could point me to a solution.

---

### Post by ink_rus on 2011-07-02
Same problem in "Linux mint 11" :confused:
Reinstall don't change situation.

---

### Post by fmouse on 2011-07-02
I solved the problem by removing and reinstalling the indicator applet.  The sound indicator came back.

---

### Post by Bazon on 2011-11-03
in xubuntu, I noticed there are two different notification indicator applets: one called "Benachrichtigungsfeld" in german (I think) and one called "Nachrichtenfeld" (I think).

In one of these, the sound indcator shows up, in the other it doesn't....

---

### Post by Bazon on 2011-11-03
PS:
After some fuddling I found out how to switch language in LightDM and now I now the english terms:

Indicator Plugin: Shows indicator-sound
Notification-area: Doesn't show indicator sound.

The Package for Indicator Plugin is xfce4-indicator-plugin if someone needs it.

---

