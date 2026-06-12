---
title: "Sound issue Open Arena"
date: 2007-05-29
forum: Gaming &amp; Leisure
---

### Post by Ripfox on 2007-05-29
I love to play OA but, the sound is like "scratchy"

Anyone else have this problem?

---

### Post by Ripfox on 2007-05-30
My first...bump..

---

### Post by Ripfox on 2007-05-30
Solved it...it was an old thing I forgot about making an .openalrc file in the home directory and pasting:

(define devices '(native))

into it and rebooting...no idea why it works but it fixes all my games that had scratchy audio.

---

### Post by n8bounds on 2007-06-19
yeah, I'm having that problem, is that exactly what you put in your ~/.openalrc file??

---

### Post by n8bounds on 2007-06-19
OMG that fixed everything, I didnt even have to reboot!

---

### Post by n8bounds on 2007-06-19
I am completely floored about this, this solved every sound issue I had.  I JUST DON'T UNDERSTAND WHY.  How in the heck was I supposed to know to do that??

---

### Post by Ripfox on 2007-06-20
Yep it's a rockin' fix!

---

### Post by dannystaple on 2008-02-06
OpenAL is the Open Audio Layer, an equivalent of OpenGL in sound terms, AFAIK. Anyway - this fix works for OpenArena, and I will try later but I suspect it solves some scratchiness/choppiness in a number of games.

If only such a simple fix could do anything about lag...

---

### Post by Sockerdrickan on 2008-03-15
For the love of epic win, just use OpenAL Soft [http://kcat.strangesoft.net/openal.html](http://kcat.strangesoft.net/openal.html)

---

### Post by Ripfox on 2008-03-16
Ok...either way seems easy enough! :lolflag:

---

### Post by WaveMyBlackFlag on 2009-08-14
Will this fix audio problems for all games of just oa?

---

### Post by Sockerdrickan on 2009-08-15
> **WaveMyBlackFlag said:**
> Will this fix audio problems for all games of just oa?
Are you referring to my post? Then yes.

---

### Post by WaveMyBlackFlag on 2009-08-15
Well either or, the .openalrc file fix or the OpenAL Soft,  my problem seems to be a bit off from all the threads I have looked at.  I can play music through rhythmbox, watch movies with sound in totem, GnomeMplayer and MPlayer.  The bongos at the log in screen play but the actual desktop init music is just static, LOUD static.  I've already disabled all system sounds due to the annoyance, but that still doesn't solve the lack of sound in any and all games i.e. from Open Arena/Nexiuz/Sauerbraten down to "simple" Briquolo and Chromium B.S.U.

My apologies, should have been more specific as to who I was addressing.

Hardware:
Acer Aspire 5535 AMD AthlonX2_64 2.1ghz, 4gb ddr667, 320gb hard disk, ATI Raedon HD3200 onboard w/512mb shared ram  Running Ubuntu Jaunty 9.04 w/ all current updates

---

### Post by WaveMyBlackFlag on 2009-08-15
> **WaveMyBlackFlag said:**
> Well either or, the .openalrc file fix or the OpenAL Soft,  my problem seems to be a bit off from all the threads I have looked at.  I can play music through rhythmbox, watch movies with sound in totem, GnomeMplayer and MPlayer.  The bongos at the log in screen play but the actual desktop init music is just static, LOUD static.  I've already disabled all system sounds due to the annoyance, but that still doesn't solve the lack of sound in any and all games i.e. from Open Arena/Nexiuz/Sauerbraten down to "simple" Briquolo and Chromium B.S.U.

My apologies, should have been more specific as to who I was addressing.

Hardware:
Acer Aspire 5535 AMD AthlonX2_64 2.1ghz, 4gb ddr667, 320gb hard disk, ATI Raedon HD3200 onboard w/512mb shared ram  Running Ubuntu Jaunty 9.04 w/ all current updates
sorry forgot sound hardware and that the Ubunu Install is the 64bit version

soudn hardware:  Onboard HDA ATI SB / Realtek ALC268

---

### Post by WaveMyBlackFlag on 2009-08-15
Got it.  Updated repositories, fixed settings in multimedia systems selector, fixed settings in settings->sound, viola...  sound all around.:guitar:

---

### Post by Strevin on 2010-05-19
Ok I have a problem with the Audio and the glitchy video. I usually can follow the way to fix it, but I don't understand what yall did to fix it. :confused::confused: Please post a step by step to fix it. Thank you.

---

