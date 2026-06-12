---
title: "[SOLVED] Suddenly firefox uses 100% of my processor!?"
date: 2008-09-18
forum: Desktop Environments
---

### Post by amyg on 2008-09-18
Ok, I'm still fairly new at all of this, so anyone that is brave enough to help me, please be patient.

I've been running ubuntu fairly well for a few months now.  I've never had lag issues with Firefox.  Recently, my husband wanted me to install LOTRO, which I successfully did (after some help), and yesterday I finally tweaked my graphics settings as good as I can in the LOTRO folder in My Documents, and *in* game.

So that shouldn't have had an effect on anything in my desktop, right?  I'm only throwing that out because it's exactly when all of this started, but it doesn't seem logical to me.

Nonetheless, suddenly when I run my browser, it's like running it on dial up.  It's very very slow to load, and when I hover my processor use on my task bar, it will suddenly say that my cpu is 100% in use.

A friend told me that I should use the top program and he thought I'd be fine with running, understanding it, and finding what program was causing the problem.  Which would end in me killing it.

Thing is, I don't know enough to feel comfortable randomly killing things as knowing my luck it'd be something very important (and not related to the problem).

When I watch top from terminal and switch firefox pages, xorg and firefox are the top in use.  Other than that it's this random  Ieee80211/0 or  Ieee80211/1 that pop up.

I see a background loader as well on occasion, but the top two always seem to be xorg and firefox.

Is there anything else that I should try to look at or run?  I'm sure it's something really simple, it normally is, that I'm overlooking.  Any advice would be wonderful.

Thank you.

---

### Post by RensoreK on 2008-09-18
Have you tried using 'htop' I personally think its easier to use. Does this happen even right after you reboot? Or after running LOTR? Could you shed some info as to what you've tried and when the problem occurs?

---

### Post by amyg on 2008-09-18
It was even after reboot.  After expirmenting around I realized that my virtual box worked fine, and so I was right to assume that firefox was the primary issue.  I moved the folder over to a  different directory, reinstalled firefox, then moved it back and all is working well at the moment.

Thank you for answering, like I said, it always seems to be something simple that I miss in my panic.  I'd like to jokingly blame my being female, but I'm afraid someone else might come in and not like that ;)

As to why it happened initially after making those changes to Lotro, I guess it was just a weird coincidence. 

Thanks again RensoreK.

---

