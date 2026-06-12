---
title: "How to use both audio outputs together?"
date: 2008-12-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Daniel Rentzsch on 2008-12-06
Hi there,

I would like to know how to use both front audio outputs of the Dell Inspiron 1525 at once.
When I use them seperately it works fine, they both give a signal. But when I plug an audio device into both, only the right one works.
I already enabled everything I found in HDA Intel (alsa mixer).

Thank you very much

---

### Post by Denny Johnson on 2008-12-06
Post #6 worked for my 1420n:
[http://ubuntuforums.org/showthread.php?t=604314&highlight=headphone](http://ubuntuforums.org/showthread.php?t=604314&highlight=headphone)

---

### Post by Daniel Rentzsch on 2008-12-07
Thanks for the answer, Denny.

Unfortunately it doesn't work for me. In "alsamixer" I have for some reason only the control for "master", nothing else (with F4 I can switch to "capture", that's all).

As far as I understood what's written in #6 there, that's only the solution for using laptop speakers and headphone output at once, but not both headphone outputs together.

What I found out so far:

- "Master" and "PCM" is for every output
- "Front" is for the internal speakers and the left audio output
- "Surround" has no for me noticable effect
- "Center" is for the LEFT box of the RIGHT audio output. So when it is unmuted, I have only sound on the right box, when it is plugged in the right audio output.  


Thank you so far

---

### Post by Denny Johnson on 2008-12-08
> **Daniel Rentzsch said:**
> 
Unfortunately it doesn't work for me. In "alsamixer" I have for some reason only the control for "master", nothing else (with F4 I can switch to "capture", that's all).



If you open the Alsamixer Volume Control [double click Volume Icon]........do you have an Edit option?.......if so, if you click preferences, this should allow you to enable more visible controls.

---

### Post by chongzi889 on 2008-12-08
API 6A **[gate valve](http://www.valvesupplier.net/index.htm)** product lines is available for two styles: expanding gate- and slab gate valves,they are Design Feature:Non-rising stem design to permit [gate valve]("http://www.valvesupplier.net/index.htm") installationin closer quarters.

---

### Post by Daniel Rentzsch on 2008-12-08
Yeah, I already did so, I enabled everything that has anything to do with output, and everything is enabled, too.
Though, it does not work yet.

---

### Post by Daniel Rentzsch on 2008-12-14
I read the instruction manual for the inspiron 1525 and it says that both are usual headphone outputs - so why does Dell built in two headphone outputs if only one can be used at once? Or what is the purpose of this?

---

### Post by Denny Johnson on 2008-12-14
Both of my outputs work at the same time since I applied the fix linked in the 2nd post above.
Can you post a screenshot of your Alsamixer settings, after you open from terminal?

---

