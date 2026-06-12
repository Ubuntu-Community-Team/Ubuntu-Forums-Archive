---
title: "Dans Guardian"
date: 2006-09-07
forum: Desktop Environments
---

### Post by GmAz on 2006-09-07
I have DansGuardian installed and working correctly on my PC.  I was wondering if anyone that has it installed has had any issues with internet performance.  I have a 3mb Cable connection but with DansGuardian, Firehol and Tinyproxy running, it really slows down the internet, espically the reaction time from when I enter a URL and when it actually starts to load.  But, when I stop DansGuardian, Firehol and Tinyproxy, the speed goes back to normal.  If this is normal activity, I can live with it, but if not, is there a way to speed things up.

Also, with DansGuardian enabled, I cannot download any files.  I went to URLBlacklist.com to get the new lists and when I go to download the file, DansGuardian blocks the download.  Where in the dansguardian.conf file is the entry that disables downloading of files.  

In advance...MANY THANKS!

---

### Post by etank on 2006-09-07
I used the conversion tool from the Christian Ubuntu project and it installs Tiny Proxy and Dans Guardian. I too had the same slow internet issues. When I posted about it on the forum they said that it was an issue only with some setups. I eventually uninstalled it.

Check the bannedextensionlist for the download problem. Not sure if that is where it is or not for sure though.

---

### Post by inetguy on 2006-10-02
I installed using the script from [http://whatwouldjesusdownload.com](http://whatwouldjesusdownload.com) and I am experiencing major speed issues.  Squid was caching and working great, then I installed the DansGuardian, TinProxy, bundle from the above mentioned site and now, the speed is soooo slow.  Is there a fix for this?  I don't want to live with the slow speeds.

As an alternative I tried to avoid using DG on my computer and go right to squid on my linux box and nothing loaded.  Is there a way to just use squid on one or two computers and then DG on the rest for my kids?

Thanks for any help.

---

### Post by tonhou on 2006-10-02
> Also, with DansGuardian enabled, I cannot download any files. I went to URLBlacklist.com to get the new lists and when I go to download the file, DansGuardian blocks the download. Where in the dansguardian.conf file is the entry that disables downloading of files.

/etc/dansguardian/bannedextensionlist

or if you are using the Ubuntu CE Parental Controls Gui it is the "Blocked File Extensions" button


> Squid was caching and working great, then I installed the DansGuardian, TinProxy, bundle from the above mentioned site and now, the speed is soooo slow.

I trust that you removed squid!!

--Tony

---

### Post by inetguy on 2006-10-02
I'm gonna put myself on a limb and ask, why would I have uninstalled squid.  Don't I want that on the system too?  Will removing squid speed up DG?

Thanks for any help.

~Dennis

---

### Post by tonhou on 2006-10-02
> Don't I want that on the system too?

No, you don't want squid. Tinyproxy is doing the job that squid does. It is a much lighter proxy server than squid with low system resource requirements. Dansguardian, tinyproxy and firehol are working together. The script that you used is based on this howto:

[http://www.ubuntuforums.org/showthread.php?t=207008](http://www.ubuntuforums.org/showthread.php?t=207008)

I believe that some of the speed problems people are having is because of not understanding the way these work together and another proxy server or firewall will mess things up.

Hope this helps.

--Tony

---

### Post by inetguy on 2006-10-02
Tony,

Thanks for the help-it seems to have worked, somewhat.  I now have lost my ssh and ftp access it appears.

Any ideas on where to get some help figuring that out?

Thanks

---

