---
title: "SUCCESS syncing Treo 500 with Evolution in Ubuntu 8.10"
date: 2009-01-10
forum: General Help
---

### Post by adair on 2009-01-10
Perhaps no big deal to some, but it's been a tortuous road here. FWIW what worked for me was to follow the instructions set out here: [http://ubuntuforums.org/showpost.php?p=6258719&postcount=6/](http://ubuntuforums.org/showpost.php?p=6258719&postcount=6/) 

Note:
1. that 'librra0-tools' is replaced by 'librra-tools' in Intrepid,

2. Network-manager seems to have no difficulties coping with the link---I was able to ignore this part of the 'HowTo',

3. nor did I need to touch the synce .config file.

Then to use gnome-kpm and Multisync0.90 (not Kitchensync which tried but seemed to have problems---may have been me).

AND most importantly to TURN OFF 'Advanced networking' in 'Settings' > 'Connections' > 'USB to PC' on the Treo (many 'HowTos' say to turn it 'On').

Once you have 'synce-sync-engine' running from the command line (you can then set it to automatically run at log-in through 'Admin' > 'Sessions'), start 'gnome-kpm', plug in the Treo, which should appear in g-kpm, then start Multisync (as described elsewhere you will need to create a 'partnership').

So far there have been none of the horrendous multiple pile ups of records which I used to get with Evolution syncing with the Palm OS. There have been a couple of 'failed' syncs but with no harm done, otherwise it's been flawless.

Cheers, credit, and thanks to all those who work on the relevant packages.

---

