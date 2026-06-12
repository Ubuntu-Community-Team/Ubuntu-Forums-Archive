---
title: "Gdesklets, not quite right..."
date: 2006-02-26
forum: Desktop Environments
---

### Post by xmastree on 2006-02-26
I'm running a new breezy installation, and I'm having problems with some desklets. Specifically, those which show a bar. Instead of the bar I just get a grey box.
[ATTACH]6443[/ATTACH]
That's sidecandy. On the right, working correctly, is the network but to the left of that, the cpu monitor shows the correct graph, but the bar above it is just grey. I'm running with it 'closed' so it doesn't show the graph or the bar, but I would like it to work correctly.

I also tried FTB, but that's the same. FTB worked for me with my Hoary installation, but not here. :-k 

Am I missing some package to allow these bars to show?

---

### Post by alamba on 2006-02-26
Same problem here, what's FTB? Maybe I could try that too.

A

---

### Post by slazh on 2006-02-26
Same problem here. I know the problem has been posted a few times on the forum, but nobody knows why it happens and how to fix it :(

---

### Post by xmastree on 2006-02-26
[QUOTE=alamba]Same problem here, what's FTB? Maybe I could try that too.[/QUOTE][**FTB**](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=224) is a set of desklets similar to side candy.

---

### Post by TherapyQuestionMark on 2006-03-02
Hey, I had the same problem with the FTB gauges.

I snooped through the source code and found a fix.

For the FTB Hard disk space gaues, look for the line:

<gauge id="data" fill="50" anchor="sw" y="100%">

By changing the anchor from "sw" to "se" the gauge will decrease from the right to show how much space you have left.

I'm not sure if this fix will work for other desklets, but report back if it does.

---

### Post by sabredog on 2006-03-02
That trick worked!

Many thanks for the assist :)

---

