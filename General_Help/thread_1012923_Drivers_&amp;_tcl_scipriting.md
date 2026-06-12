---
title: "Drivers &amp; tcl scipriting"
date: 2008-12-16
forum: General Help
---

### Post by zero_ZX on 2008-12-16
Hi all,
I'm very new to linux (actually i installed 6 minutes ago).
I must say, I'm amazed!
Automatic detecting drivers and installing them! I have never experianced such a fast browsing on the internet, theres abselutely ZERO waiting time!! OMFG this is awesome..

Well since im new i got some problems.. im using nvidia and ubuntu asks for accelerate drivers or so.. (version 177), and im having a very hard time on how to install/download those..
Well it says it needs to be activated, so i pressed activate, and download gets stucked at 0% and suddenly shuts down after 30 secs or so..

Next, i wanted to install amsn, after i found out that there was something called "permissions" (LOL), the package worked like a charm, until i needed something called tcl scripting language or similar. 
Says i must use a native package manager or apt-get. 
I really need some help on this, sry for being such a nub, but every one gotta start somewhere right :)

Further more i cannot download any updates :( 
error:
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

I know there are many posts with tcl problem, but i can't add it via the package manager since it says my download folder is locked :S

So.. Now that i searched for some time i returned:
sudo rm /var/cache/apt/archives/lock
was the solution for the download problem :)


EDIT::: Everything solved, thanks to search button. Please close thread or ignore :)
P.S. Sorry for my bad english :)

---

