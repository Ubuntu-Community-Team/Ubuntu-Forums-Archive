---
title: "google earth"
date: 2009-06-10
forum: General Help
---

### Post by blur xc on 2009-06-10
so, I downloaded googleearthlinux.bin.  Now what do I do with it?

thanks,
BM

---

### Post by keplerspeed on 2009-06-10
I find it easier to add the medibuntu repo, then add google-earth via synaptic. See here for medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Tipped OuT on 2009-06-10
Download google-earth**.deb**, not .bin.

---

### Post by ftabor on 2009-06-10
> **Barna Madau said:**
> so, I downloaded googleearthlinux.bin.  Now what do I do with it?

thanks,
BM

Save googleearthlinux.bin to your desktop.

In a terminal: 

```
cd Desktop
sh GoogleEarthLinux.bin
```

---

### Post by blur xc on 2009-06-10
What's the sh command do?

I did the whole medibuntu thing, which I was meaning to do anywa- and I downloaded the google earth package- but still @ square 1- don't know what to do w/ that either...

when I get home (at stinking work) I'll try that command in the terminal and see what happens.

Thanks,
BM

---

### Post by Soul-Sing on 2009-06-10
If you did the whole "medibuntu thing", open synaptic package manager: reload button: search for googleearth: mark it for install: install...
or
```
sudo apt-get install googleearth
```

---

### Post by blur xc on 2009-06-10
> **leoquant said:**
> If you did the whole "medibuntu thing", open synaptic package manager: reload button: search for googleearth: mark it for install: install...
or
```
sudo apt-get install googleearth
```

I searched synaptic for google earth and the only thing that came up was google earth package.  It said that google earth was not permitted to be distributed by a third party, and this utility helped you make a package for installation- (as I recall, which isn't that good)...

I'll check again when I get home.

Forgive my slowness- I've been on linux for under a week now.  I'm on learning overload.  Between learning to build a pc (my first build), bios junk, troubleshooting a post/boot problem, and learning a new os...

BM

---

### Post by oldos2er on 2009-06-10
You don't need "sh" for a bin file. Run these commands one at a time:
```
cd Desktop
chmod a+x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
```
 This will install Google Earth in /opt, where it will be available for all users. Be sure to exit the installer program completely prior to running Google Earth.

---

### Post by joey-elijah on 2009-06-10
once installed, If you're using Jaunty run it with

>  *googleearth -style GTK+*
from a terminal to make it use your GTK theme and not look like a windows 2000 relic app.

---

### Post by Soul-Sing on 2009-06-10
> **joey-elijah said:**
> once installed, If you're using Jaunty run it with


from a terminal to make it use your GTK theme and not look like a windows 2000 relic app.

ok I was using: ```
googleearth -style GTK+ %f
```

---

### Post by blur xc on 2009-06-10
> **leoquant said:**
> ok I was using: ```
googleearth -style GTK+ %f
```


Sweet- it installs and runs, but not w/o errors.  First off, it started on its own right after installation.  So, I can assume maybe that it exited the installer before running???  Either way, and it looks like it's using my theme all on its own.

Now, as far as the errors go- 
#1- "Could not create direcory /root/.googleearth
#2- "Could not create directory /roo/.googleearth/cache
#3- "Google Earth could not write to the current cache or myplaces file location. The values will be set as follows:  My Places Path: "/home/barna/.googleearth";  Cache Path: "/home/barna/.googleearth/Cache""

and no matter how I search, I can't find a googleearth.deb file anywhere in synaptic.

thanks,
BM

---

### Post by freeediver on 2009-06-11
I had to wipe my system and I am now trying to clean things up some.
I would sure like google earth agin but I am having issues??
Ref. Post #4.
I followed those inst. and the install seemed to work well but when I try to open google earth my sys crashes and automatically
goes to restart. 
Whats up, any ideas ?
Thanks

---

### Post by blur xc on 2009-06-11
ok, had a moment of inspiraton; if I enter ```
sudo googleearth -style GTK+ %f
``` it works fine, but then if I try to run it again w/o the sudo, I get the errors again.

Thanks, 
BM

---

### Post by Soul-Sing on 2009-06-11
You should [COLOR="Red"]not[/COLOR] run it with -sudo
installing and running googleearth are different things.

---

### Post by freeediver on 2009-06-11
Any ideas on what I should try? I can D/L GE ( 4.2 , 4.3 & 5 ) but with all versions I have tried when I actually attempt to open GE my system crashes and re-starts.
Before I re-installed my complete sys. GE was working.
I had a HD error and a re-install was the only way to resolve the issue.
How can I freeze my information to see the error (?) just before my sys crashes ? I get an error screen for about one second.

Thanks

---

### Post by blur xc on 2009-06-11
> **leoquant said:**
> You should [COLOR=Red]not[/COLOR] run it with -sudo
installing and running googleearth are different things.


That's wonderful- but why is it trying to make folders under the root user on startup?  At least my computer didn't blow up...

BM

---

