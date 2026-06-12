---
title: "Compiz just went crazy!!"
date: 2006-09-16
forum: Desktop Environments
---

### Post by PathSpace on 2006-09-16
My system went back into the login screen (for no apparent reason), so I logged back in.  Instead of my usual 4 viewports, it now says I have 16!  ](*,)  My desktop pager reflects this, though my Compiz cube only has 4 sides.

I REALLY want to set it back to 4 viewports (so I can use my desktop pager properly), but cannot figure out how.  I've looked almost everywhere in CSM.

If anyone can tell me how to set it back to 4, I would GREATLY appreciate it.  :D

---

### Post by ayoli on 2006-09-16
my pager seems to have a similar pb (it shows one workspaces when i have 4 viewports), i've looked in gconf, in csm, no love.
edit:  eally weird, if i check "show workspace name" it shows only "workspace 1" which confirms that pager scann see only one of four, but i see all the open windows on it (even if they are on different viewport) and when i clic a win in it, it throws me on the viewport where the win is. this means that the pager works, but with a weird view. that's since last compiz update (.54), maybe need an libwnck update

---

### Post by tribaal on 2006-09-16
Same here... :(

---

### Post by ayoli on 2006-09-16
ok got the fix from compiz forums, here it is:
>  from DBO: fix for this is easy:

-- open csm
-- go to general options -> numeric values
-- Set vertical size to 4, then back to 1
yay :)

---

### Post by PathSpace on 2006-09-16
Thanks ayoli; that worked great!  :D

---

### Post by ayoli on 2006-09-16
> **PathSpace said:**
> OK, so I'm not the only one having this kind of problem after the last update I guesss.  But how can we fix it?

I've looked nearly everywhere, but cannot find anywhere to change the number of viewports.  :(

hem, read post above ;) sometimes, look at compiz.net forums, bugs section or Q/A section

---

### Post by ayoli on 2006-09-16
it seems to be a temp fix, some needs to re-do this at each login, a bug was filled and a patch might be integrated in next release. compiz.net thread about this is here:
[http://www.compiz.net/topic-4473-gnome-workplace-switcher](http://www.compiz.net/topic-4473-gnome-workplace-switcher)

---

### Post by neymac on 2006-09-16
> **PathSpace said:**
> My system went back into the login screen (for no apparent reason), so I logged back in.  Instead of my usual 4 viewports, it now says I have 16!  ](*,)  My desktop pager reflects this, though my Compiz cube only has 4 sides.

I REALLY want to set it back to 4 viewports (so I can use my desktop pager properly), but cannot figure out how.  I've looked almost everywhere in CSM.

If anyone can tell me how to set it back to 4, I would GREATLY appreciate it.  :D

The same problem here, 16 viewports after update to compiz 0.0.13.54

---

### Post by neymac on 2006-09-16
> **ayoli said:**
> ok got the fix from compiz forums, here it is:

yay :)

It worked, thanks.

---

### Post by ayoli on 2006-09-17
completely fixed by upgrading to compiz .56 and compiz-plugins .36 last night.

---

