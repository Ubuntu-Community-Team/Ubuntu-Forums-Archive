---
title: "cant seem to get fix apache2"
date: 2009-01-18
forum: Desktop Environments
---

### Post by bigrockcrasher on 2009-01-18
i installed apache2 a while a go and got it working fine. over the months i added in php and mysql too. but then i screw up somewhere  I decided to reinstall everything. well i removed php, mysql and apache2. then i install everything. when i looked at [http://localhost](http://localhost) through Firefox it wants me to download a file. i looked on the forum some people had similar problem and all of them did not accomplish anything. so i opened up the file that it wants to download and it was my homepage file. so i backed up my website and put it somewhere else and deleted the folder /var/www. then i reinstalled everything. when i look at [http://localhost](http://localhost) again it asked me to download a file again and it is still old my homepage. does anyone have a solution. i do not want to wipe the hard drive out and install ubuntu again(some of the forums said this was a solution) because i have a feeling when i look at [http://localhost](http://localhost) i am going to see my old homepage file again.

---

### Post by lncoll on 2009-01-18
Not sure, but is possible than your browser has your old homepage in cache.
Have you tried to clean the cache of your browser and try again?

In firefox you can do it by clicking Edit -> preferences -> advanced -> net and click in the clean now button. My Firefox is in Spanish, so menus can be different.

---

### Post by yeats on 2009-01-18
Make sure the www-data user has read access to the php files.  Sometimes this is a permissions problem somewhere down the line.  I would ls -l every directory until I assured myself that this was not the case, then move on to other types of troubleshooting.

Good luck!

---

