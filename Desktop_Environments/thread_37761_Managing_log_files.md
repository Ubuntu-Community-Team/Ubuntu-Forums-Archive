---
title: "Managing log files"
date: 2005-05-28
forum: Desktop Environments
---

### Post by kabanta on 2005-05-28
My root directory is on the verge of 100% full (even at 3gb). Over 200mb of this is in /var/log. Is there a straighforward and safe way to flush log files?

---

### Post by stevenyu on 2005-05-29
What the hack did you have in the /root ???

---

### Post by Markrian on 2005-05-29
[quote="stevenyu"]What the hack did you have in the /root ???[/quote]I think he's referring to the / directory, not /root.

As for /var/log, unless you generally read what's in there, it's not that useful. You could set up a cron job to clear the directory every week or something. You can safely (as far as I know) delete those logs.

Also, doing an *apt-get clean* every once in a while would help as well - no need to keep cached .deb files unless you reuse them all the time (you probably don't).

---

### Post by kabanta on 2005-05-29
[QUOTE=Markrian]I think he's referring to the / directory, not /root.[/QUOTE] Yes, sorry for the confusion.
> 
As for /var/log ...you can safely (as far as I know) delete those logs. Ok. I'll give it a try.
> 
Also, doing an *apt-get clean* every once in a while would help as well Yes, I do that already. thanks.

---

