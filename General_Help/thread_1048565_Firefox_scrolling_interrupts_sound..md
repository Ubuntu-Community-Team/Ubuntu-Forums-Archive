---
title: "Firefox scrolling interrupts sound."
date: 2009-01-23
forum: General Help
---

### Post by JRCavileer on 2009-01-23
The Title is a bit self explanatory, if i scroll to fast or to much it stops music playback in Rythmbox for second or two (or until I (or Firefox) stops scrolling).

I've tried switching the sound devices...same problem.

Using Version 3.0.5 (Firefox) and Intrepid Ibex. Any clue?!

---

### Post by Nisko on 2009-01-23
Doing too many things at once for the CPU to handle?

---

### Post by JRCavileer on 2009-01-23
No, just Firefox, rythmbox, and pidgin. I have my CPU set at 2.20GHz. 0 percent is being used, but when i scroll it jumps to 50-60%.

---

### Post by JRCavileer on 2009-01-23
bump!

---

### Post by JRCavileer on 2009-01-24
Ok through research on the internet, I found that i was not the only one. And an easy way to fix it is to use crossfading backend.

Edit --> Preferences --> Playback tab --> Use crossfading backend

---

### Post by rrbarbosa on 2009-01-30
Thanks man. I noticed the problem some days ago, I was scrolling the output of some really large file at the same time I was generating it, so I though the problem was CPU usage.

But as today I had the same problem while just using one texmaker and rhythmbox I saw it could not be lack of processing power available.

And on the first thread that I found the problem, already had a solution. Great! :popcorn: 

(bad we don't have the thank you button working today)

---

### Post by nocive on 2009-05-08
Thanks!
Had the exact same problem.
You're a life savier :)

---

### Post by aasami on 2009-05-09
Thanks man!
This bothered me for long time. :guitar:

---

### Post by jcline on 2010-04-13
I was having trouble with scrolling in nedit interrupting sound.
Reading the response above about CPU usage made me realize that this was the problem.  I think that many programs can hog CPU cycles during scrolling.  To solve this problem for myself, I redefined the nedit command to nice -n19 nedit.  No more audio problems!

---

