---
title: "Code name to Release Version"
date: 2008-12-22
forum: General Help
---

### Post by lazman on 2008-12-22
I downloaded Ubuntu a couple of days ago and have discovered that there are code names for each release of Ubuntu. I have no idea what code name my version is. I also can not seem to find a code name to release version cross reference. I did find this page [http://www.ubuntu.com/community/ubuntustory](http://www.ubuntu.com/community/ubuntustory) that tells the story, and why each version has a code name but fails to be a comprehensive cross reference.

I have also discovered that some (if not all) Ubuntu users refer to release as the code name instead of the version number. For instance I was going to take a look at a game called Eternal Lands. The Eternal Lands website pointed me to this page [https://help.ubuntu.com/community/EternalLands](https://help.ubuntu.com/community/EternalLands) that gives clear and decisive directions to install the game. However when refering to adding the correct source repository according to the version of Ubuntu the reference to the code name and not the version is used. 

> NOTE: substitute your Ubuntu release name if you are not using hardy (gutsy and intrepid are supported too).  

Thus my situation of having no idea what code name I have installed prevents me from making a correct decision to the proper choice of repository.

My question is simply what code name do I have installed? Is there a complete cross reference somewhere that I have not found? Is it buried in the help files somewhere? I did try to look in the help by clicking on the great looking life ring and found some very useful information, but did not find a code name. 

I have installed Ubuntu 8.10 Desktop (the latest version): Includes the latest enhancements and is maintained until 2010 (64bit version) from this page [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) 

I will also use this post to make a suggestion to one of the persons here on the forums to create a sticky with this cross reference information so others like me that decided to try Ubuntu for the fist time can find a cross reference.

Thanks
~laz

---

### Post by Predator106 on 2008-12-22
No need; Use wikipedia, I use it for just about everything, because it has just about everything.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

:)

---

### Post by drs305 on 2008-12-22
The information for your version and kernel can be found with:
```

lsb_release -a && uname -r

```

---

### Post by jerome1232 on 2008-12-22
Also if you goto System-Administration-System Monitor, click on the System tab it should show your release as well.


ie mine says Ubuntu 8.10 (intrepid)

---

### Post by lazman on 2008-12-22
This is exactly what I was looking for. I was mistaken in looking in the help file for this information. 

Thanks also for the command line tip.

And thanks to both of you for a quick reply!
~laz

---

### Post by lazman on 2008-12-22
> **jerome1232 said:**
> Also if you goto System-Administration-System Monitor, click on the System tab it should show your release as well.


ie mine says Ubuntu 8.10 (intrepid)


As does mine. I did not even see this before. This is all great information. Thanks for your quick response!

As I have been using windows for years this linux endeavour is quite a new experience for me. My ignorance of linux and getting around around on it are great.

~laz

---

