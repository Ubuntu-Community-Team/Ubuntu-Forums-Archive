---
title: "Floating windows in compiz fusion"
date: 2007-12-18
forum: Desktop Effects &amp; Customization
---

### Post by dan1_m1 on 2007-12-18
Hi 
I installed Ubuntu and Copmiz fusion on my Pc but I could not enable the 3d effect for windows as the newest Compiz fusion doesn't have this feature yet (I believe is being re-written) but you can install the 3d plug-in to enable this feature. 
Therefore someone gave me the following script which installs some updates and dependencies needed to install the 3d windows effect:

  
```

#!/bin/bash
sudo apt-get install compiz-bcop compiz-dev
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O '3d.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
tar -xvvzf '3d.tar.gz'
cd '3d'
make
sudo make install

```
This script suppose to work. I seen it in many discussions on this subject

Now everything worked fine I downloaded and installed all the files needed for the plugin, I even downloaded the 3d.tar.gz but when i type the command

tar -xvvzf '3d.tar.gz' 

I receive the following error:

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed form previous errors

and nothing happens any more
Please help me with some ideas
Thanks :) 
O yes one more thing as I&#8217;m very new in Linux (2 weeks) I don&#8217;t exactly understand what this line means 
#!/bin/bash as I type it nothing happens 
Thanks again guys :)
And may the force be with you :biggrin:

---

### Post by Znort_Ubern00b on 2007-12-18
[Try this link]("http://ubuntuforums.org/showthread.php?t=620000&highlight=autumn")

it tells you how to install all the plugins easily...it did work in feisty and now have 3d specs to view it...

---

### Post by dan1_m1 on 2007-12-18
Thank You I'll try that as soon as I'll be home 
But I still like to know why I receive that error when I try to unpack the tar file. So if anyone happens to knows something about that pleas share the information so I can expand my knowledge on Linux. 
Thank You guys :)

---

### Post by dan1_m1 on 2007-12-19
I worked perfectly Thank you very much

---

