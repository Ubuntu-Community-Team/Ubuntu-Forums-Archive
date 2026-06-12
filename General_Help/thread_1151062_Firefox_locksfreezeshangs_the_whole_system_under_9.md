---
title: "Firefox locks/freezes/hangs the whole system under 9.04"
date: 2009-05-06
forum: General Help
---

### Post by Lnewb on 2009-05-06
Out of the blue while running firefox it decides to lock up my whole system and no keys work (like alt+ctrl+backspace/del) so beeing on a laptop I have to do alot of hard re-boots unfortunally.

I have now installed Opera and this browser is working like a charm,but I'm ashamed to say that I miss my stumble upon button :(

I cant find any solutions for this problem anywhere, anyone in here know?

Btw it worked just fine before the upgrade.

---

### Post by colau on 2009-05-06
> **Lnewb said:**
> Out of the blue while running firefox it decides to lock up my whole system and no keys work (like alt+ctrl+backspace/del) so beeing on a laptop I have to do alot of hard re-boots unfortunally.

I have now installed Opera and this browser is working like a charm,but I'm ashamed to say that I miss my stumble upon button :(

I cant find any solutions for this problem anywhere, anyone in here know?

Btw it worked just fine before the upgrade.
Firefox works fine in 9.04.
Interesting problem after upgrading.

---

### Post by look_as on 2009-05-09
I have the same problems.
It hangs up while typing URL into adress box :-(

---

### Post by Triptol on 2009-05-09
There are a couple of things you might want to try / look up:

[LIST]
[*]you could try deleting the FF cache (you can do that in FF in the settings menus).
[*](re)moving your firefox profile sometimes helps:
```
mv ~/.mozilla ~/.mozilla.old
```
This will ensure that FF starts with an empty profile. If that fixes it, your profile was broken. If it doesn't, you can still move back your old profile ;-)
[*]There are a lot of reported problems with Intel (and maybe ATI) video cards in 9.04. People experience hanging systems and so on, but that should not be related to FF.
[/LIST]

---

