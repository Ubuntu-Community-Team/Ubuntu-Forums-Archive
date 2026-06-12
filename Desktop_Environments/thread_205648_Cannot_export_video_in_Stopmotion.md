---
title: "Cannot export video in Stopmotion"
date: 2006-06-28
forum: Desktop Environments
---

### Post by 4ebees on 2006-06-28
Hi All,

I'm using 5.10 with a KDE desktop. 

I cannot export video. I have used my webcam to take a series of images, but cannot export it to video. Nor can I export to video if I use jpegs taken using my video still camera.

In the video export option I originally (was the default) had:

mencoder mf://$IMAGEPATH/*.jpg -mf w=640:h=480:fps=12:type=jpg -ovc lavc -lavcopts vcodec=mpeg1video -oac copy -o $VIDEOFILE

So I changed it to:

mencoder -ovc lavc -lavcopts vcodec=msmpeg4v2:vpass=1:$opt -mf type=jpg:fps=8 -o $VIDEOFILE mf://$IMAGEPATH/*.jpg

I also tried: 

ffmpeg -r 10 -b 1800 -i $IMAGEPATH/%06d.jpg $VIDEOFILE (replacing the above and changing nothing else)

(per instructions found at: [http://ubuntuforums.org/showthread.php?t=21721&highlight=stopmotion](http://ubuntuforums.org/showthread.php?t=21721&highlight=stopmotion))

None of these options have an 'stop encoder' command (I'm not sure what to put there and there was nothing in there by default)

I appear to have all the necessary related apps and my webcam produces  a good image. 

I've had a look at the Stopmotion home page but am afraid I couldn't locate a mailing list.

Any help is most appreciated - the program looks great by the way.

---

