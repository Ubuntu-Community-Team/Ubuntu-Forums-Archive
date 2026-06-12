---
title: "Switching to Xfce without a reinstall..."
date: 2010-04-05
forum: Desktop Environments
---

### Post by Aped on 2010-04-05
Been looking at it a bit and I am really interested in giving this environment a shot, both on my older laptop and my old server, in hopes of streamlining things a bit...

Is it as simple as synapticking a few specific packages or would I be better off just DLing and burning the install disc for xubuntu? If the latter, is a backup fairly necessary? 

Thanks in advance for the help.

---

### Post by peakshysteria on 2010-04-05
I think you just can open a terminal and:

```
sudo apt-get install xfce
```

Then restart and choose session in the login window. Then choose XFCE, Gnome or other window managers if you have more installed.

---

### Post by sheperson on 2010-04-05
Well you can install the XFCE desktop environment by installing the xubuntu-desktop like this:
```

sudo apt-get install xubuntu-desktop

```The only problem (which is not a problem if you have enough hard disk), is that you have the Gnome desktop with all its applications too.

---

### Post by kellemes on 2010-04-05
As @peakshysteria already wrote..
```
sudo apt-get install xfce
```
This will install xfce.

Installing xubuntu-desktop will turn ubuntu into xubuntu, but maybe that's what you want?

---

### Post by Noguarantee777 on 2010-04-05
If you just wanted to use Xfce to manage your windows than what peakshysteria   said will work fine, I've used Xfce and it's pretty nice. If you're looking to streamline a lot than you might consider using Fluxbox (or just for fun). Same code just change Xfce to fluxbox I believe.

---

### Post by ugm6hr on 2010-04-05
> **Noguarantee777 said:**
> If you just wanted to use Xfce to manage your windows than what peakshysteria   said will work fine, I've used Xfce and it's pretty nice. If you're looking to streamline a lot than you might consider using Fluxbox (or just for fun). Same code just change Xfce to fluxbox I believe.

I think it is actually:
```
sudo apt-get install xfce**4**
```

I'd actually suggest a little more:
```
sudo apt-get install xfce4 xfce4-mixer catfish
```

This might help: [http://ubuntuforums.org/showthread.php?p=7631053#post7631053](http://ubuntuforums.org/showthread.php?p=7631053#post7631053)

---

### Post by Aped on 2010-04-05
Thanks a ton everyone, especially ugm, pretty much just what i was looking for. I'll check  out fluxbox as well and maybe give it a whirl. Saving HDD space is a concern here, so I'd want to remove gnome as well if I liked xfce/fluxbox well enough. 

For the server, well, I almost never even access it directly; it doesn't have a KVM setup attached at the moment, so maybe what i'd want to do is just boot it into terminal mode or something. 

Anyhoo, thanks again guys.

---

