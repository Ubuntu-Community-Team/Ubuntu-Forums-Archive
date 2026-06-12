---
title: "web based SciFinder java drawing applet problem"
date: 2009-01-20
forum: Education &amp; Science
---

### Post by vyache on 2009-01-20
Hi, my university is switching from the client-based SciFinder (worked just fine under wine) to a new web-based version. It is based on java and should work under linux (in theory).  

Recommended web browsers:
          o Microsoft Internet Explorer, Versions 6.x and 7.x
          o Mozilla FirefoxTM, Version 2.0 and 3.0 
          o Apple SafariTM 3.0 and 3.1
JavaScriptTM, JavaTM, and cookies must be enabled. Java runtime environment (JRE) is needed for structure drawing.

I have: Ubuntu 8.10 (running KDE 4.1.4), Firefox 3.05 and Sun JRE 1.6.0 (ver. 10). I was able to start SciFinder but the structure drawing applet couldn't start :(.
The Java plug-in in Firefox is set up properly and works well according to this test page: [http://www.java.com/en/download/help/testvm.xml?ff3](http://www.java.com/en/download/help/testvm.xml?ff3).
Does anyone else have the same problem? Any possible solutions?

---

### Post by rutulian on 2009-02-19
Yeah, I'm having the same problem. It just hangs at the loading applet dialog. I haven't found a solution yet....

---

### Post by Kenno on 2009-03-25
Same here. I contacted CAS support and they say they don't support linux. Nevertheless, I submitted a bug report with a java console dump. They said they'd forward it to their developers. I recommend anyone reading this to do the same in order to make them notice that a significant percentage of their users runs Linux.

The strange thing is that I've seen dozens of extremely complicated and non-standard Java applets that worked flawlessly on Windows and Linux. It's almost as if someone somewhere down the line did some specific effort to make it not work on Linux. Then again, never underestimate the power of incompetence. It follows from the "infinite monkey theorem" that, if your application contains an arbitrary large amount of bad code, at some point you will succeed in accidentally triggering a rare platform-dependent bug. Either way it's scary.

---

### Post by rutulian on 2009-12-06
SciFinder web works now. I just tried it again on a whim a month ago, and the applet started without a problem. So I guess they fixed it, even though "they don't support Linux."  ;)

---

