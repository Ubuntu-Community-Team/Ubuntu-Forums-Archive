---
title: "Videos &amp; Screensaver"
date: 2012-03-02
forum: Desktop Environments
---

### Post by bman on 2012-03-02
I am using XScreensaver & SMplayer.

When I am full screen, my screensaver comes on at the set time. I know you can do this in Windows, how do I tell it not to when a full screen application is running?

---

### Post by papibe on 2012-03-02
Hi bman.

I had the same problem some time ago. Take a look at his [thread]("http://ubuntuforums.org/showthread.php?t=1148339&highlight=smplayer"). Specially post #9 and #10.

Hope it helps.
Regards.

---

### Post by bman on 2012-03-02
So I put that code into my SMplayer config file and thats it?

At the end of the file, where? Also, when they are talking about disabling, just while the video is running correct?

---

### Post by papibe on 2012-03-02
The command
```
xscreensaver-command -deactivate
```
does not 'deactivate' your screen saver (regardless of the literal meaning). What it does is to simulate user activity (like mouse movement or a keyboard stroke).

I would try it first without using the ending '&'. If that doesn't work try it as post #10 of the linked thread.

Regards.

---

### Post by bman on 2012-03-03
Do I need to restart for this to work? If not, it's not working.

---

### Post by papibe on 2012-03-03
No, only SMplayer itself.

Could you confirm that edited your ~/.mplayer/config and added the line:
```
heartbeat-cmd="xscreensaver-command -deactivate"
```
Regards.

---

### Post by bman on 2012-03-03
My file has a # before it, should that be there?

---

### Post by papibe on 2012-03-03
'#' is used for comments, so it depends:

- If it's on the previous line, it doesn't matter.
- If your line starts with that, you have to remove it in order to take effect.

For instance, this is OK.
```
#
heartbeat-cmd="xscreensaver-command -deactivate"
```
and this is not:
```
#heartbeat-cmd="xscreensaver-command -deactivate"
```

Regards.

---

### Post by bman on 2012-03-03
Alright, so I removed the # and it worked, I think.

It went to a black screen for a second and went away. Which is ok...

I just had the video open not full screen, and it did the same thing. Which is not ok, I only want it to do it in Full screen..

*edit I added the & at the end, and much better, no black or anything. Not sure if its still doing it without it being full screen.

---

### Post by bman on 2012-03-05
Sorry, bump?

---

### Post by papibe on 2012-03-05
At the time of the thread I linked, there was a bug in the SMplayer's internal option to disable the screensaver, thus all that trickery.

I inclined to think that the option got fixed. Have tried it? It is in:
```
Opions -> Preferences -> General -> Video -> Disable screensaver
```
Which if fixed, it should effectively disable the screensaver while playing the video.

Let us know how it goes.
Regards.

---

### Post by bman on 2012-03-05
Does it update by itself in the background? Cause it's working now.

Weird.

---

### Post by bman on 2012-03-06
It works kinda. Seems it works, but my screensaver does not come on at all. Or it works during video and everything.

That config that I needed to change, does that still have to be changed?

---

### Post by papibe on 2012-03-06
It may be interesting to try with the line on the config file. Comment the line (instead of deleting it) by putting back the '#' at the beginning of the line.

Tell us how it goes.
Regards.

---

