---
title: "Firefox, Thunderbird, Global Menu Integration and Crashes"
date: 2012-08-21
forum: Desktop Environments
---

### Post by linux4me on 2012-08-21
I'm running an up-to-date version of Ubuntu 12.04 which has been rock solid until two days ago when Firefox began crashing on a frequent, apparently random basis. By "crash," I mean that Firefox would close abruptly and the Mozilla dialog box sending a crash report to Mozilla would pop up. (I'll bet they love me, they must have 20 bug reports from me on this.)

The only non-standard (i.e., that don't come with Ubuntu) plug-ins I am running are NoScript and Firebug.

When I ran Firefox from terminal, I got the following error:
> (firefox:5261): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed

I disabled one plug-in at a time and restarted Firefox in normal mode. Removing NoScript and Firebug didn't prevent the crashes, but so far, disabling Global Menu Integration seems to have prevented the crashing.

Once I thought I had Firefox behaving, Thunderbird crashed. I disabled the Global Menu Integration add-on in it, too, and so far, so good.

I do see a mention of an issue with Firefox and Unity's Global Menu Integration in the [Firefox megathread]("http://ubuntuforums.org/showthread.php?t=1712247") which recommends either disabling them or uninstalling firefox-globalmenu. There don't seem to be a lot of details there, but apparently it's a known issue. It's just very weird it didn't strike me until now.

I can't think of anything I might have done that would have precipitated this kind of thing with Mozilla products. Does anyone have any more information about it?

---

### Post by gururuby on 2012-08-28
Hi! Check your version of Firefox. If it is 14 then to upgrade to version 15, it needs to check in the update manager precise-proposed updates checkbox

---

### Post by linux4me on 2012-08-28
> **gururuby said:**
> Hi! Check your version of Firefox. If it is 14 then to upgrade to version 15, it needs to check in the update manager precise-proposed updates checkbox

I've got version 14.0.1 at the moment. Are you suggesting the upgrade to version 15 because you too had this specific problem and upgrading fixed it, or just as a general suggestion when encountering this kind of issue?

---

### Post by nex_gen on 2012-08-28
> **gururuby said:**
> Hi! Check your version of Firefox. If it is 14 then to upgrade to version 15, it needs to check in the update manager precise-proposed updates checkbox

Had the same problem too. If you don't want to enable precise-proposed you can add 'Ubuntu Mozilla Security Team' PPA from [here]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/").

OR

```
sudo apt-add-repository ppa:ubuntu-mozilla-security/ppa
```

---

### Post by linux4me on 2012-08-28
I'm more comfortable with that. I use this machine for work, so I can't afford to have Firefox crashing and I'm hesitant to use the proposed repositories because I don't want to introduce anymore instability. I've just been running with Global Menu Integration disabled.

---

### Post by gururuby on 2012-08-29
> **linux4me said:**
> I've got version 14.0.1 at the moment. Are you suggesting the upgrade to version 15 because you too had this specific problem and upgrading fixed it, or just as a general suggestion when encountering this kind of issue?
Yes, I have had this problem, solved it in this way, updating Firefox to 15

---

### Post by linux4me on 2012-08-29
Okay, thank you for the info.

---

