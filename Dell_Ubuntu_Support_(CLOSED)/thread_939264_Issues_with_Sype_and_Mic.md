---
title: "Issues with Sype and Mic"
date: 2008-10-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zephyrcat on 2008-10-05
I noticed that sound does not appear to be recorded in Cheese, although the webcam works. I was not sure if Cheese is supposed to record sound, though, so I installed Skype. When I tried to make a test call, though, I got the error that there was a "problem with audio playback." Any idea what the problem could be?

I am using an XPS M1530 with integrated sound.

---

### Post by zephyrcat on 2008-10-06
I gather no other M1530 owners are having this problem? If you have an M1530 and it is working, what settings are you using in Skype?

---

### Post by mbeach on 2008-10-07
I've got a studio 1735 and had the same problem with skype - for me, it seemed only to happen after the lid had been closed.  To solve the issue for me, issueing the "sudo killall pulseaudio" did the trick - no promises, but something to try.

---

### Post by zephyrcat on 2008-10-17
Thanks, but unforunately, no luck. I no longer get an error message, but when my message is played back, I don't hear anything. I also tried Audacity and Sound Recorder, which also don't work.

---

### Post by Zeedok on 2008-10-18
I'm not sure if Cheese is supposed to record sound. I only tried it briefly.

I have  a Dell m1330 and am running Skype 2.0.0.72 without any problems - I do recall some minor issues with the camera at first, but sound worked out of the box (with default settings).  This version is available in the medibuntu repositories

Which version of Skype are you using?

---

### Post by zephyrcat on 2008-10-19
I just found a solution over at the Dell forums:

[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=15286](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=15286)

---

