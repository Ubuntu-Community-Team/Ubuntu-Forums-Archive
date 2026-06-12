---
title: "Xplanet in KDE4 how to..."
date: 2009-06-09
forum: Desktop Environments
---

### Post by OldGaf on 2009-06-09
Hi all,

Well... I know it is not the newest application, but I still love xplanet. Last night I got it working on my KDE4.

I created a folder in my home dir called xplanet-img.

I wrote a script with the following line in it:
> #/bin/bash

xplanet -window -geometry 1680x1050 --num_times 1 --lon 300 --lat 15 --radius 40 --range 10 --output ~/xplanet-img/pic.jpg && mv ~/xplanet-img/pic.jpg ~/xplanet-img/xplanet.jpg

This will gen a new image and replace the old one with it.

Then I call the script from cron every 5 min.

Next.... in my desktop settings I choose slide show for the background and point to the xplanet-img folder..... done.

---

### Post by OldGaf on 2009-06-09
More fun can be had by using the picture/slide show Plasmoid in the same way. 
You can have various planets on different parts of your desktop... or add some variables to the script to change which planet is displayed randomly...

Will be playing with this some more when I get home from work today....

---

### Post by OldGaf on 2009-06-09
There is probably a cleaner way to do this.... I do not claim to be a great scripter,  but just for fun  you can make it rotate with every update.......


> #/bin/sh

num=`cat ~/Settings/xplanet/num.txt`


if [ $num -le 10 ]; then
    lon=360
else
   lon=$(($num-10))
fi


echo $lon > ~/Settings/xplanet/num.txt

xplanet -geometry 1680x1050 --num_times 1 --lon $lon --lat 15 --radius 40 --range 10 --output ~/Settings/xplanet/img/pic.jpg && mv ~/Settings/xplanet/img/pic.jpg ~/Settings/xplanet/img/xplanet.jpg

---

