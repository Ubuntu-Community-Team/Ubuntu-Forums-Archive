---
title: "Scheduled events in Ubuntu"
date: 2009-04-08
forum: General Help
---

### Post by Amadameus on 2009-04-08
First of all, I would like to say that I am absolutely DELIGHTED with Ubuntu and recommend it to everyone I give computer advice to!

However, this caveat: I am what you would call an "absolute beginner." I'm currently teaching myself Unix and I have a roommate who is well versed in Terminal functions, but I do not feel confident at all sticking my metaphorical monkey wrench in the engine of my computer's OS.

Here's the dilemma: Ubuntu will not update itself. I'm currently running a version of Feisty that is quite outdated and every time I try to pull up a list of updates, the server fails to load. I have tried connecting to Ubuntu's IP address directly as well as several local mirrors with no success. One simple, brute-force solution would be to burn a boot CD of Ubuntu's latest and greatest, then reinstall the OS. It seems like a little bit of overkill, but there are others would call sitting over the computer for an hour pinging servers and cursing "overkill."

Is this a known problem with Feisty? Has anyone else had problems with this? We suspect that the update servers simply don't carry Feisty information any more, due to its age. This would be a relief, because it means the problem is not on our side of the intertubes.

Does anyone else have advice or insight into this?

Many thanks,
-Amad

---

### Post by kanikilu on 2009-04-08
Feisty reached end of life in October 2008: [http://www.ubuntu.com/news/ubuntu-7.04-end-of-life](http://www.ubuntu.com/news/ubuntu-7.04-end-of-life)

Since no new security updates will be made available to it, I think it's advised to [upgrade](http://www.ubuntu.com/getubuntu/upgrading). 

Since you are several versions back, I think it's suggested to do the upgrade in multiple steps, 7.04 -> 7.10 -> 8.04 -> 8.10 -> (9.04 beta). 

Support for 7.10 will [end this month](http://www.ubuntu.com/news/ubuntu-7.10-eol), so I would suggest going to at least 8.04, anything above that is optional...

// Edit - Of course, as you mentioned, you can always go get the ISO for whatever version you want and upgrade from there or do a clean install, but you can use the update manager to do distribution upgrades if you want...

// Edit 2 - BACKUP BEFORE UPGRADING! ;)

---

### Post by wolfen69 on 2009-04-08
> **kanikilu said:**
> I think it's suggested to do the upgrade in multiple steps, 7.04 -> 7.10 -> 8.04 -> 8.10 -> (9.04 beta). 


i highly advise against going that route. you are asking for trouble. it is best to wait until ubuntu 9.04 goes final in 15 days and do a fresh install. or go with ubuntu 8.04 which is a long term support version. besides, upgrading 1 version at a time would take many hours and probably give you problems. since 7.04 is no longer supported, i'm not even sure you can upgrade. but anyway, fresh install is best.

---

### Post by DeMus on 2009-04-08
> **wolfen69 said:**
> i highly advise against going that route. you are asking for trouble. it is best to wait until ubuntu 9.04 goes final in 15 days and do a fresh install. or go with ubuntu 8.04 which is a long term support version. besides, upgrading 1 version at a time would take many hours and probably give you problems. since 7.04 is no longer supported, i'm not even sure you can upgrade. but anyway, fresh install is best.

I fully agree. Doing upgrade after upgrade will resort in many files staying behind form installation and not needed by the next, resulting in trouble.
Back up all important data you have by April 23 , download 9.04 and do a fresh install, or as the previous poster also mentioned do a fresh install now using 8.04 for long term support.

---

### Post by 3Miro on 2009-04-08
The only time I tried a version upgrade it did not work. For such a big jump (7.04 to 8.10 or 9.04) you should probably make a clean install anyway.

BACKUP

Check the "expiration" dates for the version, I think 9.04 and 8.04 will go out of date at about the same time, so you will not be getting anything form the LTS.

---

### Post by kanikilu on 2009-04-08
Just to be clear, I'm not necessarily advocating one upgrade method or the other, just reiterating information from the official webpage. 

Also, while I always prefer a clean install where possible (I just did one last night at home from Intrepid to Jaunty), there's no reason a dist-upgrade *shouldn't* work.

In the past, I successfully did an iterated, in-place upgrade from 7.10 -> 8.04 -> 8.10 without any significant problems.

...maybe I'm just lucky \\:D/

---

### Post by raedbenz on 2009-04-08
I highly recommend to go for 8.04 immeduiately and stick with it for now, if ur hardware requirements is enough for it.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by dcstar on 2009-04-09
> **3Miro said:**
> 
.........
Check the "expiration" dates for the version, I think 9.04 and 8.04 will go out of date at about the same time, so you will not be getting anything form the LTS.

8.04 will still be supported **long after** 9.04 is forgotten:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by dcstar on 2009-04-09
> **Amadameus said:**
> 
.........
Here's the dilemma: Ubuntu will not update itself. I'm currently running a version of Feisty that is quite outdated and every time I try to pull up a list of updates, the server fails to load. I have tried connecting to Ubuntu's IP address directly as well as several local mirrors with no success. One simple, brute-force solution would be to burn a boot CD of Ubuntu's latest and greatest, then reinstall the OS. It seems like a little bit of overkill, but there are others would call sitting over the computer for an hour pinging servers and cursing "overkill."
........
Does anyone else have advice or insight into this?


The painless path to updating (not "upgrading") Ubuntu versions is:

[LIST=1]
[*]Create a separate /home partiton (so all you user data/settings are preserved when you do a new install of any version)
[*]Save all of your installed package info using the Synaptic "Save Markings" function, you can then use "Read Markings" to reinstall of of your packages when the new version is installed.
[/LIST]
These two simple things will give you a system that can be updated with a minimum of fuss.

---

