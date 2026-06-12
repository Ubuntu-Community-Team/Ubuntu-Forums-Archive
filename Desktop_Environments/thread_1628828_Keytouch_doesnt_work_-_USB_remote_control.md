---
title: "Keytouch doesnt work - USB remote control"
date: 2010-11-23
forum: Desktop Environments
---

### Post by seatec on 2010-11-23
Hi!  I'm running a Kubuntu 10.10 and recently got new speakers. They are attached to the computer via USB(!), for both sound and signaling. The speakers came with a remote control that can do the usual things such as Volume in-/decrease, mute, next/prev track and so on. Problem is not all of the keys work.  Without any special sort of driver or tool, three keys worked right out of the box: Mute, Volume Up, Volume Down. KDE displays the actions just nicely, as if I hit the buttons on my multimedia keyboard.   I tried configuring the remaining buttons using the keytouch tool. Keytouch does receive all the signals, including the ones with the missing funtionality, and I tried assigning actions to these buttons, but without luck. Also, if I use keytouch to try and get the mute button to do volume increase, that won't work either. I can't assign mute to some other action either(not that I'd want to. Just a test).   So any ideas where I can assign USB scancode to action? Or how to get keytouch to do its job?  Thanks!

---

### Post by seatec on 2010-11-23
Turned out KDE had the keys mapped, just didn't know what to do with them. I used KHotKeys to create a new group, and in there assigned actions for my media player for the three keys.
  Further reading on the topic: [http://ale.freeshell.org/articles/hotkeys/hotkeys.html](http://ale.freeshell.org/articles/hotkeys/hotkeys.html)

---

### Post by seatec on 2010-11-23
For the record since I may not be the only one with these speakers: They are Bowers & Wilkins MM-1

---

