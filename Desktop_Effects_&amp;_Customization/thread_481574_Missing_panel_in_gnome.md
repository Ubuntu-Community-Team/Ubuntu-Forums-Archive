---
title: "Missing panel in gnome"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by paranoiahax on 2007-06-22
Hi, I have a missing panel, and it is my only panel. So I cannot click "add new panel" on a panel. I am running Ubuntu Feisty with Beryl. If I restart my computer, it often comes back, but not all the time and this is becoming more and more frequent. I have tried opening a terminal and typing "gnome-panel" but it say "I've detected a panel already running and will now exit"

Does anyone have any ideas on how I could sort this out?

Thanks in advance.

---

### Post by Elv13 on 2007-06-22
this will seem to you a really wierd question, what is your sound card?

I know there is a bug in ubuntu with some ati sound chips.

---

### Post by paranoiahax on 2007-06-25
yeah that did seem like a weird question. Well it's a RealTek HD audio controller I think, I'm not so good with hardware. 
It hasn't happened in a few days now, but I really cannot see a solution to fix this by myself so I may just need to wait for software updates or system updates. Thanks for your help anyway!

---

### Post by ivesjd on 2007-06-25
Ive had the same error when I boot with Compiz fusion enabled, and then restart X. When I boot with metacity, I can change to compiz fusion fine. And I have to do it this way because booting into compiz fusion gives me a black screen with only my cursor.

---

### Post by paranoiahax on 2007-06-25
Lol I had a similar problem nick-named the WSOD (white screen of death) on Beryl, and it was a known bug for feisty and OpenGLX lol. 

newer versians should fix these bugs though hopefully. 

It may even be to do with my screenlets (I have customised my desktop to look exactly like Vista, and the screenlets are the clocks down the side etc. so it may have something to do with that.

---

### Post by paranoiahax on 2007-07-04
well I sort of have fixed it, typing "killall gnome-panel" usually restores it, but with some items in the taskbar unclear and unusable lol, but apart from that, this addresses the issue.

---

