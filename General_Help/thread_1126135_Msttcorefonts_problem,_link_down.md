---
title: "Msttcorefonts problem, link down?"
date: 2009-04-15
forum: General Help
---

### Post by afrodeity on 2009-04-15
I can't seem to access the link [https://lists.ubuntu.com/archives/ubuntu-es/2007-October/026823.html]("https://lists.ubuntu.com/archives/ubuntu-es/2007-October/026823.html") to the solution for solving this problem.

The conversation is at [ http://ubuntuforums.org/showthread.php?t=676063 ]("http://ubuntuforums.org/showthread.php?t=676063")

---

### Post by Sorivenul on 2009-04-15
The problem in the links you provided seems more along the lines of apt/dpkg wanting to try and download msttcorefonts whenever a package was installed. The resolution to their problem was to clear the dpkg info regarding msttcorefonts. The users ran:
```
sudo rm /var/lib/dpkg/info/msttcorefonts.*
``` 
and
```
sudo apt-get purge msttcorefonts
```
This resolved the issue of msttcorefonts being downloaded each time a package was installed.

This doesn't seem to be your issue, though. You want to download msttcorefonts and have them installed, right? If that's the case there are a number of things you can do:
1.) Wait. The fonts are downloaded from SourceForge mirrors, which may be being serviced when you are trying to download.
2.) If you are beind a proxy (or even if you aren't), you may want to look at this thread which outlines how to modify your wgetrc file which may be causing the problem:
[http://ubuntuforums.org/showthread.php?t=75413](http://ubuntuforums.org/showthread.php?t=75413)
3.) Use an alternative method to install msttcorefonts. A few are outlined in this thread:
[http://ubuntuforums.org/showthread.php?t=76655](http://ubuntuforums.org/showthread.php?t=76655)

---

### Post by afrodeity on 2009-04-20
Thanks, I managed to fix the initial problem, and will download the fonts and install once I have enough bandwidth - stuck in South Africa with an ISP that caps international bandwidth. Do you know anything about DNS? Am looking into it so that I can defeat the censorship.

---

### Post by afrodeity on 2009-05-19
One of this things I guess, but still haven't fixed this problem because of the lack of a local mirror for the msttcorefonts. Surely stuff like this should get mirrored in the "third-world", particularly Africa?

---

### Post by Legace on 2009-05-19
> **afrodeity said:**
> One of this things I guess, but still haven't fixed this problem because of the lack of a local mirror for the msttcorefonts. Surely stuff like this should get mirrored in the "third-world", particularly Africa?

Try to change server from System -> Administration -> Software sources

---

### Post by afrodeity on 2009-05-23
This is magic. I ran

```
sudo dpkg-reconfigure --force msttcorefonts
```

Which then gave a very nice graphic interface where I could set-up the proxy. The fonts are now downloading. Very sweet.

---

### Post by glotz on 2009-05-23
May I recommmend [http://en.wikipedia.org/wiki/Liberation_fonts](http://en.wikipedia.org/wiki/Liberation_fonts)

---

### Post by afrodeity on 2009-05-23
Sorry to sound like a complete noob, but how would one install such a thing as liberation font?

---

### Post by yoasif on 2009-05-23
> **afrodeity said:**
> Sorry to sound like a complete noob, but how would one install such a thing as liberation font?aptitude install ttf-liberation

---

### Post by glotz on 2009-05-23
Another way would be to use system > admin > synaptic package manager.

Find the package and select it for install and apply changes.

---

### Post by afrodeity on 2009-05-23
thanks.

---

