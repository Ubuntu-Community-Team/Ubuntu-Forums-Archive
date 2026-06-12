---
title: "Seperate wallpaper on each monitor in twinview."
date: 2009-09-09
forum: Desktop Environments
---

### Post by u-slayer on 2009-09-09
I wanted a seperate wallpaper for each monitor in my twinview setup, but the only [post I found]("http://ubuntuforums.org/showthread.php?p=4873266#post4873266") explaining how to do this was far too long and complicated. 

In short tl;dr:P so I wrote a bash script to automate the process.

```
#!/bin/bash
#Join images together for twinview

#Usage twinback [image 1] [image 2] [Left Desktop width]

src1="$1"
src2="$2"
x1=$3	#the width of the left image

img=twinview.png
temp=temp.png
res=$(xrandr | grep connected | sed 's/.*connected //;s/ .*//')
w=$(echo $res | sed 's/x.*//')

#Create Background
convert -size $res xc:wheat $temp

#First Image
composite -geometry $x1+0+0 "$src1" $temp $temp

#Second Image
x2=$(echo "$w - $x1" | bc)
composite -geometry $x2+$x1+0 "$src2" $temp $temp
mv $temp $img
```

I set up a cron job with this script so I can randomly change the background on each desktop every hour.

---

