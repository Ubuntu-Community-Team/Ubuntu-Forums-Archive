---
title: "How to remove dual monitor label?"
date: 2010-09-06
forum: Desktop Environments
---

### Post by auburn305 on 2010-09-06
I'm running Ubuntu 10.04 with dual monitors enabled.  Technically speaking, everything works just fine.  There is one very annoying aesthetic issue, though.  There is a label in the top left corner of each display that identifies the monitor (Dell 18", for example).  The label does not disappear and is always on top.  I had to move my panel to the bottom of the screen just to avoid the label.

How can I remove/hide this label?

Thanks!

---

### Post by mcduck on 2010-09-06
Make sure the monitor preferences dialog is closed, and the display identification popup should disappear.

If the dialog isn't open, and the identifier still shows then my first bet would be some graphics glitch that causes the identifier to stick on the screen. In that case try setting your monitors as you lke them, and rebooting, the identifier really shouldn't appear unless you open the Monitor Preferences dialog. (I couldn't even find any option that would allow you to force it to show always, not even through gconf)

---

### Post by Makaniea on 2010-09-06
> **auburn305 said:**
> I'm running Ubuntu 10.04 with dual monitors enabled.  Technically speaking, everything works just fine.  There is one very annoying aesthetic issue, though.  There is a label in the top left corner of each display that identifies the monitor (Dell 18", for example).  The label does not disappear and is always on top.  I had to move my panel to the bottom of the screen just to avoid the label.

How can I remove/hide this label?

Thanks!

Hey there auburn305,
Typically this label is only on there while the monitor preferences window is open, make sure you dont have that application minimized any where, or have it running in the background. If you still dont see it running, go to System &#8594; Administration &#8594; System Monitor | and kill the process Gnome-Display-Properties, Highlighted in the Attachment. Let me know if this works.

---

### Post by auburn305 on 2010-09-06
Ahhh... I hate it when the solution is simple (unless I try the simple option first).  I also failed to find the setting in gconf.  The always reliable power cycle eliminated the label and I haven't been able to recreate the situation since.

Thanks!

---

### Post by mlitty on 2011-03-23
this worked for me also, thank you.

> **Makaniea said:**
> Hey there auburn305,
Typically this label is only on there while the monitor preferences window is open, make sure you dont have that application minimized any where, or have it running in the background. If you still dont see it running, go to System &#8594; Administration &#8594; System Monitor | and kill the process Gnome-Display-Properties, Highlighted in the Attachment. Let me know if this works.

---

### Post by scndsky on 2012-01-06
I confirm that solution to work. Thanks!

---

### Post by fattyz on 2012-02-07
Thanks I had set up dual monitors at work and couldn't lose that laptop tag in the upper left hand corner of the screen.  I had also been wondering how to "end task" in Ubuntu.

FattyZ

---

