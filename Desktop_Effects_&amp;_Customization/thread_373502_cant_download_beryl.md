---
title: "cant download beryl"
date: 2007-03-01
forum: Desktop Effects &amp; Customization
---

### Post by dhruv_1884 on 2007-03-01
hi ,
i was able install ati drivers for my lappy, and i was proceeding to install beryl,
i added the reps to my sources list and tried to install beryl, but everytime i did, no such package was found,
anything wrong with the reps today?
can some please confirm and tell me if these are actually working

     deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main
    deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main

sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 **beryl emerald-themes beryl-settings** xorg-driver-fglrx linux-restricted-modules-`uname -r`

i cant get the ones in bold?

---

### Post by s1ptome on 2007-03-15
hi,

check the reps you  added in your sources.list ( [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) ) there are packages for edgy and feisty, but not dapper.

in fact, i'm not even sure beryl has been packaged for dapper, maybe you can find an other rep?

bye
s1ptome

---

