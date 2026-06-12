---
title: "Is anybody else having problems with the Chromium browser on 16.04?"
date: 2016-11-16
forum: Desktop Environments
---

### Post by ShowMeGrrl on 2016-11-16
As of two days ago, I am having problems with my Chromium browser.

Here are the browser specs: 
Version 53.0.2785.143 Built on Ubuntu, running on Ubuntu 16.04 (64-bit)

Certain websites display with text only, no images. And the text is often quite disordered, e.g., text lines on top of other text lines.

Some of these websites that are not displaying properly are fairly key websites for me, such as The New York Times and Amazon.com. Other sites, such as The Washington Post, ESPN.com and ConsumerReports.org, display properly. 

The other day, the Amazon site was such a mess that I was unable to complete my transaction accurately and had to switch to Firefox, which displayed the site just fine. I don't want to just switch to Firefox, because I'm fairly tied in to the Google ecosystem at this point.

I would appreciate any information, ideas or suggestions on this problem. Thank you.

---

### Post by ajgreeny on 2016-11-16
I believe this is a current bug in chromium that is being worked on still.

It is discussed in [https://ubuntuforums.org/showthread.php?t=2343147](https://ubuntuforums.org/showthread.php?t=2343147) and several others.

---

### Post by ShowMeGrrl on 2016-11-16
Thanks for the info, ajgreeny!  The problem described in the link you gave has to do with security certificates not being trusted and Chromium warning not to go to those sites.

My Chromium has THAT problem as well as the one I described above of displaying text only. Are the two problems linked? Or are they two separate, unrelated problems?

---

### Post by ajgreeny on 2016-11-16
I'm not sure as I seldom use chromium and when I used it earlier to see if I had a problem all seemed to work fine.
I am using chromium Version 53.0.2785.143 Built on Ubuntu , running on Xubuntu 16.04 (64-bit).


Is it just certain sites that give the problem or does it affect everything?

---

### Post by ShowMeGrrl on 2016-11-16
I am using the same Chromium Version you tried on Ubuntu 16.04LTS.

[COLOR=#000000]The websites that are not displaying properly are fairly key websites for me, such as The New York Times and Amazon.com. Other sites, such as The Washington Post, ESPN.com and ConsumerReports.org, do display properly.  Did you try Amazon and/or NY Times on your Chromium?

I am attaching[/COLOR][IMG]http://janehadley.net/AmazonOnChromium-a.png[/IMG][IMG]http://janehadley.net/NYTimesOnChromium-a.png[/IMG][COLOR=#000000] screenshots of the NY Times Website and the Amazon website as seen on my Chromium browser at the moment.[/COLOR]

---

### Post by CantankRus on 2016-11-17
Just installed and tested and was seeing the same on amazon.
New chrome version just appeared in updates and now renders fine.
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] apt policy chromium-browser**
chromium-browser:
  Installed: 53.0.2785.143-0ubuntu0.16.04.1.1257
  Candidate: 53.0.2785.143-0ubuntu0.16.04.1.1257
  Version table:
 *** 53.0.2785.143-0ubuntu0.16.04.1.1257 500
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
        500 http://ftp.iinet.net.au/pub/ubuntu xenial-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     49.0.2623.108-0ubuntu1.1233 500
        500 http://ftp.iinet.net.au/pub/ubuntu xenial/universe amd64 Packages
```

---

### Post by ShowMeGrrl on 2016-11-17
Thank you. Yes, my Chromium browser is now working for those two sites (NY Times and Amazon.com). I'll mark this as solved.

---

