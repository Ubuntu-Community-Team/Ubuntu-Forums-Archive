---
title: "Totem + DVD + Beryl = problems"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by jonsayer on 2007-05-19
I was trying fix some problems I have with dvd playback and came across this post:

[http://ubuntuforums.org/showthread.php?t=438721&highlight=resize+window+dvd](http://ubuntuforums.org/showthread.php?t=438721&highlight=resize+window+dvd)

I am having the same problems this guy did: I hear sound in Totem, but no picture. I only see a picture while I am resizing the window. 

The solution found in that post was that the guy was using compiz or beryl, and that was causing the problem. They told him to turn it off. One person told him to install Totem-zine, which I did and it told me I didn't have the necessary codecs anymore, which I did. 

I am using the "desktop effects" in Ubuntu 7.04, which I imagine is based on one of those two. 

How do I keep the beautiful desktop effects while still being able to watch movies?

---

### Post by Campingman on 2007-05-19
There are some fixes at the end of this thread which may help you out
[http://ubuntuforums.org/showthread.php?p=2493353&posted=1#post2493353](http://ubuntuforums.org/showthread.php?p=2493353&posted=1#post2493353)

---

### Post by Campingman on 2007-05-19
This solution posted by solicitus should work for Totem
If you load a terminal and do a;
$ gstreamer-properties
in the Video tab there is a drop down box for Plugin. I had a similar issue and selected "X Window System (No Xv)" and that solved my issue.
And for VLC this should work
In VLC if you go to settings/preferences/video/output modules click advanced options you can change the video output, I have tried X11 video output and Xvideo extension video output, both now display the video in VLC

Hope this does it for you

---

### Post by jonsayer on 2007-05-19
I tried that after I got that thread, but "Xwindow system (No Xv)" is not an option.

Should I hit "custom" and just type that in?

---

### Post by Campingman on 2007-05-19
I am not sure whyb they should be different are you seeing this output

---

### Post by jonsayer on 2007-05-19
I was looking in the wrong drop-down menu


It works now! thanks folks

---

### Post by Campingman on 2007-05-19
No problem glad you sorted it out.  
People do report poorer graphical quality with these settings though, In the end it may be better to just turn off desktop effects when you want to view a movie.

---

