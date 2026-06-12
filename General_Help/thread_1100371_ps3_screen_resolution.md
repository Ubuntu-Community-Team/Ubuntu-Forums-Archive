---
title: "ps3 screen resolution"
date: 2009-03-19
forum: General Help
---

### Post by bhuthogg on 2009-03-19
hi i have installed the 8.10 to ps3 did all the updates etc im now trying to get rid of the black borders but seem to have made it worse :(
hdmi connection

i have followed a tutorial on-line and it looks good until I reboot,

Here is what i have done so far..

```
ctrl+alt+f1

then Sudo /etc/init.d/gdm stop

then ps3-video-mode -v 131

ok my just about no border res seems to be 1205 by 685
(although i would prefer 1024 x 768 as my eyes are old :) )

so i have 
Sudo fbset -a -xres 1205 -yres 685

all is good after restarting X. 
then i edit kboot.conf to put the line in .. 

video=ps3fb:mode:131

then i did 

sudo nano -w /etc/init.d/fbset.sh

inserted the following

#!bin/sh -e
fbset -a xres 1205 -yres 685 -vxres 1205 -vyres 685

saved both

made fbset.sh executable

made a link to it in rc2.d 

reboot and i have a miniscule screeen to work with in the middle of my monitor
```

Any help GREATLY apreciated

---

