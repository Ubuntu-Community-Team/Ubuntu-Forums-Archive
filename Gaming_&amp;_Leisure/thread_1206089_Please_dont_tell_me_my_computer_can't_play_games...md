---
title: "Please dont tell me my computer can't play games..."
date: 2009-07-06
forum: Gaming &amp; Leisure
---

### Post by CharlesWelsh on 2009-07-06
I have a Toshiba Satellite A15- S1292 with an Intel Celeron Processor in it. For some reason ALL of the games I play lag. I couldn't even play Brutal Chess :( Is there something i need to do? Or is there some kind of package or something I need in order to play these games? (Dont know how to check graphics card) ANY help would be appreciated... -CJ

---

### Post by tommcd on 2009-07-06
What video card is in your machine? Open a terminal and run:
```
lspci | grep -i vga
```
and post the output here.

---

### Post by X-BANE on 2009-07-06
Your laptop has an old Intel graphics chip, I'm afraid you can't expect much in the way of 3D performance on Linux or Windows.

---

### Post by Irritant on 2009-07-07
What you are experiencing is not "lag", it's low fps.

---

### Post by noerrorsfound on 2009-07-07
> **Irritant said:**
> What you are experiencing is not "lag", it's low fps.
The English language disagrees with you.

---

### Post by b@sh_n3rd on 2009-07-07
The output of the code **tommcd** gave would help you resolve your probs. If you've got an Intel card and you use Jaunty, there's a fix for a bug that seems to have popped up. But the fix is for i850 and i950 cards...(I *think*)

---

### Post by CharlesWelsh on 2009-07-07
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)

---

### Post by Irritant on 2009-07-07
> **noerrorsfound said:**
> The English language disagrees with you.

Not true.

Lag refers to the latency between a client and server.  

What he is expierencing is low fps, caused by the client system being unable to render the game fast.

---

### Post by Barky on 2009-07-07
> **Irritant said:**
> Not true.

Lag refers to the latency between a client and server.  

What he is expierencing is low fps, caused by the client system being unable to render the game fast.

YES

the average person doesn't differentiate between the two and it drives me nuts!

---

### Post by CharlesWelsh on 2009-07-07
Ummmm... back to topic please... as i posted in No. 7 as you guys wished... what do i do?

---

### Post by Grishka on 2009-07-07
> **CharlesWelsh said:**
> Ummmm... back to topic please... as i posted in No. 7 as you guys wished... what do i do?

get a better video card.

---

### Post by Pressondude on 2009-07-07
> **Grishka said:**
> get a better video card.

Which basically means get a new laptop

---

### Post by Sef on 2009-07-07
How much ram do you have?

---

### Post by Bölvaður on 2009-07-07
Well the intel graphic cards are pretty weak.
But you might get something more working with a better driver. There was a bug with Jaunty that caused intel cards not to give you what you need, driver wise. There are how-tos on this forum.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

It is also possible to go to earlier versions of ubuntu like 8.10 or 8.04 which might be easier.

---

### Post by ShadowTek on 2009-07-07
Have you tried to run any NES emulators?

I've yet to see a modern system that can even do *that*. But if even that stutters, you're in some bad shape!

---

### Post by b@sh_n3rd on 2009-07-08
The link in post #14 is the fix I was talking about. I'm not sure if you could play *all* games though it's known that Intel cards aren't really the *best* when it comes to Linux. However, I was able to kick my frames up and enable 3D Acceleration with that how to. After that I could even mess around with windows games on wine and configure cairo-dock for my desktop. My card was a 82845 btw so it's actually older than yours. In other words, you may get better results than I did. If you *do* follow the how-to linked above, I recommend using the "Optimal" method...hope this helps...

---

### Post by insanity99 on 2009-07-08
> **CharlesWelsh said:**
> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)

thats a very weak graphics card i'm afraid. thats why you should always build your own computer, or at least get on custom built.

---

