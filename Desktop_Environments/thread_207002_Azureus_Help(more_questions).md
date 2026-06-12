---
title: "Azureus Help(more questions)"
date: 2006-07-01
forum: Desktop Environments
---

### Post by xpix on 2006-07-01
Hello,

Although my Azureus works I have some problems with it and I would like to solve them but I am not sure how.

**1. **When I start Azureus i get a PopWindow:
**Azureus Updater**
Here I am asked to aloow the update "azupdate/Azureus Update Support 1.8.2_CVS"
I Click on UPDATE button and an "Install Verification Failed" pop-up appears:
Verification of 'azupdater/Azureus Update Support' failed: Signature missing from file.
I click OK and on right left coner a windows appears: 
Version 1.8.2_CVS of plugin 'azupdater' failed to install - Verification Failed

But if I close all this popups and info messages Azureus still works. 

I Hope someone can help me with this.

**NOTE: **I installed Azureus like in this post:[http://ubuntuforums.org/showthread.php?t=193660](http://ubuntuforums.org/showthread.php?t=193660)

**2. **When I load some torrents(not all of them, some work, some do not)
I get an error in the Status Column:

Error: Operation not permitted, setLength fails(allocateFiles new:*Path to my location*)

I read a post about something similar but did not worked. here is the post:[http://lists.serverhive.com/pipermail/cylug-main/2005-March/000210.html](http://lists.serverhive.com/pipermail/cylug-main/2005-March/000210.html)

So, in the post the guy increased the "Size of cache in MB". I did the same to the maximum value(for me 32) and offcourse tried different sizes, restarted, etc. Still the same problem.

Note: Some torrents work if I open them with BitTornado and some do not work at all. Could it be that the torrent files have a different "version" that the ones supported by Azureus and BitTornado? I usually use torrentspy.com.

**3. **Here I will talk about NAT:
So I think I have a NAT problem. My computer is behind a router (an old computer with Smothwall installed).
My question is: What do you usually put in the "Source port or range:"?
I know what "Destination IP:" and "Destination port" means but for "Source port or range:" all I can think of is "ALL RANGE"


I hope someone can help.

Thank You :)

---

### Post by deathbyswiftwind on 2006-07-01
Have you tried downloading azureus off the sourceforge site? I use the bz2 file and just unzip it into my home. Then all you have to do is create a symbolic link in usr/local/bin  It works and doesnt give any errors

---

### Post by Thund3rstruck on 2006-07-02
I had to use one of the howtos to get it to run at all and now it works but if I don't babysit the entire download it will error out with all kinds of abstract errors. I try to update it with the auto-updater but it tells me that update fails due to signature failure.

The version on sourceforge is 2.4.0.2 and that older than the one I have installed.

---

### Post by kinematic on 2006-07-02
azureus just doesn't work correctly on ubuntu(or debian or any debian derived distro's)in my experience.
i recommend you use bittornado....it's also very configureable and works just as well(it's in the repo).

---

### Post by Thund3rstruck on 2006-07-02
kinematic,

 Thanks for the advice... I actually got so sick of azureus failing out that just last night I got uTorrent running under Wine. I'd much rather use something Linux native so I'll grab bitTornado and give that a try this afternoon.

---

### Post by kinematic on 2006-07-02
the strange thing is that azureus only works for me on rpm based distro's...go figure.

---

### Post by xpix on 2006-07-03
[QUOTE=kinematic]azureus just doesn't work correctly on ubuntu(or debian or any debian derived distro's)in my experience.
i recommend you use bittornado....it's also very configureable and works just as well(it's in the repo).[/QUOTE]

I tried BitTornado but if I remember well for every torrent I have a BitTornado window.
When having 3 or 4 BitTornado windows my system is not so fast. That's why I swithed to Azureus.

---

### Post by msandersen on 2006-07-03
I originally installed Azureus using **[this guide]("http://ubuntuforums.org/showthread.php?t=144546")** by Artificial Intelligence and had no problems, except I had to change permissions on the Azureus folder, since the first thing it did was download an update which didn't have permission to install. I set **Group** to **admin** and permissions to **g+w** (drwxrwxr-x). Arnieboy posted that Automatix is now using his method, so later I tried it, and it worked fine too. Again I think I had to change the permissions manually on /opt/azureus, though. 
So, I can recommend using Automatix to install Java and Azureus. It's part of an option to install several P2P programs, though, not an individual option.

---

