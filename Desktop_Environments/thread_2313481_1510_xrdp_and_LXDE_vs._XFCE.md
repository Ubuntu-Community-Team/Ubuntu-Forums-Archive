---
title: "15:10: xrdp and LXDE vs. XFCE"
date: 2016-02-12
forum: Desktop Environments
---

### Post by TerryMcP on 2016-02-12
I'm looking for very general guidance on the state of affairs of xrdp on Lubuntu 15:10


xrdp + LXDE = NOT WORKING for me - common problem posted many times with different solutions - the "grey screen" issue - after many attempts, still not working.
xrdp + XFCE = Works like a charm, first time, very easy setup. But this isn't the default DE for this distro, which isn't a problem but I'd like to get both working.


Another source claims:
**"...use the xfce desktop ... instead of Unity or Gnome (which are not working anymore in Ubuntu)."** I assume this is in the context of using xrdp and is quite possibly dated.


Now, many of these posts are quite dated and refer to older versions of (L)ubuntu (e.g. 12) but is seems like a very common issue that I would hope would have been sorted out by now (v 15:10).


Can anyone offer a high-level overview of the current xrdp package? 


Should I expect to have problems with LXDE? expect XFCE to work with a possible performance hit?
I don't much care about Unity or Gnome specifically, but the more general health of the xrdp ecosystem could offer some insight (i. e. why were these broken? are they still broken? does anyone care?)


Many thanks,
Terry

---

### Post by TerryMcP on 2016-02-13
From another source:

[FONT=abelregular]Since Ubuntu 12.10 (if I&#8217;m not mistaken), xRDP doesn&#8217;t seem to work with the Ubuntu desktop anymore &#8230; unless you use an alternative desktop manager. This seems related to 3D acceleration and nobody seems to care (since 2011, according to bug reports).[/FONT]

---

### Post by TerryMcP on 2016-02-13
I discovered my LXDE solution - it appears that lubuntu needs "exec lxsession..." in the .xsession file where most of the docs omitted this for Ubuntu(?)
My question is somewhat moot, unless we now add LXQt into the mix...

---

### Post by raffi.lueckl on 2016-03-23
> **TerryMcP said:**
> I discovered my LXDE solution - it appears that lubuntu needs "exec lxsession..." in the .xsession file where most of the docs omitted this for Ubuntu(?)
My question is somewhat moot, unless we now add LXQt into the mix...

Could you tell me how you made it working (a bit more specific if possible).

I'm in the same boat right now. It would be great if you could help me out. :)

---

### Post by Dorian_Mode on 2016-03-23
Not sure if this will help.
[https://www.reddit.com/r/Lubuntu/comments/2qxacn/getting_xrdp_working_on_lubuntu/](https://www.reddit.com/r/Lubuntu/comments/2qxacn/getting_xrdp_working_on_lubuntu/)

---

