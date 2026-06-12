---
title: "Never seen this before.  Highlight not working."
date: 2019-09-10
forum: Desktop Environments
---

### Post by OpenSage on 2019-09-10
Hello, I have new install.  It is Ubuntu Mate 19.04 with the Unity7 desktop environment.  So of course I have had a few strange issues so far, but I have never seen this issue in all of my days of computing.  I am so used to clicking 2 times to highlight a word, or clicking 3 times to highlight a sentence.  Neither of which are working right now.  I first noticed it in FireFox trying to highlight a URL.  When that didn't work I tried it to highlight text on the page.  When that didn't work I opened a text editor and it did not work there either.  I can select text with a mouse and highlight it by right clicking and dragging the mouse over what I want highlighted, it is just the quick clicks are not working.  Any ideas?  Thanks for taking the time to read this.

---

### Post by Skaperen on 2019-09-10
can you do quick clicks in [COLOR=#0000cd][FONT=courier new]xev[/FONT][/COLOR]?

---

### Post by OpenSage on 2019-09-10
I tired it in xev, but I have never used it before and I don't really know what I am looking for.  It is giving the time and position of the mouse button press and then the position of the mouse as I move the mouse and the time and position of the release of the mouse button.  If I do rapid clicking it does register all of them.

---

### Post by OpenSage on 2019-09-10
Solved.  It was a double click speed setting.  It had been changed from in the middle of a sliding scale of slow to fast, to all the way on the fast side of the slider.

---

### Post by Skaperen on 2019-09-11
[COLOR=#0000cd][FONT=courier new]xev[/FONT][/COLOR] would have shown if any clicks were lagged or missing.  gotta subtract the timing or just watch it.  it's a useful tool if you develop interactive GUI apps.

---

