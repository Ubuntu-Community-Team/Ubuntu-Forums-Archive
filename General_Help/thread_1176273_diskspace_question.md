---
title: "diskspace question"
date: 2009-06-02
forum: General Help
---

### Post by tomski on 2009-06-02
Hi there,

since upgrading my 2 pc's to jaunty my second pc (LAN media server) seems to have lost diskspace

with my previous install (interpid)i maintained a constant 1GB(+-20mb) free space in / (total partition size = 5GB)this included the rotated log files etc as well as 1200ish installed apps including webmin/apache/mysql/ntop/cacti/mediatomb

all was fine & i had ample freespace to cope with any misbehaving app which may create huge log files whilst having a problem.

since upgrading to jaunty i can only maintain a constant total 529Mb freespace in /
yes i have removed/cleaned the apt cache, removed ALL unnessecary apps such as games/office apps/tomboy,also i changed the rotation of log files BACK to 4 day&#8217;s!!!!!! as the upgrade changed them to 10 or 7 days

i have used the 2 cleaner app&#8217;s 'trash collector' & 'computer janitor' which removed ALL unneeded configs from updates,orphaned libs & files, unused lock/tmp files and any other chuff that was no longer needed but all that these managed to glean was a messley 50MB between them!!

have any of you readers out there noticed a jump in the installed system footprint?

my /usr/lib folder is the largest on my system currently at 126Mb

also is it a bad idea to use 'disk patitioning' to resize an IN USE/MOUNTED partition to create a /var partition?

---

### Post by MichaelSammels on 2009-06-02
It CAN be a bad idea, since that section of the disk may be getting used. I recommend you boot from an Ubuntu LiveCD/DVD/USB, run GParted to do it from there, when the drive is not mounted, unless you can safely unmount this from within Ubuntu.

---

### Post by tomski on 2009-06-02
thnx Michael
i have worked out how to copy contents of folders whilst maintaining permissions but was hoping to not reboot as it is a headless server & lives in the attic!
but my main head banger is the drop in contigous free space!!!
do you think this is a footprint increase or something elase

---

