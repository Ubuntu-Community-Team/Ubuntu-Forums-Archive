---
title: "Pointing everything in /etc/apt/sources.list to a different server"
date: 2006-05-11
forum: Desktop Environments
---

### Post by Littleweseth on 2006-05-11
G'day;

I'm currently in the process of completely reinstalling a Ubuntu box. (did some rather stupid things involving mkswap and the whole of my harddrive.. *wince*) Since I just rather conveniently nuked my cache of installed packages, I have to redownload them all. The problem is, I'm paying $22.50/gig (australian dollars, of course) to download from the .au ubuntu mirrors.

However, I can download for free (well $1/gig, but that's a triviality - even uni students aren't that poor) from [http://mirrors.uwa.edu.au/](http://mirrors.uwa.edu.au/) - which has a full repository mirror, though I'm not sure exactly what version of Ubuntu it's for. Can anyone point me towards rewriting sources.list to use this server instead of the defaults?

Cheers;
-lws

---

### Post by morequarky on 2006-05-11
Hey, I am fairly new at this, but lets see if this works.  I am not sure of every detail.


If you have Breezy running, go to System - Admin - Synoptic Package Manager
Then choose Settings - Repositories.

Uncheck all the repositories you see.

Then click Add

Click "custom"

Enter the new server correctly.

Then it might do everything for you, but if it doesn't, you need to run an update command and then upgrade which will upgrade everything for you from the new server.

---

### Post by Littleweseth on 2006-05-15
Funnily enough, the official australian mirror is actually mirrors.uwa.edu.au. Whodatthunkit? However, while UWA (University of Western Australia) is on AARNet, I'm getting charged the full $22.50 a gig still - bummer. However, apparently anything on Internet2 is free, for great justice.

Does anyone know if any of the universites in this list run Ubuntu mirrors?

[http://members.internet2.edu/university/universities.cfm](http://members.internet2.edu/university/universities.cfm)

Cheers
-lws

---

