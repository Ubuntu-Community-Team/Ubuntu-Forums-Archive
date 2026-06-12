---
title: "I still don't get how Compiz Fusion can do 50x what Vista does with half the power"
date: 2007-08-04
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-08-04
I just finished installing Compiz Fusion on my Inspiron 8600 after Beryl being too slow and Compiz in Feisty being...well, messed up. And all I can say is, WOW.
It's just mind boggling to me, that somehow this amazing software (whether it's unstable or not) can do all of these amazing things, yet I'm running it on a laptop with NOWHERE near the requirements to run Vista's wimpy effects.
I can't help but wonder how it's done! Can anyone explain this to me?

---

### Post by BitTorrentBuddha on 2007-08-04
I believe the answer lies in openGL, however I'm not certain.

---

### Post by psyopper on 2007-08-04
It is OpenGL. There's a lot more to it than this but essentially Fusion takes screenshots and then manipulates them with OpenGL libraries. 

Almost ALL "3D" video cards support OpenGL instruction sets natively. Asking your video card to reduce the opacity of Firefox is about as easy as asking your processor to open Firefox.

Microsoft is using DirectX 10 to do effects in Aero. Unfortunately for MS not nearly as many video cards are fully DX10 capable as they are OpenGL capable.

---

### Post by DMXell on 2007-08-04
You beat me to the punch Psyopper! Yes, that is the reason. But in addition Direct X is a clunky system, it takes more lines of coding, and thus more complex calculations, to achieve the same effect. SO naturally it'll be slower.

---

### Post by rainwalker on 2007-08-04
Well, that's pretty spiffy!

The only problem is, at least the effects in Vista work...
I put Compiz Fusion in my things to load at the start of each session, restarted, and now it no longer works
I'm about to post a thread about it, hang on...

---

