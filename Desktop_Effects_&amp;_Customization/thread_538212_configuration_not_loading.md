---
title: "configuration not loading"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by chanman on 2007-08-29
so I have compiz as default in gconf. But it does not load the correct configuration. I have to do a "compiz --replace" to get the correct configuration.

I had compiz load through my startup sessions before I changed it in gconf. Is that the problem?

If I try to go to CCSM without doing a "compiz --replace" it crashes and defaults to metacity.

---

### Post by michael37 on 2007-08-30
I tried several guides addressing this problem, but it's hard to manage with Fiesty.  They may make it easier with the future versions, but for now I found a trivial solution.

Go to System/Preference/Sessions.  Create a "New" launcher for "compiz --replace".  Next time you log in, Gnome will execute this command as a part of a sessions startup and you'll have a working WM.

---

