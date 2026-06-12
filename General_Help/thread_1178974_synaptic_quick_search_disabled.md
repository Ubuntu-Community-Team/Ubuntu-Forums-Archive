---
title: "synaptic quick search disabled"
date: 2009-06-05
forum: General Help
---

### Post by ZOOstation on 2009-06-05
This might be a simple issue, but my Quick Search box in Synaptic Package Manager is inaccessible. It's there, but grey and unusable.

---

### Post by gettinoriginal on 2009-06-05
Is that the only thing greyed out??  Have you tried the "Reload" button??

---

### Post by drs305 on 2009-06-05
Can you successfully run this command? I've used a search term of "tunneld" which provides 2 returns in both the command and in the search box of synaptic:
```

apt-cache search "tunneld"

```

If it doesn't run, then some function of the APT system is broken. One possible rememdy may be to rebuild the cache by running either of the following commands. Although the command rebuilds the *cache* and not really the *search* function perhaps it will reset something that is preventing the search function from properly running. Both commands do the same thing.
```

sudo apt-get check
*or*
sudo apt-cache gencaches

```

---

### Post by Thingymebob on 2009-06-20
Check you have the apt-xapian-index package installed
```
sudo apt-get install apt-xapian-index
```then force a rebuild of the index
```
sudo update-apt-xapian-index -vf
```

---

### Post by JoeDuncan on 2009-06-25
First off, thank you Thingymebob, I have had this exact problem since upgrading from 8.04 to 8.10. It even persisted across 8.10 to 9.04.

It worked just fine on my home machine (which went through the same upgrades) but it never worked on my workstation.

I have been looking for a solution to this for a while and couldn't find one anywhere.

I have tried uninstalling and re-installing synaptic multiple times to no avail.

Installing "apt-xapian-index" fixed the problem immediately, which brings up the question: why is it not listed as a dependency for Synaptic? It seems necessary for the "Quick Search" functionality, and the association is not obvious, so it really should be listed as a dependency.

I see that "apt-xapian-index" is listed as a "Recommendation" by synaptic, but that is next to useless if it never gets installed when synaptic is installed or re-installed. 

Regular users are not going to go looking through package dependencies to see if there's something they missed. If it's needed it should be a dependency, if, for whatever reason it can't be made a dependency, then the "Recommendation" status should at least do *SOMETHING* to let the user know that they are perhaps not getting complete functionality.

Just my 2p. Thanks again!

---

### Post by Thingymebob on 2009-06-25
No problem it took me about 4 hours of googling when i first came across the problem. 

Difficult one on dependencies, as a dependency is a requirement i.e the program will simply not work without it, while a recommendation is there to increase functionality and provide extra features. So in reality apt-xapian-index is a recommendation not a dependency. there is a setting in synaptics preferences>general tab to treat recommends as dependencies, I don't know the default status of this but mine is un-checked. you can also use apt-get install with the --install-recommends option to do the same. The issue here of course is you'll probably end up with a load of guff installed that you don't need and will never use (MS anyone?) probably not a problem if you have a monstrous hard drive though.

However the default install should include the package, I've now done two installs and had to install this package on both, thought it was just me, perhaps not and I'll head on over to launchpad.

---

### Post by Thingymebob on 2009-06-25
So it's not really a bug so I didn't go over to launchpad but have posted an idea on brainstorm here:
[http://brainstorm.ubuntu.com/idea/20418/](http://brainstorm.ubuntu.com/idea/20418/)

---

### Post by iluii on 2010-11-06
THANK YOU!! took me a while to find this

why it isnt installed by default is very strange, maybe its because im trying lubuntu and it so focused on being light weight

---

### Post by zigmo on 2011-04-04
I just did a Lubuntu install on an old system and had the same problem. Thanks for the quick solution - it really helped me out.

---

### Post by Big Lizard on 2012-01-21
> **Thingymebob said:**
> Check you have the apt-xapian-index package installed
```
sudo apt-get install apt-xapian-index
```then force a rebuild of the index
```
sudo update-apt-xapian-index -vf
```

This worked for me on Lubuntu 11.04.

I found the "install apt-xapian-index" on many different posts and sites, but on my computer it would cause the CPU to run at 100%. This was the first post I found that says to rebuild the list, which worked and the CPU now runs normally. (Why? When you install apt-xapian-index, it requires python-xapian to be installed as well. From experience with other software that requires Python support, the Python addition is what causes the CPU problem on this and *some* other Python supported software.)

---

### Post by stratoka on 2012-03-30
Thanks, it worked on Debian Unstable to.

---

