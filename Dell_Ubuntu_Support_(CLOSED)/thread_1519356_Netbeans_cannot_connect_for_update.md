---
title: "Netbeans cannot connect for update"
date: 2010-06-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ufis on 2010-06-28
I am running ubuntu 10.04 on my Dell Inspiron laptop and am trying to install netbeans 6.8.

I have downloaded the install from netbeans.org installed it and tried to update.

But netbeans cannot connect to the web to check for updates or install new plugins. Keeps on telling me to check my proxy settings. I have tried all the settings, no proxy, use system settings, but no luck.

I even installed netbeans via apt-get and tried to update, with the same result.

Same results for 6.9.

All my other applications can connect fine.

Any ideas?

PS. I have now reverted back to 8.04 and have installed and updated netbeans fine.

I also tried ubuntu 9.10 but netbeans did not update there either.

---

### Post by ufis on 2010-07-12
Disabling ipv6 ([http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)) fixed this problem.

---

### Post by schmendrick on 2011-03-03
did not work for me. 
my solution is to download the updates manually and then installing them via -> Tools->Plugins->Download->Install

tedious, but it worked

---

