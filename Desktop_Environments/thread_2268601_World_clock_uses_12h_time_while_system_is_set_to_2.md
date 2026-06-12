---
title: "World clock uses 12h time while system is set to 24h"
date: 2015-03-10
forum: Desktop Environments
---

### Post by Czarcasmo on 2015-03-10
Hi folks,

Long time lurker, now I actually have a question I have not found a direct answer to yet. 

If I go to 'Time/Date Settings' and then 'Clock', I set the time to use 24-hour time. If I slide over to 'Time in other locations' and then proceed to choose the cities I want to add, all of those times are displayed in 12-hour time. Is there a setting to override this? I have dug through dconf and have attempted setting a custom time string (which did not work) and aside from that, I did not see anything else worth changing to try and "fix" this.

Any help is appreciated.

Thanks!

EDIT: Dear Lord, I just noticed that the forum indicates me as using 10.10. I cannot change that right now because I do not have enough magic beans, but I am using 14.04 LTS.

---

### Post by ryan-c-dunlop on 2015-04-03
This bug seems to have been around for a while now... not sure why there isn't more traction to this!  I face the same issue.  

Bug report:  [https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1319195](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1319195)

A reported work around (I haven't tried...yet):  [https://askubuntu.com/questions/493725/24h-time-format-not-applied-on-other-locations](https://askubuntu.com/questions/493725/24h-time-format-not-applied-on-other-locations)

EDIT: Also running 14.04 LTS

---

