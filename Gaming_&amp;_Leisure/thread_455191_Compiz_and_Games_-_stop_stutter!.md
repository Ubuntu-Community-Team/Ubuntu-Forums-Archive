---
title: "Compiz and Games - stop stutter!"
date: 2007-05-26
forum: Gaming &amp; Leisure
---

### Post by viciouslime on 2007-05-26
I noticed that with desktop effects enabled, my framerates in games such as nexuiz would hardly fall at all, however, there was a definite stuttering effect. Turn compiz off and the stutter goes away...

I've finally found a solution so if anyone else has the problem do as follows:

Press alt+f2 and enter "gconf-editor" then press run or the enter key
Navigate to apps/compiz/general/screen0/options
Tick the box next to they key "unredirect_fullscreen_windows"
Et voilà

Problem solved. :D

Using Beryl I have never had this problem, so I am guessing Beryl does this, or something like it by default.

---

### Post by Feba on 2007-05-26
I hadn't noticed anything I didn't blame on my computer, but i'll see if this helps!

---

### Post by anotherdisciple on 2008-07-28
hmmm... I'm going to try this...

---

### Post by tjwoosta on 2008-07-28
```

Press alt+f2 and enter "gconf-editor" then press run or the enter key
Navigate to apps/compiz/general/screen0/options
Tick the box next to they key "unredirect_fullscreen_windows"
Et voilà

```

strange..
mine was already ticked

---

### Post by viciouslime on 2008-07-29
This is a very old post and I' afraid it is no longer relevant. At the time, beryl shipped with some sort of module that compiz did not, but now compiz incorporates this by default. I can't remember what it's called, but if you're using the leatest version of ubuntu (8.04 hardy heron) this tip is no longer relevant.

Sorry...

---

### Post by tjwoosta on 2008-07-29
ha, yea i didnt even notice the date wow..

may 2007

talk about revival



but anyway if anybodys reading this and wondering the easiest way i know of to make compiz stop affecting games is to just temporarily turn it off

(press alt-f2 to run metacity --replace , then after your done just press alt-f2 and run compiz --replace to turn it back on)

or you could even write a simple script to do it for you

---

### Post by BigSilly on 2008-07-29
Funny I should spot this thread. I don't enable Compiz, since it used to cause me some problems when playing DVD's and some games. I decided to give it a try again today, and sad to report it still causes some issues.

I started up SDLMame with it enabled, and straight away there's a problem with it. Usually SDLMame goes to fullscreen just fine, but with Compiz enabled it jumps between full and windowed. Can anyone explain why this is, and what I can do to fix it. I'd really like to have Compiz permanently on. I'm using an NVidia 6200 AGP 256Mb card, with proprietary drivers enabled.

Thanks.

---

### Post by eragon100 on 2008-07-29
Unfortenately, nothing, AFAIK. Just turn it of when you start playing, and then enable it again. Compiz fusion icon is a very handy program for dis/enabling it with a single mouse click :wink:

---

