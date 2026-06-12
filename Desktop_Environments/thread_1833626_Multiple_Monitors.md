---
title: "Multiple Monitors"
date: 2011-08-26
forum: Desktop Environments
---

### Post by fuchini on 2011-08-26
Hello, 

I have a computer with 3 Nvidia GT430 cards to connect 6 monitors. First I wanted to know if this cards are compatible under Ubuntu 10.04 or 11.04. I also wanted to know if I can write a script or something in order to open 4 different browser windows in fullscreen mode(chrome or firefox), each one in a different monitor. Any help is greatly appreciated.

Thanks.

---

### Post by realzippy on 2011-08-26
Should be possible...

---

### Post by fuchini on 2011-08-26
Thanks, finnally some hope. Do you know how to do this or any guide to accomplish this. I was looking at wmctrl but don't really know how to use it. Thanks!

---

### Post by fuchini on 2011-08-26
Would something like this work?

```

#!/bin/bash
DISPLAY=:0.1 firefox <URL>
```

---

### Post by realzippy on 2011-08-26
Since an Ubuntu install is done in a few minutes,I would suggest simply
to start.Then run all updates,then install the nvidia driver.
After a reboot you will see the status quo,then it makes sense to ask further questions.
I highly recommend to use 10.04 or 10.10 since 11.04/Unity does not
seem to handle 2 monitors pretty smart,so I guess 6 would be a mess.
Here in the forums there used to be a 6-monitor-nvidia-thread,pretty impressing,but it was a few years ago and might not be so useful anymore..
[http://ubuntuforums.org/showthread.php?t=884161](http://ubuntuforums.org/showthread.php?t=884161)

---

### Post by fuchini on 2011-08-26
Thanks, I just downloaded 10.04 and will read that thread. Which drivers should I download, the nouveau or nvidia-current (nvidia-current from ubuntu's repos or Xorg-edgers)? Thanks a lot for helping me :)

---

### Post by realzippy on 2011-08-26
Would add xswat ppa,then the driver (n-current) available in additional drivers is from xswat.(280.13)
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by fuchini on 2011-08-26
Thanks.

I'll dual-boot in case something goes wrong I can have Windoze with the Nvidia drivers. Cool thread about the 6 monitors but it's a bit too technical for me, don't know what xinerama and twinview are but I guess they are really necessary for what I'm trying to do.

Thanks for all your repplies realzippy. I'll install and post my "progress".

---

### Post by realzippy on 2011-08-26
good luck.
If you do not have empty space on your disc,you have to shrink windows
before installing ubuntu.

---

### Post by fuchini on 2011-08-26
Thanks, Just did that according to:

[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

Will now install

---

### Post by fuchini on 2011-08-26
Ok, already installed Ubuntu 64 and added the xswat repo and installed nvidia-current and it's dependencies. Do I have to restart or blacklist nouveau or something?

---

### Post by realzippy on 2011-08-26
Yes,restart.

---

### Post by fuchini on 2011-08-26
THANKS!!! I just restarted, have great resolution in the main monitor, the nvidia control panel sees my 3 cards GT430, but my other monitors won't work which I think it's normal.

---

### Post by fuchini on 2011-08-26
I added another screen in the nvidia control panel as twinview, should I add the other 4 in a separate x screen?

---

### Post by realzippy on 2011-08-26
Opened nvidia-settings ?
How much monitors does it see ?

---

### Post by fuchini on 2011-08-26
It sees all 6 monitors and already added the second one as twinview and works great. Do i add the other 4 as separate x screens or should I add all other 5 as separate x screens?

---

### Post by realzippy on 2011-08-26
> **fuchini said:**
> I added another screen in the nvidia control panel as twinview, should I add the other 4 in a separate x screen?

Maybe.Guess so.Had to google...
Check it out,now you are on your own.
If you would be my neighbour,I would come over because I think that is real interesting.
I never set up more than 2,so I can't help.
If you made some progress or collected issues/questions,I would
strongly recommend to open a new thread with "nvidia + 6 monitors + 3 graphic cards" in thread title to get most possibly replies.

---

### Post by fuchini on 2011-08-26
Thanks, I'll try with the separate x screens and then open a new thread.
Thanks a lot for your help.

---

### Post by realzippy on 2011-08-26
....envy...flight simulator must be great with this set-up     :P

---

### Post by fuchini on 2011-08-26
Yeah, I know I also envy this, but it's not even mine. They need this at work.

---

### Post by fuchini on 2011-08-26
Here's the new thread: [http://ubuntuforums.org/showthread.php?t=1833668](http://ubuntuforums.org/showthread.php?t=1833668)

Thanks a lot! :)

---

