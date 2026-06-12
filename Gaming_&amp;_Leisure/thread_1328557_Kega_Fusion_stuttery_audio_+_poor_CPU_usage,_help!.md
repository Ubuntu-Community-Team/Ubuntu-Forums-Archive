---
title: "Kega Fusion stuttery audio + poor CPU usage, help!"
date: 2009-11-16
forum: Gaming &amp; Leisure
---

### Post by BigSilly on 2009-11-16
Using Karmic 64 bit.

Whenever I launch Kega Fusion, say Sonic the Hedgehog, the game starts but the audio is incredibly stuttery at intermittent intervals that seems to affect the frame rate in a similar fashion. Also, I notice that my CPU usage shoots up to 50%+ when it runs (I have a dual core AMD 64 X2 5200+). 

I noticed that if I mute the audio in the KF options, then the game doesn't suffer the frame rate issues (though obviously there's no sound). This suggests to me that it is the audio somehow that's causing the problem. 

Anyone have any idea what could be causing this and how to fix it? Cheers.

---

### Post by BigSilly on 2010-01-24
Just thought I'd post up to say I think I may have found a solution to this. All I did was tick the "Use Alternate Timing" box in the Options menu. This, along with "Perfect Sync" seems to have done the trick, and there is no more juddering sound and jumpy frame rates. This is on version 3.6.3 by the way.

Hope this helps someone. :)

---

### Post by BigSilly on 2010-05-03
Yet further bumpage of my own threads...

Just to point out to whomever might be interested, Kega Fusion on Lucid seems now to run with no issues with sound or frame rates at all. I'm using Lucid 64 bit, and Kega Fusion is running brilliantly on it. :)

You can now also edit the Fusion .ini to point it at libmpg123.so, and actually get sound in your Sega CD games too, which really cheered me up today! This never worked on Karmic, choose how you edited the .ini. I never did find out what was causing these issues.

Have fun!

---

### Post by msktje on 2010-06-08
Hello,

can you tell me how you installed it?
I'm on Lucid 64-bit and can't get it to run. If i do ./Fusion nothing happens and i go to an empty prompt.
I used this .deb from [https://bugs.launchpad.net/getdeb.net/+bug/537771](https://bugs.launchpad.net/getdeb.net/+bug/537771)
and i also tried the tar.gz from the original website.

Is it a dependency problem? Do i need to install the ia32-libs?

Or is it my videocard? intel gma945

---

### Post by BigSilly on 2010-06-08
I don't use a .deb or anything. I grabbed the emulator direct from the [Kega Fusion website]("http://www.eidolons-inn.net/tiki-index.php?page=Kega"), and just launch it from the Fusion executable in the folder after extraction. It doesn't install, but I made a launcher with a wee Sonic icon for my AWN dock, and that's how I use it. I don't know if it requires the 32 bit libs, but it can't hurt to have them installed. I would imagine you video card is fine, as my daughter runs Kega Fusion on her tiny Eee PC 701 with no problems at all. Hope this helps.

---

### Post by msktje on 2010-06-08
Hello i installed the ia32-libs and now it runs!

---

### Post by BigSilly on 2010-06-08
Ah cool. I wasn't sure, but there you go. :)

---

