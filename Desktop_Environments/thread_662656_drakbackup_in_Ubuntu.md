---
title: "drakbackup in Ubuntu ?"
date: 2008-01-09
forum: Desktop Environments
---

### Post by rafalr on 2008-01-09
Hello,

This is related to (already closed, and a very short) thread accessible here [http://ubuntuforums.org/showthread.php?t=212569](http://ubuntuforums.org/showthread.php?t=212569)

I have checked myself, to some extent, almost all backup-related stuff available at repos for 7.04 (around 5-7 of them), and another 5-7 not available in repos. Of which PyBackpack seems to be the most handy, however, can not find any debian based stuff that:
- works via simple GUI to set source/target
- allows to flexibly and easily control in- & exclusions and filters
- can also output a script (describing all in/exclusions) that could be put in cron, or, better - allows to edit / insert cron entries for backup.
:confused:
Inevitable it always comes back to Mandriva's drakbackup that can do all of the above in a friendy way. Has anyone "ported" that to a debian package ? 

I was considering to alien this rpm package into a decent deb on my own, but I see there is quite a lot dependencies on the way which seem to be very specific to Mandriva:

-------------------------------------------------------------
drakbackup-0.6-1mdv2007.1.noarch.rpm
Requires (plus many more)
drakxtools => 10.4.89-1mdv2007.0

then 

drakxtools-10.4.239-1mdv2008.0.i586.rpm > 10.4.89-1mdv2007.0
Requires (plus many more)
drakxtools-curses = 10.4.239-1mdv2008.0	
mandriva-doc-common >= 9.2-5mdk	
drakx-net	
drakconf-icons	

then

drakxtools-curses = 10.4.239-1mdv2008.0
Requires (plus many more)
urpmi >= 4.8.23	
drakxtools-backend = 10.4.239-1mdv2008.0	
drakx-net-text	

then

mandrake-doc-common-10.0-3mdk.noarch.rpm
seems to be OK without Mandriva specific dependencies

but

drakx-net	
Requires ... ?

drakconf-icons
Requires ... ?

urpmi >= 4.8.23
Requires ?

drakxtools-backend = 10.4.239-1mdv2008.0	
Requires ?

drakx-net-text
Requires ?
-------------------------------

I used to sucessfully install several rpm packages with help of alien, but those were never so complex as far as multi-layered dependencies. 

In case I had really plenty of spare time and decided to go for it:
- should I alien all the rpms supplying dependencies as whole packages (which surely will contain lots of rubbish not needed by Ubuntu, or worse, conflicting with existing Ubuntu supplied libraries), or
- try to extract the individual libraries/files required by dependencies (which surely will much exceed my expertise level and time resources).

Any ideas how to approach it in a simple way ?

EDIT
Actually there a *simple* way: install sbackup from repos. 

Apparently, I did not spend sufficient time with that piece, and only last evening discovered that actually you can add hidden files (like /home/user/.hidden.one) by right clicking on any folder, in the panel you use to pick the catalogues to be backed up. I was missing that functionality much, and no manual contains that hint - I learned it only by mistake.

rafal

---

