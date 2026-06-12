---
title: "nepomuk/strigi storage size abnormous."
date: 2010-06-13
forum: Desktop Environments
---

### Post by japs_it88 on 2010-06-13
Hi all,
the other day i found to my surprise that nepomuk store size inflated to 1.6GB. I have both nepomuk and strigi enabled. I decided to delete the old database and start the indexing anew.

I have two questions:

1) what is the purpose of the advanced settings tab in the desktop search configuration window, where it says "memory usage"? i have mine set at 100MB, but after less than a day of fresh indexing a click on nepomuk icon on the panel tells me "Nepomuk store size: ~300MB". So what's the point?

2) What is the relationship between nepomuk and strigi? i see that strigi should index files by content, but then what should nepomuk on its own do? i mean, shouldn't it at least enable searching for a file by name in krunner, when strigi is disabled but nepomuk isn't?

Bonus question: i think this is a quite odd functioning, and i read of many poeple complaining on line, in forums and on launchpad, yet there wasn't a proper bug report for it. should we report that there is something that is not working right?

This is not related to the storage problem, but i'm going to ask it anyway: when you use krunner (alt+f2) to search for a file, and you find it, i noticed that when you click on it to open that file, you are actually opening some kind of a copy...certainly not the actual one, but one that has a very long codename. why is that?

Many thanks and have a good day all.

---

### Post by Kilroy2011 on 2011-02-22
Too bad no one came up with an answere on this.

I have similar problems:
My nepomuk's store size is 1.7 G out of 15981 files.

What is more, it does not find any pdf results. If anything at all.

Kilroy

---

### Post by bartman2589 on 2011-03-09
I'm having much the same problem, my strigi index file is enormous (almost 4 gigabytes!) considering that in the Nepomuk/Strigi indexing config screen I only have it set to index my:

Documents
Downloads
Music
Pictures
Public
Scripts
Sounds
Templates
Videos
Wallpaper

Folders, along with 2 folders containing music files (about 8,000 mp3's) on another drive, making the total number of files it should be indexing less than 10,000 files, but for some reason Strigi is indexing EVERY folder on my hard drive reporting that is has indexed almost 400,000 files so far, I found it indexing the /var folder the other day which caused a problem for my updates that were installing at the same time because strigi was accessing the file that the updater needed to access.  This is ridiculus, don't the KDE developers test this **** before they release it anymore!!!  First I had to put up with the fact that after 3 years the KDE Network Manager is STILL broken, IT DOESN'T SHOW ANY NETWORK CONNECTIONS WHEN YOU GO TO EDIT THE CONNECTIONS EVEN THOUGH AUTO ETH0 ALREADY EXISTS AUTOMATICALLY, then it turns out that the idiots who packaged Kubuntu/Ubuntu included the martian-modem package from an old release THAT DOESN'T WORK WITH THE NEW FILE/FOLDER STRUCTURE IN MAVERICK so my modem doesn't work and I can't get anyone to f*cking help me with the problems I'm having compiling the new modules, add to that the screwed up way that Kickoff creates desktop shortcuts (they're not even compatible with the 'align to grid' functionality or other normal desktop shortcut things because they're NOT REAL SHORTCUTS THEY'RE F*CKING MINI-WIDGETS INSTEAD),  the KDE idiots need to start focusing on fixing problems for a change instead of making things look pretty!!!!!  Pretty is all well and good IF and ONLY IF the sh*t f*cking works!!!!  And before anyone tries to tell me I've probably got a messed up install somehow I should point out that I've re-installed Kubuntu 10 f*cking times in the last god damn week, I've even tried Debian Squeeze and Kubuntu 10.04.2 all with the same problems!!!!!!  I have asked for help several times but this so called 'community' has done nothing but suggest I get different hardware instead of helping get hardware that is SUPPOSED to work with Kubuntu working!!!

---

