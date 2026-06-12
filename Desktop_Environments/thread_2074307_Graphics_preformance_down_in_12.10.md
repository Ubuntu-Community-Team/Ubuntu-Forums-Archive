---
title: "Graphics preformance down in 12.10"
date: 2012-10-21
forum: Desktop Environments
---

### Post by JaySeeJC on 2012-10-21
Just upgraded from 12.04 to 12.10, and i notice my graphics performance has really dropped on my laptop. I have a nvidia optimus card meaning kwin is running on integrated intel graphics. The performance drop is especially noticeable when using the desktop cube effect. Has anyone else experienced these slowdowns and if they had found any fixes?

---

### Post by Jimmzone on 2012-11-12
> **JaySeeJC said:**
> Just upgraded from 12.04 to 12.10, and i notice my graphics performance has really dropped on my laptop. I have a nvidia optimus card meaning kwin is running on integrated intel graphics. The performance drop is especially noticeable when using the desktop cube effect. Has anyone else experienced these slowdowns and if they had found any fixes?

Hello!

I had a same problem with Kubuntu 12.10 on my new E530 ThinkPad Edge Lenovo laptop. Recently my dear friend notified me about that there
is a new kde release 4.9.3 and it can solve all my performance problems with kde desktop effects. After the upgrade, it works for me. So I suggest you update your kde from the Kubuntu Backports PPA.

You can do this by graphical user interface:
[INDENT]Follow the instructions can be found here: [http://www.kubuntu.org/news/kde-sc-4.9.3]("http://www.kubuntu.org/news/kde-sc-4.9.3")
After that you should click on the'Check for Updates' button of the 'muon' update manager application to fetch list of available packages and after click on the 'Install Updates' button to install the new packages.[/INDENT]
Or from console as well:
[INDENT]```

sudo add-apt-repository ppa:kubuntu-ppa
sudo apt-get install aptitude # if you do not have
sudo aptitude update
sudo aptitude safe-upgrade
```[/INDENT]

Finally, restart the computer. (The KDE restart may be enough.)
I hope this will help.

---

