---
title: "HELP! devilspie not doing what it's supposed to"
date: 2009-04-14
forum: Desktop Environments
---

### Post by akahige on 2009-04-14
I've got several devilspie configs that simply do not work when the windows are first created. (This worked fine on Hardy, but not since then.)


VMware.ds:
```
( if 
( and 
( is ( application_name ) "vmware" )
( contains ( window_name ) "VMware Workstation" )
) 
( begin 
( set_workspace 1 )
( geometry "+0+0" )
( println "match" )
)
)

```

and 

Pidgin.ds:
```
( if 
( and 
( is ( application_name ) "Pidgin" )
( is ( window_name ) "Buddy List" )
) 
( begin 
( set_workspace 5 )
( geometry "258x435+2958+58" )
( println "match" )
)
)

```

If I stop and restart devilspie, the windows are trapped and acted upon exactly as they should be, but dp won't grab them when they're first created. That kind of suggests it's a problem with dp and not with my config.

VMware loves to move itself to my other monitor, and that's a huge pain since devilspie just ignores its bouncing around.

My system: Jaunty beta (upgraded from Intrepid, which exhibited the same behavior), dual monitors on an NVIDIA card w. NVIDIA driver, vanilla Gnome w. no desktop effects (not enough horsepower).

---

### Post by drs305 on 2009-04-14
I can't answer your question but can present an alternative. I was a devilspie user for several years. Since Intrepid I use compiz's CompizConfig Settings Manager (ccsm) to place my windows. CCSM, Windows Management, Place Windows, Fixed Windows Placement tab.

It's much easier to set up than devilspie and works very well, including in Jaunty.

*Edit: I received a PM from the OP that compiz still takes too many resources from his setup. I was happy he informed me but disappointed in the results. So if someone can help with devilspie he is still looking for a solution.*

---

### Post by akahige on 2009-04-14
> **drs305 said:**
> I can't answer your question but can present an alternative. I was a devilspie user for several years. Since Intrepid I use compiz's CompizConfig Settings Manager (ccsm) to place my windows. CCSM, Windows Management, Place Windows, Fixed Windows Placement tab.

It's much easier to set up than devilspie and works very well, including in Jaunty.

I'd love to do that, but unless they've greatly reduced the performance footprint of Compiz, it would choke my system to the point of utter unusability. I tried it on Intrepid (kind of by accident) and everything ran so slowly I thought I was back on a VIC-20.

---

### Post by pyro2927 on 2009-09-09
Did you ever find a solution to this? I am having the same problem.

---

### Post by akahige on 2009-09-09
Nope. I never did.

I did write to the DP author, but he was kind of of the opinion that there was an issue with the rule(s) I was using.

---

