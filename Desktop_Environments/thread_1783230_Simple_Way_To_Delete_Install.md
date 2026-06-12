---
title: "Simple Way To Delete Install?"
date: 2011-06-15
forum: Desktop Environments
---

### Post by BruisedQuasar07 on 2011-06-15
Is there a simple way to delete an existing Linux Distro install so you can install a new version or distro in the partitions where a current one resides?

We have several laptops, all of which are at least dual boot with Windows and with a Linux Distro. A few have Windows and two Linux Distros.

What we want and need to do, without disturbing the Windows install is simply remove a current Linux install and replace it with another install, a simple way. We cannot find a simple Partition command of eliminate install or install over existing install.

Since the movement in Linux community for four years now is "easy", "simple", and "user friendly" you would think Ubuntu project would by now have a simple, low risk way of doing this. The delete and expand specific partitions method is very risky (to the O/S installs one wished to keep intact) and requires more partition study than all but a few people have interest or time to invest in.

Anyone know of a simple way to replace an install. What puzzles us is why Ubuntu has not come up with a simple command that allows users to replace one Ubuntu version with another, or at least uninstall back to a previous install when a user finds the new version tanks his system and requires hours of study to figure out how to get his basic hardware up and running. 

I realize that Linux community members tend to accept criticism about as gracefully as a Republican or a Democrat but progress cannot happen without constructive or well meaning criticism. For those so tempted, please spare me the "stupid", "its easy idiot", "Works fine on my PC" or
"this is the best of all possible worlds" replies.

--Bruised

---

### Post by cmwhidmore on 2011-06-15
Actually, alot of installers (at least the ones ive seen) have an option anymore that says something like (Remove <your old distro> and install.

If yours doesn't, then open the installer's partition manager, and select the Linux partitions manually. If you rub a couple brain cells together, it isn't all that hard.

If you are just upgrading to a newer release of the same release (ie from ubuntu 10.10 to 11.04), just open your favorite terminal, and type either ```
 sudo apt-get update
sudo do-release-upgrade 
```

or, the less-preferred, but just as easy: ```
 sudo apt-get update
sudo apt-get dist-upgrade 
```

with these options, you don't have to worry about backing up or moving your personal files, settings, etc.
these (should) carry over

------------
ALWAYS backup first
------------

---

### Post by wildmanne39 on 2011-06-16
Hi, there is one problem with doing an upgrade, natty is not working very well for a lot of people that have upgrade, I myself finally had to do a clean install, the best thing to do when you are installing the new version of linux is manually partition  and reformat where your old system was on the partition and install the new one. That way the old one is completely gone and you do not have to worry about conflicts from upgrading.

---

### Post by BruisedQuasar07 on 2011-06-16
> **wildmanne39 said:**
> Hi, there is one problem with doing an upgrade, natty is not working very well for a lot of people that have upgrade, I myself finally had to do a clean install, the best thing to do when you are installing the new version of linux is manually partition  and reformat where your old system was on the partition and install the new one. That way the old one is completely gone and you do not have to worry about conflicts from upgrading.

Precisely. Upgrades are simple and quick. As I mentioned, I want to replace an install, not upgrade. You get it. Can you steer me to simple instructions for using Partition Manager (PM) to replace one install with another. We use PM but do not see a way to get the addresses it demands you input so you hit the correct partition borders. 11.04 upgrade was THE worst mistake we ever made! Our mistake is we had come to trust team Ubuntu as we had never trusted any O/S project, ever. We will NEVER make that mistake again. An upgrade message came into our computers and we just pulled the trigger.

Every one of them were working great under 10.04 and 10.10. 11.04 turned our fine working systems, ranging from Thinkpads to Dell (business class), into something worse than we had seen even under Windows 3.2 and Vista. 

We got rid of Unity fast but that just improved a horrid install. 11.04, contrary to what Ubuntu cult members claim, is flawed itself, even with many updates we have nothing but goofy acting flash, sudden cursor control freeze ups, etc. The bug list is long. I know it went through Beta testing. What a joke. The same group that beta tested 11.04 must have tested Windows Vista! 

We need a clean install of 10.04. We can say "simple" and rub some brain cells together to outsiders to our areas of expertise but we would never do so. We know the average car mechanic or computer mastro isn't interested in becoming investment tycons, so we do not expect everyone to invest 1/2 their awake time to learning the stock market.

A biochemical engineer doesn't want to become a wall street expert just to save for retirement. My physician doesn't want to become an economist in order to know how to organize his practive. My wife doesn't want to become an auto engineer in order to drive a car. 

If you can't make it in the real world, professor isn't the only way to boast your ego and think you can look down on people. Learn more about an operating system than a user should need to and insult people who have other things on their to do list. 

Its not a matter of IQ or refusal to think. Its a matter of time agenda and whether or not a person has some marketable skill set. What gets me is true Linux masters are in high demand and earn more than Windows ITs. I have advised a few on investing. I understood they don't want to study the market, just as I do not want to learn programming to work an O/S but then...they have real jobs and earn serious money with Linux. The others are wannabes. 

Linux could have been much more widely used today if it were not for the many pretentious  wannabes attracted to it and the "support" forums, who drive sane people away from Linux.

--Bruised

---

### Post by pony-tail on 2011-06-16
I AM a motor mechanic -
Anyway my suggestion would be to boot up with a 10.02.4 disk and install onto existing partitions ( They will be the ones that are not NTFS ) or if you are only using Ubuntu and not dual booting let the installer use the whole drive .
I too found 11.04 to be severely flawed and had to re-install and I was both annoyed and disappointed with that release ( what were they thinking )
But to continue - a Ubuntu install is usually easier than a Vista install .
I would suggest you try a clean install on one machine and see how you go .

---

