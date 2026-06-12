---
title: "openbox, hsetroot, gnome-settings-deamon mess up?"
date: 2009-07-27
forum: Desktop Environments
---

### Post by phonky on 2009-07-27
Hi

I am having problems in configuring my desktop.

I initially installed xubuntu on the machine.
Then I played around with different DE/WM,
mainly openbox, LXDE and windowmaker.

I finally settled for openbox.

When I log in, I can see the background image shortly coming up. Then it seems as it gets overwritten by some solid background color, which suspiciously looks like ubuntu's "human" theme colour.

I switched the GTK theme with switch2 and set it to MurrinaBleu.
Here is my openbox autostart.sh:
```

# Run the system-wide support stuff
. $GLOBALAUTOSTART

# Programs to launch at startup
hsetroot -full ~/pictures/bkgrounds/boelchen-sunset.jpg &
xcompmgr -c -t-5 -l-5 -r4.2 -o.55 &

sleep 2
lxpanel &
wbar -above-desk & 

```

I know that .$GLOBALAUTOSTART loads gnome-settings-daemon.

I previously had similar problems when it was loading xubuntu's
default xfce-mcs-manager before installing gnome-settings-deamon.
Then, the color was black though, and I thought it was related
to openbox's Onyx theme I was using. This has been now proven
to be incorrect.

Any idea what's going wrong?

Thank's for any suggestion.

---

### Post by kerry_s on 2009-07-27
if you like openbox you might as well try crunchbang & get rid all that other desktop stuff. it's just ubuntu+openbox
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by phonky on 2009-07-27
BTW, it seems the icon sets are "corrupted" too, as it seems they are set to the what I believe to be the "human" theme. Changing the theme with switch2 does change colors, but not icons, as far as I can see.

I interpret this as there are different applications trying to access and set the GTK themes, creating a conflict.

---

### Post by phonky on 2009-07-27
Thanks kerry_s,

that looks great.
However, I couldn't find any howto on the wiki about
"HOWTO migrate from [?]ubuntu to CrunchBangLinux".

If there is one, I might consider it.

Otherwise, I honestly don't want to go through the 
download_ISO - burn_CD - reboot - reinstall - reconfigure everything
cycle.

I presume by changing sources.list I could access its repositories maybe,
but I am afraid to mess up the system by doing that.

Thanks anyway.

---

### Post by kerry_s on 2009-07-27
> **phonky said:**
> Thanks kerry_s,

that looks great.
However, I couldn't find any howto on the wiki about
"HOWTO migrate from [?]ubuntu to CrunchBangLinux".

If there is one, I might consider it.

Otherwise, I honestly don't want to go through the 
download_ISO - burn_CD - reboot - reinstall - reconfigure everything
cycle.

I presume by changing sources.list I could access its repositories maybe,
but I am afraid to mess up the system by doing that.

Thanks anyway.

no it's the same repos you got now, the benefit is the work is done for you & you don't have other de/wm's compromising your install.
but if you don't want start over that's fine, i'm sure your problems can be worked through.


no doubt you have other settings from other de's/wm's getting in the way, so first go into your home holder press ctrl+h to show the hidden folders/files & start deleting the stuff you don't have anymore.
i can't tell you what you have & don't have, so you'll just have to use your common sense, if your not sure just rename it to something else.

if it were me & i was feeling lazy, i would just create a new user & delete the messed up user. just make sure you give the new user admin privileges so you don't lock yourself out.

---

### Post by phonky on 2009-07-27
It's not only lazyness. This box is also used by my parents. I set it up with xfce in the beginning and my mum learnt to use it this way. She will want to stay with a familiar interface (my mum is 68 :-) ).

Anyway, I made progress! Strangely enough, by moving the call to hsetroot to be the very last in the autostart.sh, now I have the desired bkground image. Now the opposite happens, first the familiar "human" theme color shows up, and then gets "covered" by the image.

I also installed tint2 and I think it looks great. Just need to check if I still want tint2 to go with wbar, but I believe tint2 also has launcher capability.

The icon set seems to still be fixed to something, but that's for tomorrow. Need to go to bed.

Thanks for helping, kerry_s.

---

### Post by phonky on 2009-07-28
Finally got the culprit.

It took me to go through the session initialisation sequence from gdm, where I saw that for openbox, the openbox-session script is called.

There, the $GLOBALAUTOSTART gets called by default.

Calling it again in my .config/openbox/autostart.sh, as shown
in my initial post, messed up my configuration.

So everything is fine now!

---

