---
title: "No logoff sound?"
date: 2008-01-02
forum: Desktop Environments
---

### Post by hvtuananh on 2008-01-02
When i login to Ubuntu, i heard login sound
but when i logoff, my computer play nothing
I set up logoff sound coincide with login sound but i heard nothing

Can i fix it?
I'm using Ubuntu 7.10

---

### Post by hvtuananh on 2008-01-03
No solution :)

---

### Post by Najmudin on 2008-01-03
I'm having the same problem since installing gutsy .
May be you will find a solution in the last post in this bug report
[COLOR="Red"][COLOR="Orange"][https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/131711]("https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/131711")[/COLOR][/COLOR]
 , i will try it now, may will fix the problem.

---

### Post by Najmudin on 2008-01-03
Its fixed for me now , after long waiting .:guitar:
I have to thank the guy who suggest this solution on the bug report.:)

---

### Post by rainwalker on 2008-01-03
I'm confused...what solution does it talk about?

---

### Post by hvtuananh on 2008-01-03
> **Najmudin said:**
> Its fixed for me now , after long waiting .:guitar:
I have to thank the guy who suggest this solution on the bug report.:)
This solution doesn't work for me!

---

### Post by Najmudin on 2008-01-04
> **rainwalker said:**
> I'm confused...what solution does it talk about?

What i understand from his post is that you have to search for these in synaptic :
- esound.
- esound-clients.
- pulseaudio-module-gconf.
- pulseaudio
Check the boxes and install them , then restart you machine ( in my case i did a hard restart ).
thats what i did exactly and my problem was solved.
if that didn't help you , remove them and do a hard restart ( as he said)
If that didn't help also , wait for the bug to be fixed or ask some one knows better than me.:lolflag:
I hope that will help.
Good luck for every one.

---

### Post by hvtuananh on 2008-01-04
Yes. Finally it works!
Thanks so much

---

### Post by Najmudin on 2008-01-04
> **hvtuananh said:**
> Yes. Finally it works!
Thanks so much

I'm glad to hear that .

---

