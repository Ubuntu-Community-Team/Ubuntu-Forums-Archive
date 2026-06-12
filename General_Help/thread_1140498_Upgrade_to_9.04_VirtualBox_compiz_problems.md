---
title: "Upgrade to 9.04 VirtualBox compiz problems"
date: 2009-04-27
forum: General Help
---

### Post by ajhtiredwolf on 2009-04-27
If you upgraded or just installed 9.04 and are using virtualbox/compiz and suddenly suffer from all your Guest machines being transparent windows here is what you can do.

create a blank text file on your desktop named compizfix

open up a terminal
```
cd /home/user/Desktop
sudo chmod a+x compizfix
```

now open up compizfix and copy/paste this into it
```

#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1 
VBoxManage startvm "vista"

```
replace "vista" with the name of the guest machine

then in a terminal 
```

cd /home/user/Desktop/
./compizfix

```

if it works you can add it to youur local bin
```
sudo cp compizfix /usr/local/bin/nameofvirtualmachine

```
then right click on your gnome menu
edit menus
place a new item in the category you wish
name: nameofvirtualmachine
command: nameofvirtualmachine

Sidenote: you can find the name of the virtual machine by openning up virtualbox  clicking on the guest machine and it will be on the left under general

(This was tested under Ubuntu 9.04 64-bit on vista nd XP with and without guest additions installed)

---

