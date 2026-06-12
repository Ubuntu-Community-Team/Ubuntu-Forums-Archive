---
title: "inactive rectangle in second X server (mouse cant enter)"
date: 2011-10-25
forum: Desktop Environments
---

### Post by fraktalek on 2011-10-25
Hi,

I upgraded to 11.10, I have a multiseat confinguration notebook+two LCDs (notebook and one LCD on one X server + the second LCD on a separate X server, see details here: [http://ubuntuforums.org/showthread.php?t=1457255](http://ubuntuforums.org/showthread.php?t=1457255)).

I just noticed that on the second LCD running on the separate X server (screen :1 via DisplayLink), there is a rectangle area in the lower left corner that can't be entered by the mouse pointer. It is rendered correctly though. 

I see no warnings or errors in the X log. Some idea what the problem might be? It worked fine in 11.04.

---

### Post by fraktalek on 2011-10-27
it's probably an x2x problem. I tried to use synergy instead of x2x and in that case it's possible to move the mouse cursor freely on the second screen.

However, synergy unfortunately has a bug: [http://synergy-foss.org/tracker/issues/2778](http://synergy-foss.org/tracker/issues/2778) that makes it pretty much unusable.

---

### Post by fraktalek on 2011-10-28
Just in case someone runs into the same problem:

[LIST]
[*]I wasn't able to fix the synergy blanking problem

[*]I wasn't able to fix the x2x problem

[*]**Solution**: replace x2x with a combination of x2vnc and x11vnc
[/LIST]

[LIST=1]
[*] on display :1 run x11vnc

```
$ DISPLAY=:1 x11vnc
```


[*]run x2vnc to connect to the vnc server

```
$ DISPLAY=:0 x2vnc localhost:0
```
[/LIST]

---

### Post by krunge on 2011-10-28
If you are using x11vnc and x2vnc in 'x2x-mode' you will get better interactive response if you run x11vnc with the '-nofb' option:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-win2vnc](http://www.karlrunge.com/x11vnc/faq.html#faq-win2vnc)[/INDENT]

---

### Post by fraktalek on 2011-10-29
Great, thanks a lot! I was wondering how to improve the performance.

---

