---
title: "GNOME Icon display failure"
date: 2010-02-15
forum: Desktop Environments
---

### Post by yyann on 2010-02-15
Hello everyone!

As of now, I run a Ubuntu 9.10 Karmic Koala system (2.6.31-20-generic-pae #57-Ubuntu SMP Mon Feb 8 10:23:59 UTC 2010 i686 GNU/Linux)

For a while now I've been experiencing a weird behavior of icons. In fact, it comes down to the one particular icon displaying the w-lan status in the notification area. Sometimes, in about half of the cases, it is shown as a black box. There is no way to click it or do anything to it, yet connection and everything works fine. Funny: When I change the width of the panel it belongs to, it appears normal again. So, every once in a while, I need to do this in order to be operational. 

Seems, this started with the update to 9.10. Anyone else experienced this? I will gladly provide any information you desire but have no idea as to what might help you. :S

All the best,
yyann.

---

### Post by NightwishFan on 2010-02-15
That is a very odd bug. Perhaps you should gather information and screenshots and report it.

Does it do this on a fresh install or after a bit of time? Also are you running Compiz desktop effects? Try turning off desktop effects then logging out and back in.

---

### Post by yyann on 2010-02-15
Hello NightwishFan,

 thanks for your time. I've indeed installed Compiz ages ago and I seems I still had some of the effects activated, though none of them were particularly visible. I switched them off now and the last time I logged on, the "odd bug" didn't happen. For now, I'll keep an eye on this. Maybe it did the trick.

Funny thing, noone else experienced this. Doesn't happen on my desktop machine neither... let's see!

Anyways: I appreciate your compassion and hope you have a great time!
yyann.

---

### Post by sisyphus1978 on 2010-02-15
I get this frequently on UNR 9.10, running openbox. I issue > killall gnome-panel
 and it often reloads fine. Gmail notifier seems to be the culprit in my case.

Good luck.

---

### Post by mcduck on 2010-02-15
> **yyann said:**
> Hello everyone!

As of now, I run a Ubuntu 9.10 Karmic Koala system (2.6.31-20-generic-pae #57-Ubuntu SMP Mon Feb 8 10:23:59 UTC 2010 i686 GNU/Linux)

For a while now I've been experiencing a weird behavior of icons. In fact, it comes down to the one particular icon displaying the w-lan status in the notification area. Sometimes, in about half of the cases, it is shown as a black box. There is no way to click it or do anything to it, yet connection and everything works fine. Funny: When I change the width of the panel it belongs to, it appears normal again. So, every once in a while, I need to do this in order to be operational. 

Seems, this started with the update to 9.10. Anyone else experienced this? I will gladly provide any information you desire but have no idea as to what might help you. :S

All the best,
yyann.
That's an already reported (and confirmed) bug (although I can't remember if the buggy appp responsible was the notification area applet or the nnetwork manager ;)).

Anyway, until it gets fixed there is not much you can do about it, but pressing Alt-F2 and running "killall gnome-panel" is a quick way to get the network manager icon working correctly.

---

### Post by yyann on 2010-02-21
Thanks everyone. Ever since fuzzing around with the Compiz-effects, I haven't experienced the issue again. Could be coincidence, though. None the less, I'll try and set this thread to solved. Maybe this can help with the current bugwork?

Best wishes,
yyann.

---

