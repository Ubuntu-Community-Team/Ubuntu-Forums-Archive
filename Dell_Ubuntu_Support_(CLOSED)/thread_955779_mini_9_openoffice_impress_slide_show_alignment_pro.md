---
title: "mini 9 openoffice impress slide show alignment problem"
date: 2008-10-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by milton1 on 2008-10-22
I have and love my new dell mini 9, but I have one problem. When I go to view a slide show in OOo impress while connected to an external projector, the slide show is centered on the laptop screen, which causes it to be off center and get cut off on the projected screen. Switching to the external projector shrinks the taskbars to a standard 4:3 ratio, and many screens will maximize correctly to fill only the left side of the display. viewing pdf's in presentation mode correctly displays only on the part of the screen that is projected. Sadly, the slide show problem with impress persists. Now I, personally, would just switch to exclusively using beamer and presenting in the pdf format, but I need to occasionally share this system with my students, and many of them will know only powerpoint or impress as a tool for presentations (sadly, I haven't the time to teach them beamer/LaTeX).

So ultimately, my question is this: Is there a way I can set OOo impress to display the slide show shifted to the left so it will not be cut off by the projector?

---

### Post by cmspider on 2008-11-20
Try making sure that you start up openoffice only after the projector is connected.  I think it does a better job of its display if both displays are active when it starts up.

---

### Post by milton1 on 2008-11-26
Thanks, but I already tried that. It didn't help. Any other suggestions? Could there be some setting to better integrate OOo settings to match gnome's? As I mentioned before, the pdf viewer does a great job of correctly displaying beamer presentations.

---

### Post by armandh on 2008-11-26
how about a solution in the projector instruction book
position etc.

---

### Post by yakker.yak on 2008-11-26
> **milton1 said:**
> Thanks, but I already tried that. It didn't help. Any other suggestions? Could there be some setting to better integrate OOo settings to match gnome's? As I mentioned before, the pdf viewer does a great job of correctly displaying beamer presentations.

Would Impress -> Save as PDF do the trick? Doesn't fix the original problem, I know, but should work :)

---

### Post by milton1 on 2008-11-30
Yes, this works. In fact, it is one of the first things I tried. Unfortunately, it renders any dynamic content useless.

---

### Post by ldorman on 2009-03-22
Attached is a one-slide example of how things do not fit.
This slide views OK under a "normally" proportioned display.
On the Mini, even with no external display attached, the title
lies outside the slide bounds and the equations have lost
their alignment with the text.
The Ooffice version is
openoffice.org-core 1:3.0.1-7ubunbu1hardy1.Fri Mar 20 19:45:27 UTC 2009
Openoffice 3.0.1
OOO300m15 (Build:9379) (the foregoing was typed in, not pasted)

Does anyone have any ideas about whether this is an ooffice
problem, or is in xorg?

The attachment is a gzipped .ppt file

---

