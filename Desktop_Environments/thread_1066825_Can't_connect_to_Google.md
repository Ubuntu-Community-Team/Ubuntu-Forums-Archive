---
title: "Can't connect to Google"
date: 2009-02-11
forum: Desktop Environments
---

### Post by Barriehie on 2009-02-11
This happens everytime!  My internet connection is fine.  Does anyone know which log file I can look into to see what's happening?  FF 3.0.5 and Ubuntu 8.04

Thank You,
Barrie

---

### Post by r.stiltskin on 2009-02-11
Only Google?  Maybe you inadvertently blocked them somewhere in your browser configuration?

I don't know of any built-in log that you can look at, but you can use Wireshark to log your connection attempt & see where it's failing.  You can find instructions in the Wireshark Users Guide at:

[http://www.wireshark.org/docs/wsug_html_chunked/ChapterCapture.html]("http://www.wireshark.org/docs/wsug_html_chunked/ChapterCapture.html")

---

### Post by Barriehie on 2009-02-11
> **r.stiltskin said:**
> Only Google?  Maybe you inadvertently blocked them somewhere in your browser configuration?

I don't know of any built-in log that you can look at, but you can use Wireshark to log your connection attempt & see where it's failing.  You can find instructions in the Wireshark Users Guide at:

[http://www.wireshark.org/docs/wsug_html_chunked/ChapterCapture.html](http://www.wireshark.org/docs/wsug_html_chunked/ChapterCapture.html)

Thank you for the link to wireshark.  It's installing now.  I checked /etc/hosts.deny and Google isn't in there.  I'll see what wireshark says.

Barrie

---

### Post by Barriehie on 2009-02-11
Gottit, I had to set FF to allow session cookies for Google and add Google to hosts.allow.

Barrie

---

