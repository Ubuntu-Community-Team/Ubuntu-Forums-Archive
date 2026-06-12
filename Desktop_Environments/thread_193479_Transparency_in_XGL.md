---
title: "Transparency in XGL"
date: 2006-06-10
forum: Desktop Environments
---

### Post by ss0007 on 2006-06-10
Hi , 
I just installed xgl from "XGL Install and General Tips For Gnome and Nvidia" post and  evrything is fine, but the transparency wont work. I tried ctrl+scroll up/down . It seems i need to tweak some settings?

thx

---

### Post by Anduu on 2006-06-10
On my XGL setup transparency is controlled by Alt+scrollwheel...

---

### Post by ss0007 on 2006-06-10
hey thx for ur reply ,
but alt+scroll doesnt work !!! nor ctrl+scroll , ctrl+alt+scroll 

here's my compiz parameters, to start xgl

gnome-window-decorator & compiz --replace gconf miniwin decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &

are the above parameters set right for transparency effects ? 
now wht can i try ?

---

### Post by angkor on 2006-06-10
You're missing the 'state' plugin I think.

You don't need to start compiz with all the plugins listed anymore. Just gconf and decoration I think. 

The rest of the plugins you can enable in gconf-editor (or install 'gset-compiz') in the order explained in this thread:

[http://www.compiz.net/viewtopic.php?id=968](http://www.compiz.net/viewtopic.php?id=968)

---

### Post by ss0007 on 2006-06-10
hey thanks again for the reply,

the problem still persists !!

i have edited the .sh file to start the xgl to the following 

#!/bin/bash
gnome-window-decorator & compiz --replace gconf miniwin decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water bs dock state widget &

i tried ctrl+scroll, alt+scroll , but the windows like nautilus zooms in and zooms out  (also ctrl+alt+scroll doesnt work)

any suggestions pls ...

---

### Post by 23meg on 2006-06-10
Follow this guide to enable Quinn's repo and get more up to date XGL and compiz packages:

[http://www.compiz.net/viewtopic.php?id=652](http://www.compiz.net/viewtopic.php?id=652)

Warning: these versions will likely be less stable and if you upgrade all packages with this repo enabled, many libraries on your system will be upgraded to newer versions which can cause unstability and conflicts.

---

### Post by ss0007 on 2006-06-10
hey guy s,
more problems ,

i tried to reinstall by the previous post, now compiz doesnt start !!!
it gives the following error :

compiz.real: No GLXFBConfig for default depth, this isn't going to work.
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0

my defualt depth is 24 

pls help !!!

---

### Post by tronica on 2006-06-10
i would use this repo on here:
[http://xgl.compiz.info/](http://xgl.compiz.info/)

and then go to your guide and reinstall all the stuff over.

---

### Post by ss0007 on 2006-06-10
hey , 
it 's working now,  feels grt and awesome .
just did apt-get dist-upgrade 
the newly updated libmesa is needed for compiz to work .

wow , what a way to feel the ubuntu ,
xgl rocks !!!

---

### Post by someusernoob on 2006-06-10
I updated my compiz with that beerorkid repository, got all the nice transparacy etc. But what i'm missing now are the wobbly menu's, they used to wobble when i open e.g. Applications, Firefox bookmarks etc., now thats just normal. I took a look in gconf-editor but cant seem to find the right setting to enable it, anyone an idea?

Nevermind, found it. Install gset-compiz and do:
gset-compiz > plugins > wobbly > enable map shiver effect > and play around with Friction and Spring K under Map in the upperright corner of that window to change the strenght of the effect.

---

