---
title: "Firefox 1.0.4 Ubuntu deb now available"
date: 2005-05-12
forum: Desktop Environments
---

### Post by shakin on 2005-05-12
I haven't seen anybody else post this yet so I built a deb from the Firefox source. You may all use it for web browsing, feeding underpriviledged children or picking your nose, as you see fit.

*warning*

This deb may work perfectly or cause your system to spontaneously combust, or anything in between. I've tested it for a few hours and it seems ok, but consider it not suitable for production systems.

Just in case it is bad, I changed the install directory to /opt/firefox so it *shouldn't* affect your existing Firefox installation at all. dpkg will not remove the old install as this package isn't considered an upgrade. After installing it just update your shortcuts to point to /opt/firefox/bin/firefox and it should work.

* Note: this link MUST come down tonight. Somebody please mirror this file and I will change the download location to the mirror.

**
link removed -- sorry
I have an updated version that fixes several problems with the original package I made (like Javascript not working properly and settings being reset).

If you have a web or ftp site I can mirror this file on please let me know and I'll send you the deb.
**

Please reply with any bugs relating to my package and I'll try to address them.

** UPDATE **

There is a problem where Firefox shows you the profile selection menu when you try to start a second instance of the browser. I have attached a shell script that fixes the problem that you should run instead of the firefox binary. You can replace the /usr/bin/firefox script that already exists on your system or, like me, put it in /opt/firefox/ and switch your shortcuts to run /opt/firefox/firefox. It seems to work perfectly.

---

### Post by dolny on 2005-05-12
How do I launch it? I know this is a stupid question but 'firefox' or 'mozilla-firefox' doesn't work for me.. 

Ok I read the edit now :]

---

### Post by shakin on 2005-05-12
[QUOTE=dolny]How do I launch it? I know this is a stupid question but 'firefox' or 'mozilla-firefox' doesn't work for me.. 

Ok I read the edit now :][/QUOTE]

FYI, the actual binary is at /opt/firefox/bin/firefox

---

