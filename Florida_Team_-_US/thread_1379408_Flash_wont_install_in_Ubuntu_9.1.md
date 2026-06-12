---
title: "Flash wont install in Ubuntu 9.1"
date: 2010-01-12
forum: Florida Team - US
---

### Post by JWinters on 2010-01-12
I'm a Linux newbie and have been impressed with the Ubuntu distributions in the past.  I just installed Ubuntu 9.1 and immediately ran into an issue with Flash not installing.
I am surprised to hit this type of snag in what to this point has been a superlative distribution.  Also am surprised that my research hasn't shown others with a similar problem.  The install seemed to go fine.
 
Have researched and tried the answers that say to use a command in the terminal to install; have installed from adobe site, etc. all with no luck.  (by the way, how do you know just which version you are you to pick to install flash with?  They show at least 5 different choices!)
 
Firefox advises that flash is not installed and provides a link to install. When it tries to install flash I get messages that a flash install program seems is missing followed by a dialog box saying flash is installed.  It isn't!
 
I'd appreciate any help you gurus might be able to provide to get this issue resolved.  My alternative is to go back to 9.04 - all seemed to work ok there - but hate to go backwards.

---

### Post by itnet7 on 2010-01-12
JWinters, 

There are a couple of ways that you can install flash. The easiest way that I can tell you is to open a terminal and type the following: 

```
sudo apt-get install flashplugin-nonfree
```

There are a couple of other ways that you can do it though. Here is one other method that may help. Go to [Adobe's Site]("http://www.adobe.com") and on the right hand you will see the Get Adobe Flash Player Download Button, here is the current [link]("http://www.adobe.com/go/EN_US-H-GET-FLASH").

Once there you should see the Adobe Flash Player version 10.0.42.34 Linux (your version may show a more current one). Click the drop down to select the version to download. If you are using Karmic (or version 9.10), you can see the latest available they have listed is APT for Ubuntu 9.04+, that is the one that you should choose. Usually this way it will install flawlessly. 

If either of these methods do not seem to help you get it installed, then I would hop into the Florida Team's IRC #ubuntu-us-fl on freenode. If you are new to IRC then you can go [here]("http://www.ubuntu-fl.org/team-chat/") and use the more user friendly client!

Hope this helps. 

Chris Crisafulli
ITnet7/#ubuntu-us-fl

---

### Post by hyperAura on 2010-03-12
i had the same problem but doing it through the terminal solves the problem.. thnx

---

