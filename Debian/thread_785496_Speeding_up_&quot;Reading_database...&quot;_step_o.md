---
title: "Speeding up &quot;Reading database...&quot; step of dpkg"
date: 2008-05-07
forum: Debian
---

### Post by ivucica on 2008-05-07
Hi all,

I'm a Debian user, not Ubuntu, but the system is the same so this is as good place to ask as any other.

"Reading database..." step in DPKG now takes about one and a half minute to pass. The /var/lib/dpkg directory produces a whooping 76mb TAR file (no compression) which makes me think that it might be the reason (especially considering that /var/lib/dpkg/info contains some files from packages uninstalled long time ago)?

Did anyone else have this problem where "Reading database..." takes longer and longer? How did you fix it? 

Thanks in advance!

---

### Post by ivucica on 2008-05-14
Bumping. Please help.

---

### Post by Milk &amp; Toast &amp; Honey on 2008-06-15
> **ivucica said:**
> Bumping. Please help.

+1
I also anxious to find out what's going on here. I had googling around, but can't find how to speed up this thing.

As far as I can remember, feisty's "Reading database..." is speedier than my current setup (Hardy, upgraded from Gutsy).

---

### Post by Perdignus on 2008-10-29
I'd also like to know if there is a solution to this.  I recall back in the day there was a rebuilddatabase command for the RedHat RPM package manager, isn't there anything like that available for dpkg?

Thanks,
Perdignus.

---

### Post by markharding557 on 2008-10-29
> **ivucica said:**
> Hi all,

I'm a Debian user, not Ubuntu, but the system is the same so this is as good place to ask as any other.

"Reading database..." step in DPKG now takes about one and a half minute to pass. The /var/lib/dpkg directory produces a whooping 76mb TAR file (no compression) which makes me think that it might be the reason (especially considering that /var/lib/dpkg/info contains some files from packages uninstalled long time ago)?

Did anyone else have this problem where "Reading database..." takes longer and longer? How did you fix it? 

Thanks in advance!
I don't know the answer but have you posted this on debian forum they may be  able to help

---

