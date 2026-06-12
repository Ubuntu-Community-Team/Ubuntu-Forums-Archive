---
title: "removing updates under 8.10"
date: 2008-12-16
forum: General Help
---

### Post by james.wilde on 2008-12-16
I removed pulseaudio from my 8.10 installation some weeks ago in order to get sound working.  Now I see that the latest bunch of updates for 8.10 include 9 for pulseaudio.

I normally rely on just loading all updates that arrive without filtering, working on the principle that the people preparing these updates are very much more competent than I am and wouldn't deliberately screw up my operating system.

However, trying - and failing - to get pulseaudio working properly and finally finding a reliable method of removing it without having to reinstall Ubuntu has made me cautious.  In the first place, the entire home directory is now a separate mount, just in case.  In the second place, I now study the update list to see if there is anything there relating to pulseaudio, having seen a threat in one thread that the next pa upgrade could break my system.

So I'd appreciate help with the following question: is there any way to configure the update process so that it does not include any pulseaudio updates, and doesn't present me with the ones that have already come.  I've just installed everything else, and after the check, the system comes back with a suggestion that I perform these 9 updates.  One day I'm going to forget to make this check.

TIA

//James

---

### Post by Sukarn on 2008-12-16
Go to **System -> Administration -> Synaptic Package Manager**

Click on the package name that you want to block, at the top of the window click on **Package -> Lock Version**

---

