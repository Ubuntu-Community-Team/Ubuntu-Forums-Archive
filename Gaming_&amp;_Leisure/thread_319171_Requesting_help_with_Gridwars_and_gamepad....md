---
title: "Requesting help with Gridwars and gamepad..."
date: 2006-12-15
forum: Gaming &amp; Leisure
---

### Post by shadarack on 2006-12-15
Hello, I hope I'm doing this right, this is my first post here...

I've gotten Gridwars installed and working - for those who are unfamiliar it's a clone of Geometry wars. The problem is, I cannot seem to get it to recognize my gamepad. Chances are that's my bad, I'm still learning about Ubuntu, although every day I learn a little more.

What I'm using is a playstation 2 dual shock controller, through a super dual box pro USB adapter. Unfortunately, I'm not sure if Ubuntu is even recognizing the thing.

Soooo...I guess what I need is first for someone to tell me how to confirm that Ubuntu is working with the adapter, then someone who is familiar with Geometry wars to help me figure out how to make the gamepad work with it.

Hopefully I've given whoever decides to help me enough information.

Please help? I'd hate to have to boot back into Windoze just to play Gridwars!

---

### Post by unarmedninja on 2006-12-15
I got gridwars working with my xbox controller.  Ubuntu automatically detected my controller too. you should type in dmesg or lsusb in the terminal and see if your controller shows up. if it does then you need to make a link from /dev/input/js0 to /dev/js0 since griwars looks for that path. i dont have the exact command to do that. theres also a joystick package you can install to test the controller.

Once thats working you will have to play around with the configuration in gridwars. default seetings made my controller axis messed up.

---

### Post by shadarack on 2006-12-15
Thank you so much! I ran lsusb and got confirmation that there were two devices attached to my USB - since neither description was enough to tell me what they were, I read through the spammy result of gmesg and confirmed that my adapter was plugged into joystick port zero - /dev/input/js0.

I found how to do the link you suggested [here]("http://ubuntuforums.org/showthread.php?t=312569&highlight=%2Fdev%2Finput%2Fjs0"), and after a bit of adjusting the gamepad settings in Gridwars, it works perfect!

Just one minor little thing - is it just the version of Gridwars I'm using or do all Linux versions of Gridwars not have grid settings? The windoze version of the game I was using before I escaped Bill's tyranny allowed you to pick various settings for the background grid, and I hate the default grid...too cluttered looking.

---

### Post by jakswa on 2009-01-26
First, thanks for the thread, it helped me hunt down my solution.  In my case, the XBOX 360 controller's left analog stick was behaving like the mouse (really annoying), and grid wars wouldn't pick it up. 

I read this thread, and realised that Grid Wars wasn't my problem (except for being hella-addictive), something else was getting in the way of it getting input from my XBOX 360 controller.

And then this bug report saved my day:  [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/277915](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/277915)

To quote from that page:  "
How to make it work:

$ xinput list
   See which device number the Xbox controller has...
$ xinput set-int-prop THATDEVICENUMBER 'Device Enabled' 32 0
"

That only works as long as you don't restart, but there's more permanent solutions on that page (startup scripts).

---

### Post by crazyfuturamanoob on 2009-02-03
I just can't get my old xbox controller working with gridwars. I linked it, but doesn't work:
```

$ sudo ln -s /dev/input/js0 /dev/js0

```

---

### Post by Gen2ly on 2009-06-21
Is the xpad module getting loaded?

```
lsmod | grep xpad
```

---

