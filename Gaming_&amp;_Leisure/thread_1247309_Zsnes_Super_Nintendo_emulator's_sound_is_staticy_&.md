---
title: "Zsnes: Super Nintendo emulator's sound is staticy &gt;_&gt;"
date: 2009-08-22
forum: Gaming &amp; Leisure
---

### Post by Sorry For Trolling on 2009-08-22
Zsnes's sound is really staticy when i try to play a game, i changed the settings to 48000mhz it fixed it a little bit but it still sounds staticy can anyone help me?

---

### Post by nomnomnom on 2009-08-23
Which Ubuntu are you using?

---

### Post by Sorry For Trolling on 2009-08-23
> **nomnomnom said:**
> Which Ubuntu are you using?

Jaunty

---

### Post by nomnomnom on 2009-08-23
> **Sorry For Trolling said:**
> Jaunty

Is it the ZSNES from Add/Remove? I remember having issues with that too.

---

### Post by Sorry For Trolling on 2009-08-23
no you have to type it in the terminal to open the program. there's a version for linux.

---

### Post by nomnomnom on 2009-08-23
> **Sorry For Trolling said:**
> no you have to type it in the terminal to open the program. there's a version for linux.

Ok, I think you have misunderstood. Let's try this way.

How did you download ZSNES to your PC?

---

### Post by Sorry For Trolling on 2009-08-23
Whadda ya know, zsnes is in the add/remove section. :P I didn't check.

---

### Post by nomnomnom on 2009-08-23
> **Sorry For Trolling said:**
> Whadda ya know, zsnes is in the add/remove section. :P I didn't check.

Lol, that doesn't matter so much. How did you get ZSNES onto your PC in the first place?

---

### Post by Sorry For Trolling on 2009-08-23
It was a .deb package and it installed.
It wasn't an .exe file or anything.

---

### Post by nomnomnom on 2009-08-23
> **Sorry For Trolling said:**
> It was a .deb package and it installed.
It wasn't an .exe file or anything.

O-k. Do you remember the site you got the Deb from?

---

### Post by Sorry For Trolling on 2009-08-23
no sorry i can try and look for it again if you want

---

### Post by nomnomnom on 2009-08-23
> **Sorry For Trolling said:**
> no sorry i can try and look for it again if you want

It would kind of help.

---

### Post by Sorry For Trolling on 2009-08-23
[http://fileforum.betanews.com/detail/ZSNES-for-Linux/990106453/2](http://fileforum.betanews.com/detail/ZSNES-for-Linux/990106453/2) i think thats where i got it from...80% sure.

---

### Post by nomnomnom on 2009-08-23
> **Sorry For Trolling said:**
> [http://fileforum.betanews.com/detail/ZSNES-for-Linux/990106453/2](http://fileforum.betanews.com/detail/ZSNES-for-Linux/990106453/2) i think thats where i got it from...80% sure.

That's a tar.bz2, not a Deb.

---

### Post by chriswyatt on 2009-08-24
"Sorry for trolling" :roll:

---

### Post by mister_playboy on 2009-08-24
I have the same issue... sound in zsnes on Linux isn't quite up to par compared to the Win32 version. :-k  Not sure if much can be done about it.

---

### Post by nomnomnom on 2009-08-24
> **mister_playboy said:**
> I have the same issue... sound in zsnes on Linux isn't quite up to par compared to the Win32 version. :-k  Not sure if much can be done about it.

If it's the version I think it is you can.

---

### Post by flathampster on 2009-08-25
I just fixed mine by changing the sound config to 8000Hz Sampling rate. Using the GUI Menu > Config > Sound : then click on Sampling rate until it reaches 8000

At least it worked on the one game Ive tried so far (f-zero)

---

### Post by spcwingo on 2009-08-25
I believe this is the same problem I was having after installing ZSNES.  You can try launching it with:

```
zsnes -ad sdl
```

Then try different sampling rates under config>sound>sampling rate...then again, you might just want to try different sampling rates before running with the above code.  Good luck and let us know how it turns out.

---

### Post by Sorry For Trolling on 2009-08-26
I just tried snes9express and it works perfectly :D :D

---

