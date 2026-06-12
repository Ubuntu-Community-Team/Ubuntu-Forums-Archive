---
title: "Getting really low FPS on a Nvidia Graphic Card!"
date: 2009-04-30
forum: General Help
---

### Post by tonybeccar on 2009-04-30
Hi everyone!

My problem is that i'm getting 60fps with an Nvidia 6800 XE 256mb graphic card. It's really really low, and i can notice it on things like, moving windows, they move in a choppy way, effects, everything i think.

I googled around and people use to get like 6000 fps with better Nvidia cards, i don't intend to reach that number, but I would like to get a little higher just to run Ubuntu smoothly.

I'm running Ubuntu 9.04 64 bits. I have the latest Nvidia restricted drivers installed (version 180). 

I noticed that Ubuntu runs smoother when compiz is disabled. But not as good as I want.

I googled and also found that what's making the windows run choppy may be a sync problem of the display. I think a have everything set up correctly, I have a native resolution of 1680x1050 and with a 60hz of refresh rate.

So, I'd appreciate any kind of help! Thank you and good bye!

---

### Post by tonybeccar on 2009-05-01
Please, anyone?

---

### Post by sgtbug on 2009-05-01
i am assuming u mean the fps achieved in glxgears..

Do this:

System > Administration > OpenGL Settings > Uncheck the Sync to V-Blank checkbox..

Worked for me.. :-)

---

### Post by tonybeccar on 2009-05-04
Hi, my problem magically was solved yesterday, now i'm getting around 2400 fps. Anyway, I notice when I move a window for example, that it moves a little choppy.. When have compiz DISABLED, it moves a little smoother, any idea what is the problem? because I've seen people to move windows REALLY smoothly.. again, thanks for your response!

---

### Post by garythegoth on 2009-05-04
> **tonybeccar said:**
> Hi, my problem magically was solved yesterday, now i'm getting around 2400 fps. Anyway, I notice when I move a window for example, that it moves a little choppy.. When have compiz DISABLED, it moves a little smoother, any idea what is the problem? because I've seen people to move windows REALLY smoothly.. again, thanks for your response!

Weird #-o

---

### Post by Mirge on 2009-05-04
Having a hard time wrapping my head around 6000 fps... or even 2400 fps. I assume FPS = frames per second? I'm used to people referring to 50-100 fps in games, how would one achieve 1,000+ fps? lol.. maybe i'm thinking of something completely wrong here.

---

### Post by tonybeccar on 2009-05-04
Thanks for your amazingly fast response.. Yeah, I don't know, I just want my Ubuntu to run Smooooothly... Maybe it's a monitor sync issue, like the response is too high or to low, I don't know, it's just a thought.. I would appreciate someone who know about this stuff...

---

### Post by garythegoth on 2009-05-04
> **tonybeccar said:**
> Thanks for your amazingly fast response.. Yeah, I don't know, I just want my Ubuntu to run Smooooothly... Maybe it's a monitor sync issue, like the response is too high or to low, I don't know, it's just a thought.. I would appreciate someone who know about this stuff...

You could try setting the resolution/vsync from the Nvidia X Erver Settings.
It may help......

---

