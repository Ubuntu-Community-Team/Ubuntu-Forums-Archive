---
title: "OpenGL mouse pointer (and other input) behaves strangely"
date: 2009-04-03
forum: General Help
---

### Post by JohnLM_the_Ghost on 2009-04-03
I have a bit of problem while trying to play games on my Ubuntu box.
Well there seems to be a problem with some input processing for OpenGL.

Especially mouse behaviour is really erratic, however it is not limited to mouse cause keyboard also play tricks on me.

From what I can see it looks like input signals get stacked on input buffer (just as it should), but they get processed only when more input is coming instead of "ASAP policy".

Most fun is pressing screen buttons, I struggle to point my cursor to a button, then click... but click responds only when I move my mouse a bit more (often making cursor leave the button).

No such behaviour happens with x11 mouse. (And also limited to Linux)
Also for some games this can be overcome using windowed (UFO:AI for example), however most OGL games still does it in windowed mode.

My specs are:
AMD Phenom 9950 (2.66Ghz Quadcore)
ATI Radeon HD4850
Usual USB mouse and keyboard

Ubuntu Interpid x86_64

Anyone has a clue?

---

