---
title: "dual monitor issues"
date: 2010-11-28
forum: Desktop Environments
---

### Post by mdgtptrl on 2010-11-28
Let me preface this with: I haven't used ubuntu in almost 2 years, but i can still use a terminal pretty well :) I remember dealing with all this stuff two years ago when I was setting up on my laptop, but it's been a while...

I'm on a pretty fresh install of 10.10 and having some issues with my dual monitor setup. The attached image illustrates the problems pretty well. 

First of all, the monitors are different sizes, so there's some "dead space" in the top left. That's where ubuntu is putting new files and things. In addition, the pointer can get lost up there. Is there a fix for either of those?

Second, ubuntu sees the smaller monitor as the primary. How can I change that?

Third, and the most tricky i think, is all the stuff happening on the right-hand side. The background won't render, but I can drag windows over there. When I do, they sort of leave a trail, but the window still works fine. ...Of course, as I was typing this paragraph, I went to verify my next sentence ("it doesn't really matter what the resolution of the second monitor is, this happens anyway"), but now it's not happening -- at any resolution. I was playing with the fglrx driver but I couldn't get it to install properly, so I think i'm running on the ATI. How can I tell? Does this sound/look like a driver issue?

Finally, sort of as a follow-up to the last issue, I don't think the drivers are working properly. The CPU seems to be doing a whole lot of graphics processing (changing the desktop background takes 10 seconds, and CPU usage shoots up to 100%). How can I get the video card (an ATI Radeon 4850) drivers set up properly?

Thanks, I'm excited to get this thing set up!

---

### Post by deano_ferrari on 2010-11-29
What does the following command report?

```
xrandr
```

Attach the output of /var/log/Xorg.0.log to your reply. That may help others get a handle on your problem.

---

### Post by mdgtptrl on 2010-11-29
here's what xrandr spits out:
```
Screen 0: minimum 320 x 200, current 2704 x 1050, maximum 4096 x 4096
VGA-0 connected 1024x768+0+282 (normal left inverted right x axis y axis) 304mm 
x 228mm
   1024x768       60.0*+   75.1     70.1  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1680x1050+1024+0 (normal left inverted right x axis y axis) 433m
m x 270mm
   1680x1050      59.9*+
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0     70.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  

```

Terminal responds to /var/log/Xorg.0.log with "command not found"

---

### Post by deano_ferrari on 2010-11-30
> Terminal responds to /var/log/Xorg.0.log with "command not found"

That's because it's not a command. To view the contents of that file

```
cat /var/log/Xorg.0.log
```

Attaching this file (or uploading the contents to pastebin, and posting the link to it here), may help us determine which driver is in use (I'm assuming radeon driver) and what issues may be occurring.

---

### Post by deano_ferrari on 2010-11-30
>  but now it's not happening -- at any resolution. I was playing with the fglrx driver but I couldn't get it to install properly

What errors did you get? Maybe this guide will help:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by mdgtptrl on 2010-11-30
Here's the file: [http://pastebin.com/jQuCw3hU](http://pastebin.com/jQuCw3hU)

I also discovered that xorg.conf is empty, which i believe it should not be?

I was following that guide. It's set up for ubuntu 9, and doesn't seem to work for 10, but i'll keep working on it. I wasn't so much getting errors as I was crashing the whole system. The first problem i'm running into is that System->Administration->Additional Drivers won't show fglrx.What do I do about that?

---

