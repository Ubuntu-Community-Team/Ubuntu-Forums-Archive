---
title: "Problem with Record My Desktop"
date: 2012-04-16
forum: Desktop Environments
---

### Post by forsubhi on 2012-04-16
I have small problem with  Record My Desktop  , After I recorded what I want , I don't know where the program save my files , please help me 
this is image of the program 

[IMG]http://img7.imagebanana.com/img/9p9yecr0/Selection_047.png[/IMG]

---

### Post by samigina on 2012-04-16
Do you see that little button beside the "Quit" one? Click there and choose you file name and destination.

---

### Post by forsubhi on 2012-04-16
I had seen  it before  , I am not blind .. man :lolflag:   ,  but the problem was that you have to click save as and choose you file name and destination before recording , not after it .

thanks . :popcorn:

---

### Post by 23dornot23d on 2012-04-16
It usually puts the file out.ogv in the directory its started from ....

Mine tend to go in the /home ..... directory .....

find  -name out

```

[root@keith-aspire-7730zg keith2]# recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:720
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:720
Your window manager appears to be KWin


Detected compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device hw:0,0
Playback frequency 22050Hz is not available...
Using 44100Hz instead.
Recording on device hw:0,0 is set to:
2 channels at 44100Hz
Capturing!

*********************************************

Cached 24 MB, from 847 MB that were received.
Average cache compression ratio: 97.1 %

*********************************************
Saved 241 frames in a total of 241 requests
Shutting down.....
STATE:ENCODING
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
Output file: out.ogv
[100%] 
Encoding finished!
Wait a moment please...
   
Done.
Written 5048400 bytes
(5046916 of which were video data and 1484 audio data)

Cleanning up cache...
Done!!!
Goodbye!

[root@keith-aspire-7730zg keith2]#[COLOR=Red] **find ~/ -name out.ogv**[/COLOR]

[root@keith-aspire-7730zg keith2]# [COLOR=Red]**ls**[/COLOR]
Desktop  Documents  Downloads  Music  [COLOR=Blue]**out.ogv**[/COLOR]  Pictures  Videos

[root@keith-aspire-7730zg keith2]#[COLOR=Red]** find -name out.ogv**[/COLOR]
./out.ogv
[root@keith-aspire-7730zg keith2]# 


```

---

### Post by MartyBuntu on 2012-04-16
I think it defaults to the home directory for saving. Have a look there (It's been about a year since I've used this).

---

### Post by forsubhi on 2012-04-18
thanks

---

