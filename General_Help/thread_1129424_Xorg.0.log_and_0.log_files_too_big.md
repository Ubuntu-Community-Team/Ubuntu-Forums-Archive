---
title: "Xorg.0.log and :0.log files too big"
date: 2009-04-18
forum: General Help
---

### Post by luoihoc on 2009-04-18
I have problem with these two files. They are always too big after i use my computer for a while. I think the problem is that, i have dualhead now on my laptop. And the gdm and xorg server try to write log for my both monitors. Does anyone have a good solution for my problem? 
Thanks

---

### Post by justin_guerin on 2009-04-18
I can think of at least two options:

1) you can alter the xorg startup command and set the logging level to something less verbose.  I don't know offhand which script starts xorg, but you should be able to find it by poking around.

2) you can set up a logrotate config file for your Xorg logs.  Logrotate is a standard package, so it's likely already installed.  Drop your new config file in /etc/logrotate.d/ and you're good to go.

---

