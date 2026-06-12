---
title: "How do I update my drivers in Ubuntu 13.04 for my Radeon HD 6750?"
date: 2013-08-16
forum: Gaming &amp; Leisure
---

### Post by GameGuru on 2013-08-16
I went to play World of Warcraft through Wine and this is what I saw:

[IMG]http://i40.tinypic.com/2yzep7t.png[/IMG]

I followed a guide online before but then it messed up my computer if you saw my posts from a week ago.  What is a sure fire way of updating these drivers so I can play WoW and other games in Ubuntu?  Thanks.

---

### Post by Zeven on 2013-08-16
So you've tried to update them manually and it didn't work? Installing graphics drivers on Linux isn't the easiest task, that's for sure. I suggest you switch to [Manjaro]("http://manjaro.org/"). Your software will always be up to date, your graphics driver will update without breaking your system, and your kernel will be upgraded as well. It's pretty much like Mint, except it's a rolling release distro and based on Arch.

---

### Post by GameGuru on 2013-08-16
I don't really want to nuke my install again so I would love to get the latest drivers for my video card in Ubuntu 13.04.  Any recommendations?

---

### Post by DarkAmbient on 2013-08-16
Nothing shows up in Systemsettings -> Software & Updates -> Additional Drivers?

---

### Post by oldrocker99 on 2013-08-16
Updated drivers can be gotten thus:

> sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
> sudo apt-get update
> sudo apt-get upgrade

This will almost certainly upgrade your drivers; it works for me...

---

### Post by GameGuru on 2013-08-16
I actually installed the Synaptics Package Manager and it had the Catalyst Control Panel and drivers there and I installed them and am good to go, thanks!

---

