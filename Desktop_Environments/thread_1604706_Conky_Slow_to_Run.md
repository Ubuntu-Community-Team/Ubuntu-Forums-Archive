---
title: "Conky Slow to Run"
date: 2010-10-24
forum: Desktop Environments
---

### Post by ssmith335 on 2010-10-24
Hi Folks,

I've been running Ubuntu 10.10 since its became available and have recently dialed in my conky config. All has been working just fine. I usually leave my system running 24x7 and will reboot it or shut it down from time to time. 

I have conky running via a command line (manual) and as soon as I enter 'conky' it will run immediately. However, this morning I rebooted my system, ran conky in a terminal window as I usually do...nothing the usual script shows up in the terminal window, but conky didn't appear on the screen. I've not changed backgrounds, changed my .conkyrc file, nothing. I removed conky and reinstalled it and pulled a new .conkyrc from a backup. I could read the original just fine, but thought perhaps the . file had something wrong. Still the same results...conky didn't appear on the desktop. Here is what is really weird. After about 3 or 5 minutes, conky appeared on screen and is running fine except its no longer pulling my external IP number via: 

External IP$alignr${execi 3600 wget --connect-timeout 4 -q -O - "$@" [http://whatismyip.org](http://whatismyip.org) | tail}
Gateway     $alignr${gw_ip}

Any suggestions on why its taking conky so long to appear on the screen?

Thanks,

---

### Post by Pablo Pablovski on 2010-10-24
It might be that whatismyip isn't working - I get a timeout error when I try it (from the UK). If conky doesn't get a response, it'll wait will something times out before painting anything on the desktop.

Try taking that line out of the script temporarily and try again. If it works ok, then fails when you put the line back into the script, it's a fair bet the problem lies with whatismyip.com. Might be a temporary glitch.

---

### Post by ssmith335 on 2010-10-24
Pablo,

Thanks for the tip. I'll give that a try.

~Steve

---

### Post by Old_Grey_Wolf on 2010-10-25
Whatismyip.org hasn't been working lately. I comment out the line. I am looking for an alternative site.

Edit:  just found out that whatismyip.org is working again.

---

### Post by hrickh on 2010-10-25
If you find that whatsmyip.org is too slow or not available, you can also use:

${execi 3600 curl ifconfig.me}

Of course, you need curl installed for this to work.

R.
==

---

