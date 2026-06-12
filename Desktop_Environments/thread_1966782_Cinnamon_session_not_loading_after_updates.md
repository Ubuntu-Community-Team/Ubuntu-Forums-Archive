---
title: "Cinnamon session not loading after updates"
date: 2012-04-27
forum: Desktop Environments
---

### Post by Redsandro on 2012-04-27
[SIZE="1"]I initially wrote this post as a reply to the [Cinnamon on 12.04]("http://ubuntuforums.org/showthread.php?t=1941288&highlight=cinnamon&page=4") topic, but the forum for +1 is now closed.[/SIZE]

I've been running Ubuntu **Precise** since **12.04 Beta 2** with **Cinnamon**.

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-nightly
sudo apt-get update
sudo apt-get install cinnamon
```

All is ofcourse fully updated, so I don't have the development version of Precise anymore.

However, since last update, my Cinnamon session won't work anymore. I will get my desktop-image, and nothing happens. Pidgin will start, without window-decoration or -controls, because it's coded to autostart. When I create a new user and try to login with Cinnamon session, it too shows an empty panelless desktop with a mouse cursor.

What went wrong? How can I fix this? I am writing this from Gnome Shell, but obviously, I want Cinnamon back.

-edit-

I now have Cinnamon 1.4.0-20120427044007-precise. I thought I should add the stable repository: **sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable**
But how do I choose a version? I rename the nightly .list to .list.bak but after update, the 'latest version' is still the same as 'installed version'.

Is maybe the nightly the same as stable today?

---

### Post by Redsandro on 2012-04-27
Cinnamon 1.4.0-20120427044007-precise > **Synaptic** > Package > **Force Version** > **1.4.0-2ubuntu1~precise1**

Cinnamon works again, unfortunately I now have the Window-decoration bug on every reboot again:
[https://bugs.launchpad.net/linuxmint/+bug/987791](https://bugs.launchpad.net/linuxmint/+bug/987791)

How can I keep Cinnamon updating to the stable version without using force-version?

---

### Post by adidalax on 2012-09-23
I'm actually having a similar issue. How exactly did you get around this? I'm having the issue after a fresh install of 12.04 64-bit, and a fresh install of Cinnamon per instructions here:  [http://www.linuxbsdos.com/2012/09/20/install-cinnamon-1-6-in-ubuntu-12-04-lts/](http://www.linuxbsdos.com/2012/09/20/install-cinnamon-1-6-in-ubuntu-12-04-lts/). 

The latest out in the repo that got installed was 1.6.0-0ubuntu1~precise1.

Also, as a sidenote, if I choose just "Cinnamon" I get a standard Gnome desktop as well.

Any help is much appreciated.

Thanks,

Jon

---

### Post by Redsandro on 2012-09-24
I used to have a fixed version to 1.4.0 by forcing it in Synaptic.

Then a few months later, I unforced everything, and now I just have the latest 1.6.0 from the repo.

I no longer have the issues I mentioned before, and I never reinstalled Ubuntu either. I still run the same version I upgraded from 12.04 Beta 2. I guess some updates finally worked everything out for me.

One thing you can try is to create a new user, see if it has the same problems. If not, then it's probably a conflicting setting in your home directory. As for the rest, I'm sorry I wish I could be more helpful.

---

