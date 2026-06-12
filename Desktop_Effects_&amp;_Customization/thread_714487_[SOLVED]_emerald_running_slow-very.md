---
title: "[SOLVED] emerald running slow-very"
date: 2008-03-03
forum: Desktop Effects &amp; Customization
---

### Post by spandanj on 2008-03-03
hi everyone,

i have been enjoying ubuntu for 3 months - all working great including compiz_+emerald

- but, out of nowhere, one day gutsy became very slow. I particularly noticed this when i tried to resize a window. cpu usage shoots through the roof - 100%, and the computer lags to the point of "stuck". 

however, the problem was resolved upon uninstalling emerald. ubuntu got back to its ever lightning fast speed with only compiz and metacity remaining.

so, i reinstalled emerald to confirm that it was causing the problem. lo and behold, i have re/uninstalled emerald 3 times to find that it is the culprit.

anyone have a solution to cure this. the thing is: it USED TO WORK FINE until 2 weeks ago. since then i have been stuck with "meta" uglycity. i wanna get back to emerald....

show me a light!
thankxx

---

### Post by dennis.groome on 2008-03-04
I have a similar problem where two instances of grep consume most of my processor when I start Ubuntu. The greps are tied to compiz somehow, maybe to reading config files? It was working find since Gutsy came out and only started having problems over the weekend.

---

### Post by spandanj on 2008-03-05
yeah,

i dont know what the problem is. i have absolutely no skills in config files. if anyone requests to post one of my config file output to help - i ll be happy to do so. 

if not, i guess/hope the problem will be resolved with a fresh install of hardy heron in april.

-spandan

---

### Post by spandanj on 2008-03-10
look guys,

the problem is still not solved. i really want to use emerald for transperant windows ---- can someone please HELP me????

---

### Post by spandanj on 2008-03-10
for someone who's trying to solve this problem (IS THERE?)

it becomes slow only AFTER i try to resize a window. up until that point, ubuntu is running fast and ok. after a window resize, everything becomes slow.

---

### Post by spandanj on 2008-03-13
SOLVED

Here's what i did:

i made a new user--Guest. logged into guest. since i had emerald installed, it worked fine in guest. i could even resize a window without slowing it down. so then i realized that the problem must lie in my own account not in the general emerald installation. so, i went back to my account. i opened up ".emerald" in my home folder. there were 2 folders--theme and themes. and, a config file. i deleted all three. restarted emerald theme manager, and added a new theme. now, everything works fine.:):guitar:

---

