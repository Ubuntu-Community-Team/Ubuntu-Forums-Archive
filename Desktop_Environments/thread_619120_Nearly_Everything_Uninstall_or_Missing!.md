---
title: "Nearly Everything Uninstall or Missing!"
date: 2007-11-21
forum: Desktop Environments
---

### Post by kagy on 2007-11-21
Hi all,
I'm not too sure what happened but nearly all programmes (applications) disapeared from my machine last night. Postgresql etc are still running in the background. Several things might have caused it 
[LIST]
[*]Purged CUPS (capt-filter was hanging)
[*]Uninstalled MythTV (didn't support my card)
[*]an automatic upgrade via Adept (asked to restart KDM)
[/LIST]

I'm of the opinion that it was the last item, though I couldn't find anything on a Google search.
The end result was that when I restarted my machine the log-in screen was Debian (XDM?) and I only got a terminal session.

I reinstalled kdm and kde-core via apt-get. but all apps are missing

In hind sight it has the appearance that /usr or some configuration file was deleted. If it was the latter what file could it be?
If I have to reinstall everything, how can I speed things up. e.g. installing everything at once, using the cache etc.

Thanks

---

### Post by Stemp on 2007-11-21
> **kagy said:**
> If I have to reinstall everything, how can I speed things up. e.g. installing everything at once, using the cache etc.

What about reinstalling kubuntu-desktop ?

---

### Post by kagy on 2007-11-21
Thanks, I thought of re-installing kubuntu-desktop, but I had quite a few other apps installed. I was hoping that there was a list or config file somewhere that I could pipe to apt-get

Also is there anyway to use the packages in /var/cache/apt

according to the file modified date on /usr it wasn't just created today. so that means that either the update or uninstall messed up on me

---

### Post by Stemp on 2007-11-21
Maybe this command will help : 
```
dpkg --get-selections "*" > MyPackages
```

---

### Post by kagy on 2007-11-21
Thanks, that helped. 
I noticed that many items had *purge* beside them. Obviously when I was purging MtyhTV or CUPS I selected something I shouldn't or there was some dependency issue.

I can't really think of what that might have been because many of my apps aren't part of the kubuntu desktop and they went missing too!

Oh well, I've a nice clean system now

---

