---
title: "Netflix redirect loop???"
date: 2015-07-30
forum: Desktop Environments
---

### Post by Jordan_Florchinger on 2015-07-30
I'm using the most recent version of chromium to watch netflix but when ever I try to load a video I get redirect loop error. I've cleared everything, ran in incognito... I have no clue why it keeps happening?

---

### Post by NathanRodriguez on 2015-07-30
You can try it on Chrome itself, it's available via PPA.

---

### Post by deadflowr on 2015-07-31
> **NathanRodriguez said:**
> You can try it on Chrome itself, it's available via PPA.
A 3rd party download/app, but not a PPA.
(PPA's are for packages from launchpad)

As far as I know chromium does not include the correct packages, like chrome, to be able to use Netflix.

You can go to google-chrome home page and then to the download page and select the one for Ubuntu/Debian.
Choose the correct arch-type either 32-bit or 64-bit.
(Hint: A quick way to figure out which arch you have you can run this
```
uname -a
```
if the output contains entries like i386, or i686 then you are using 32-bit.
if output contains x86_64 then you are running 64-bit.)

If the downloaded file doesn't ask to start installing, just open a File Manager(Ubuntu's is called Files) and go to Downloads and simply double click on the google-chrome-stable-something.deb and it'll automatically open the software center for installation.


However, if you mean chrome to begin with, then ignore all...
hope it helps

---

### Post by NathanRodriguez on 2015-07-31
deadflowr is right, sorry, Chrome it's available as a .deb package.

---

### Post by SeijiSensei on 2015-07-31
The best solution I've found for watching Netflix is to install [Pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") and use Firefox.  You'll also need to install a user-agent spoofer like [UA Control](http://neko.tsugumi.org/UAControl.html), so Netflix will think you're using Windows.  My current agent string for netflix.com reads:
```
Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:39.0) Gecko/20100101 Firefox/39.0
```

---

### Post by yancek on 2015-07-31
I've had pipelight installed on several Linux systems and it worked well, a little better on some than others even on the same hardware.  Chrome is simpler to install and seems to work well.  I haven't seen any Linux system that will run Netflix with Chromium other than Slackware.  

[http://alien.slackbook.org/blog/new-chromium-now-supports-netflix-natively-without-wine-plugins/](http://alien.slackbook.org/blog/new-chromium-now-supports-netflix-natively-without-wine-plugins/)

---

### Post by Jordan_Florchinger on 2015-07-31
Thank you for your help everyone, installing google chrome from googles website got it to work perfectly!! Thank you!

---

