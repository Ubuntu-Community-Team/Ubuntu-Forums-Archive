---
title: "mini 9 8.10 no wifi"
date: 2008-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ubudv on 2008-11-08
I followed the guide on ubuntumini.com to install 8.10 it installs but the wifi will not work at all. I installed the broadcom sta driver that ubuntu suggests and the guide suggests but it does not work. Do people actually have this working? What driver do you use?

---

### Post by nrdlevans on 2008-11-08
> **ubudv said:**
> I followed the guide on ubuntumini.com to install 8.10 it installs but the wifi will not work at all. I installed the broadcom sta driver that ubuntu suggests and the guide suggests but it does not work. Do people actually have this working? What driver do you use?

I had to revert to wired.  My system uses wpa2 and 8.10 does not seem to work with it.  If I turn off my routers wireless security it will connect.  Based upon all the web posts, nobody has it working yet.  The only workable security is to turn off all wireless security.  That is not an option.  Personally I suspect it is hardware driver issue.

---

### Post by nrdlevans on 2008-11-08
After seeing refernces to WICD. I decided to try it out.  I am now currently writing this on my Dell Mini using 8.10 and a WPA2 connection.  The install uninstalled the default manager and connected without any problems.

I found it on sourceforge

---

