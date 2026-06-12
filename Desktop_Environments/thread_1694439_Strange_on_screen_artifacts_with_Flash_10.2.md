---
title: "Strange on screen artifacts with Flash 10.2"
date: 2011-02-24
forum: Desktop Environments
---

### Post by mfraser on 2011-02-24
I'm running Kubuntu 10.10 with KDE 4.5.5 and I've noticed that since upgrading Adobe Flash to 10.2 I occasionally see artefacts left on screen after closing Firefox or even changing to another tab. This photo [http://twitpic.com/438nvx](http://twitpic.com/438nvx) is an example of what I'm seeing at the moment after visiting play.com's website, closing down Firefox and bringing up Kontact.

It stays in the same place on screen and this time is only visible when the background of the window is white, I've also had it after watching videos from YouTube where the background had to be black to see it.

If I do a screen grab, the artefact isn't visible.

Any ideas?

---

### Post by ankspo71 on 2011-02-24
Hi,
You might want to check out the firefox addon called Flash-Aid. [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) 
It removes any conflicting plugins, then installs the best flash plugin for your system, and then configures it for best playback.

If you would rather go back to version 10.1, you can find it is still  available in the repositories... but it is hidden from plain view. In Synaptic Package Manager, search for flashplugin-installer, select it, then go to the menu > 
package > 'force version', then select flash 10.1 from the dropdown list. Then click apply. 

When it is done installing, you can lock the 10.1 version so it doesn't get any updates. In Synaptic Package Manager, search for flashplugin-installer, select it, then go to the menu > 
package > 'lock version'.

Hope this helps.

---

### Post by lumbricus on 2011-05-09
Thanks for your help! For some strange reason also after downgrading to 10.1, the problem occurs on some pages. Although I'm quite sure that the artifacts arrised with the upgrade 10.1 -> 10.2. So for now I can't see any solution. What gives me hope is that the problematic pages seem to get more rare, at least youtube is now working fine (and wasn't before). But I have no idea why...

---

