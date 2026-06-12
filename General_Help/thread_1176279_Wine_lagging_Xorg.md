---
title: "Wine lagging Xorg"
date: 2009-06-02
forum: General Help
---

### Post by brodiepearce on 2009-06-02
Hi,

As of about a few days ago, whenever I start a program in wine, xorg will start to chew 100% of one of my CPU cores and lag badly until the program has finished loading.  Lately it has not stopped lagging at all until all wine processes have been killed.

This is happening with every program I use in wine including foobar2000 etc. etc.  I have tried purging and reinstalling wine from the jaunty repos (currently wine-1.0.1), and also just now I've tried the latest development build 1.1.22 to no avail.

Anyone had this happen before?

---

### Post by lovinglinux on 2009-06-02
This happened to me due to a game that uses PunkBuster. This application installs as service, so whenever I started any applications with Wine the stupid Punkbuster service was loaded and lagged my machine a lot.

You might want to check which services are being loaded with Wine.




*UKeywords: 649167 2009 june wine service lag punkbuster*

---

### Post by brodiepearce on 2009-06-03
> **lovinglinux said:**
> This happened to me due to a game that uses PunkBuster. This application installs as service, so whenever I started any applications with Wine the stupid Punkbuster service was loaded and lagged my machine a lot.

You might want to check which services are being loaded with Wine.




*UKeywords: 649167 2009 june wine service lag punkbuster*

I did notice when I last started Exact Audio Copy that a process "services.exe" was started and was the last one to die.

---

### Post by lovinglinux on 2009-06-03
> **brodiepearce said:**
> I did notice when I last started Exact Audio Copy that a process "services.exe" was started and was the last one to die.

The process "services.exe" is expected to run, the problem is what is loaded with it. I don't remember exactly if a new installed service will load within "services.exe" or as a separate process.

---

### Post by brodiepearce on 2009-06-05
On second glance, I'm getting this problem with any new window, including firefox etc. etc.

New thread posted [here](http://ubuntuforums.org/showthread.php?p=7403386)

---

