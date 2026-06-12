---
title: "[xubuntu] Since upgrading to 20.04 snapd is slowing down system"
date: 2020-09-03
forum: Desktop Environments
---

### Post by shersk on 2020-09-03
I recently upgraded Xubuntu to 20.04, and since then, discovered that the harddrive is working constantly. It turns out, the reason is that I now have snapd versions of many applications, and this is causing the increased load on the system.

The reason I chose Xubuntu was that it is a lightweight distribution, which lets the system work comfortably despite low ram. 

Is it possible to retain this quality under version 20.04, using snapd, and if so, how? Could Xubuntu 20.04 be used in a "non-snapd" mode somehow? Do I need to set some configuration parameters for low-mem? 

Or will I need to start looking for a different distribution to get that lightweight quality that Xubuntu used to offer before version 20.04?

---

### Post by scorp123 on 2020-09-03
> **shersk said:**
>  Could Xubuntu 20.04 be used in a "non-snapd" mode somehow?

Yes. I use Ubuntu 20.04 and completely removed "snapd". And I don't see or experience any problems so far.
Commands to completely get rid of "snapd":

```

sudo snap remove gnome-3-34-1804 gtk-common-themes snap-store
sudo snap remove core18
sudo apt purge snapd

```

After these steps "snapd" will be gone from your system.

---

### Post by shersk on 2020-09-04
Thank you. I removed snapd from my system. Now the question is: How do I install the non-snapd version of the chromium browser? If I just type sudo apt install chromium-browser, it reinstalls snapd and I'm back where I started.

More broadly: How do select "non-snapd" versions of other programs and generally avoid inadvertently reinstalling snapd?

---

### Post by guiverc on 2020-09-04
Ubuntu does not package `chromium` (browser) except via snap for *newer* releases starting May-2018 (*so 18.04 missed out*).

Chromium is packaged in *deb* format in beta, and via PPA, but not official repositories for Ubuntu. (*a search online I'd expect to show that; however being 3rd party sources; the validation of them being safe & appropriate for you, is on you; thus why I've not included an*y).

I usually install apps via command (CLI), so I'll know what I'm installing over a GUI store (*where it's listed yes, but you have to look for it, in the terminal you okay the command and can't miss it*).  I also like `aptitude` which doesn't know about *snaps*.  I don't mind snaps though; but I avoid if I can as I like my box faster (*it's a 2009 desktop; c2q-q9400 so not a lot of spare resources*).

Avoiding snaps is pretty easy though, with the exception of chromium, which was covered extensively during the change on discourse.ubuntu.com ([https://discourse.ubuntu.com/t/intent-to-provide-chromium-as-a-snap-only/5987](https://discourse.ubuntu.com/t/intent-to-provide-chromium-as-a-snap-only/5987) and more)

XFCE as it moved to GTK3 became heavier, as the GTK3 libs are heavier than GTK2 (I noticed the same thing when MATE made it's move; it's very noticeable on really low powered devices, especially prehistoric pentium M laptops, somewhat on pentium 4; this is very subjective and my 2c only from experience).  It's not noticeable on anything in the last decade though; at least in my opinion.

---

### Post by shersk on 2020-09-16
Thank you. But I am back to square one, I'm afraid. I installed Chromium from a different PPA, and it worked nicely without snapd, but then came another software update of chromium, I clicked update, and it tried reinstalling snapd. Not wanting to get the snapd version I interrupted software updater, and have to do some repairs. How do I tell apt to stick to the alternate repository for chromium-browser?

*Solution:*

I found out through searching that in order to hold apt back from reverting to the official chromium version whenever there's an update, one needs to edit the file [COLOR=#333333][FONT=monospace]/etc/apt/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]preferences.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]d/chromium and add a so-called PIN priority between 501 and 990:

[/FONT][/COLOR]```
[COLOR=#333333][FONT=monospace]Package: *
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]Pin: release o=<name of release package>
Pin-Priority: 700[/FONT][/COLOR]
```[COLOR=#333333][FONT=monospace][COLOR=#222222][FONT=Ubuntubeta]

This worked in my case. I was able to install chromium again from the alternate repository, not from canonical, and thus avoided having snap reinstalled.

ADVICE TO DEVELOPERS: Please include a non-snap version of chroimium in xubuntu! It is vital to this distro's survival. I would switch to some other distro if I had not been able to solve this problem, and I'm sure you'll hear from others too as people move to the 20.04 version. [/FONT][/COLOR][/FONT][/COLOR]

---

