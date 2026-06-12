---
title: "Sound on wrong audio output after monitor sleep - multiple monitors on DP"
date: 2019-11-26
forum: Desktop Environments
---

### Post by ixperience on 2019-11-26
I don't think this has been posted yet, but it's an interesting one. Not really a threatening bug, but just a small issue.

I have a dual-monitor setup, the screens are connected through a single display-port connection and then '*Daisy chained*' to extend it to two screens.
They are Dell screens, and I really like the fact you can use one cable to connect multiple monitors.

But here is the issue. I have connected my audio (3,5mm jack) to my 'primary' screen and selected '*HDMI / Displayport 4 - Built-in audio*' as my audio output source.
All works fine, but when the monitors go to sleep, and when I wake them up, the audio output most of the time doesn't work anymore, and I think I know why.
It looks like the monitors do not always wake up in the same sequence. This way, the audio assigned ports get confused and twisted around.

Going to the audio settings screen and select the other output card '*HDMI / Displayport 3 - Built-in audio*' does the trick, and sometimes I need to choose the other way around of course.

I can imagine this isn't a very easy fix, maybe looking at a hardware number (like screen identification) would be a way to determine the correct output?

Well, this is my small dime for now, the rest of the Ubuntu system is working fine most of the time. The only issues I DO have are all graphics related (like crashing on a lot of animations, but that's not often and not a real big issue for me personally).
I am very grateful that you guys create and maintain this platform !

---

### Post by ixperience on 2020-01-31
As no one probably is interested in this issue, I'll add some extra info;

On starting up, sometimes the screen stays blank or go auto off because they're not receiving a signal.
To overcome this, just shut down both monitors, and then turn them on ONE BY ONE. 
I looks like in this particular setup, Ubuntu doesn't find the monitors when they are both on one cable and started simultaneously.

This issue is the underlying problem for the sound also I think.

---

