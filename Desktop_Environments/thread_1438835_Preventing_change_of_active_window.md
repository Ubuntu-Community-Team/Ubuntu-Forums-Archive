---
title: "Preventing change of active window"
date: 2010-03-25
forum: Desktop Environments
---

### Post by dorylinus on 2010-03-25
I'm having a problem wherein a background window will become the active window (i.e., the one to which text from the keyboard is sent) when it calls for attention.  This is problematic when I'm debugging code in MATLAB and leave it to run and then go to another window in another workspace to write an email or somesuch; when MATLAB hits the breakpoint I've set, the current window remains displayed on the screen but my text is suddenly going to MATLAB instead.

What I'm looking for is some way to ensure that the active window REMAINS the active window until I manually switch it myself so that I don't have to worry about seeing text being sent somewhere off-screen ever.  How do I enforce this on Ubuntu?

Using Ubuntu 9.10, and GNOME 2.28.1  (default Ubuntu installation).

---

### Post by dag.stromsvag on 2010-10-27
I have the same problem...any suggestions?

---

### Post by mcduck on 2010-10-27
If you use Compiz, you'll find options for focus stealing prevention in the "Focus & Raise Behaviour" -tab under General Options (in CompizConfig Settings Manager). Try different levels to see what works best for you.

---

