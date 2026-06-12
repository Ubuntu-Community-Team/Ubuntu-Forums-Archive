---
title: "Java issue in Chrome browser"
date: 2014-05-22
forum: Desktop Environments
---

### Post by sharath2 on 2014-05-22
[TABLE]
[TR]
[TD="class: votecell"]

              [/TD]
              [TD="class: postcell"]                I am running Ubuntu 14.04 64 bit. Installed java on this. 

  Version 1.7.0_55. trying to enable java on google chrome but have failed. 

  I symbolic linked libnpjp2.so to /opt/google/chrome/plugins

  I also have installed icetea plugin . It works fine in for firefox. But in chrome it says install java runtime environment from [www.java.com](www.java.com)
 
Can someone please help me out. I am stuck up from past 2 days

      

[/TD]
[/TR]
[/TABLE]

---

### Post by startas on 2014-05-22
How did you install java ? I suggest using ppa:webupd8team/java, that way java will work with chrome, i tried it.

---

### Post by a8j8i8t8 on 2014-05-23
[COLOR=#333333][FONT=UbuntuRegular]You cannot get Java to work on Chrome 35.
Its because of the removal of the older plugin NPAPI. 
The bug report is here:[/FONT][/COLOR][https://code.google.com/p/chromium/issues/detail?id=375909](https://code.google.com/p/chromium/issues/detail?id=375909)[COLOR=#333333][FONT=UbuntuRegular]. You can try and follow the thread for this discussion here: [/FONT][/COLOR][https://groups.google.com/a/chromium.org/forum/#!topic/chromium-dev/xEbgvWE7wMk](https://groups.google.com/a/chromium.org/forum/#!topic/chromium-dev/xEbgvWE7wMk)

---

