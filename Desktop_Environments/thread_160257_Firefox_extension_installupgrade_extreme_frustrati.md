---
title: "Firefox extension install/upgrade extreme frustration"
date: 2006-04-14
forum: Desktop Environments
---

### Post by radioraheem on 2006-04-14
So today I sudo'd firefox so I could obtain the 1.5.0.2 update, and while I was at it I figured I check my extensions for updates too.

Here's my problem:  If I try installing a new extension without sudo'ing firefox it installs and tells me it will be available after firefox is restarted, but restarting it changes nothing.  The extension is still listed in the extensions manager but it still says to restart firefox.

If I install an extension as sudo, then restart firefox it is working while still in sudo, but as soon as I try and launch it normally (without sudo) the newly installed/upgraded extensions disappear.

I've tried searching for previously posted suggestions but the search criteria I have to work with is bringing up a ton of completely false positive results.

Any suggestions?  I'm still glad I ditched windows entirely but I must admit I'm getting pretty fed up with little problems like this.  Please help a recent convert STAY a convert!

---

### Post by aysiu on 2006-04-14
Maybe *sudo* changed permissions on your Firefox profile directory? Try this ```
sudo chown -R radioraheem:radioraheem ~/.mozilla
sudo chmod -R 755 ~/.mozilla
```

---

### Post by radioraheem on 2006-04-14
You rock!  :-D That fixed it.  Can't believe I overlooked something as simple as permissions, but I've never had sudo mess them up before.

A side question:  should I continue to install new extensions as sudo?

Thanks again for the quick and excellent help!

---

### Post by aysiu on 2006-04-14
[QUOTE=radioraheem]You rock!  :-D That fixed it.  Can't believe I overlooked something as simple as permissions, but I've never had sudo mess them up before.

A side question:  should I continue to install new extensions as sudo?

Thanks again for the quick and excellent help![/QUOTE] I think now that it's fixed, you should just install extensions the regular way, as extensions get "installed" to your /home/radioraheem/.mozilla directory, not to the system-wide Firefox directories.

---

