---
title: "dell monitor is stuck in suspend..i think??"
date: 2009-10-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by topsykretts187 on 2009-10-24
hey guys..this would be my first time posting here since this is my first time having a problem. i have a dell inspiron 5160 and i just recently re-nstalled ubuntu on it.just this morning i decided to clean the heatsink of dust  and dirt.before i took apart my laptop,i left it on to completely drain the battery..when i got back the battery was drained and i proceded to take apart and clean the heat sink..when i put it back together again and turn on the laptop..it turns on all right..the fan spins and the light from the optical drive and hard drive blinks but the screen stays black..when i turn off the laptop and boot it agan..the same thing happens again..it turns on,the laights turn on but the monitor is black.i dont think its my monitor..i think the problem happend when i let the battery drain..since i just re-installed ubuntu on my laptop i didnt get a chance to change the power save settings(which i normally change to shut down when battery is less than 10%-or something like that)...so when the battery drained it went on suspend/standy/sleep/hibernate(or whatever its default setting is)and now i cant get out of it...can anybody help me get out of suspend/standby/sleep/hibernate setting?

---

### Post by cyqotiq on 2009-10-24
I see what you're thinking, in terms of the computer being stuck in a power-saving state.  The fact that it stays in this state even after a hard reset tells me it's most likely in a hibernation state, rather than a sleep mode.

Before you do anything else, I would try to test that monitor on another computer just to rule out the possibility that it's the monitor.  You didn't mention doing anything with the monitor, so I'm going to guess that it's probably fine.

You seem informed enough to know about error beep codes.  Is the computer making any sounds during what should be the boot sequence?  I'm also guessing that there aren't any... you would have probably mentioned them if there were.  To be honest, I haven't heard a error beep code in many many years.  I'm not even sure if they still use them. ::shrug::

Now that all of that has been ruled out, can you boot from a Live CD?  The idea is to try to find some alternative method to boot your computer, just for the sake of being able to show that everything functions properly - current installation not withstanding.

---

### Post by topsykretts187 on 2009-10-25
-hey cyqotiq.sorry i forgot to mention that i did try to attach the laptop to another monitor..the monitor was still black...so i guess its not my laptop monitor thats the problem.

-nope no error beep haha

-i just tried the livecd..i turned the laptop on..put the cd in..turned the laptop off...turn the laptop on again and the screen was still blank

a friend suggested to take out the video card and put it back in??would anyone agree to that??i dont really see the connection between the video card and my laptop being stuck on power saving state.

---

### Post by topsykretts187 on 2009-10-25
tried taking out the video card and putting it back in..still doesnt work

---

### Post by cyqotiq on 2009-10-25
Can you try booting with a live cd and reviewing your system logs to see if there's any indication about what might be happening?  I'm thinking that if it's stuck in hibernation, Grub should at least be showing up.

EDIT [25 OCT 2009 1832 GMT]
Sorry - Just went back and re-read your post.  It sounds like the live CD can't boot either.  Is this correct?

---

### Post by cyqotiq on 2009-10-25
I've done some looking around, and I've found that this problem might have occurred in [another post]("http://ubuntuforums.org/showthread.php?t=578586"), but with no resolution.  I've also found a reference to something similar over on [launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/361852").  Glancing through, I didn't see anything that "jumped out" at me, but it might be worth a shot looking over that thread.

Out of curiosity, does anything show up on your monitor at all?  BIOS info/splash, POST, anything?  Or is it just blank the whole time?

---

