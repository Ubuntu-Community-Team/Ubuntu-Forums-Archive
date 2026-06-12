---
title: "Unity interface unresponsive"
date: 2011-05-25
forum: Desktop Environments
---

### Post by aj_the_first on 2011-05-25
I recently upgraded to 11.04, and I loved it for a few seconds until I saw that it ALWAYS displays recent documents and recent downloads.  I found out that the downloads only displays the default download folder, but recent documents was unacceptable.
So in searching for a solution, I followed this guide:
[http://linux.aldeby.org/ubuntu-natty-11-04-unity-clear-recent-documents.html](http://linux.aldeby.org/ubuntu-natty-11-04-unity-clear-recent-documents.html)
I followed the steps, but couldn't get the GUI interface for folder exclusions, 
but I saw that Zeitgeist could be uninstalled to get it to stop accessing my recent documents.  ...  but read-over the part where it told me that all access to applications would be lost if I uninstalled zeitgeist.  I didn't realize that it drives the whole Unity interface engine, and now I can't look for nor access anything other than my quick launch bar.  Unfortunately that means all admin apps and even the ability to even change the color scheme.
I immediately reinstalled zeitgeist in terminal and the installation was successful, but after a re-boot Unity still doesn't work at all.
Can anyone provide me some help?
Thanks,
AJ

---

### Post by Krytarik on 2011-05-25
First, reinstall "unity":
```
sudo apt-get install --reinstall unity
```If you don't have a launcher for the terminal in the Launcher, press Ctrl+Alt+T to get one.

Then see this guide on how to blacklist certain directories in Zeitgeist, among other settings:
[http://ubuntu4beginners.blogspot.com/2011/05/clear-tweak-zeitgeist-historys-settings.html](http://ubuntu4beginners.blogspot.com/2011/05/clear-tweak-zeitgeist-historys-settings.html)

Greetings.

---

