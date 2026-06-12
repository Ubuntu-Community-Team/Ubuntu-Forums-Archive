---
title: "F-Keys not working in 10.10"
date: 2010-12-01
forum: Desktop Environments
---

### Post by mjrmua on 2010-12-01
After installing Ubuntu 10.10 my function key hot-keys (F1 though F12) are no longer working. So I can't press F5 to refresh this webpage as I would expect -- very frustrating!

If I press F1, I get a popup saying "Power Information" instead of help for the application in focus.  So I assume there is some program running in the background that is interrupting these function key presses.

Is this expected behavior for 10.10?

But either way, how do I get back to having the function keys interpreted by the currently focused application?

---

### Post by gogolink on 2010-12-01
I guess you could re-define the behavior of your function keys under System > Preferences > Keyboard Shortcuts, no?

---

### Post by mcduck on 2010-12-02
Is it a laptop? Make sure your "Fn" (or equivalent)  key isn't stuck or something. The "power information" popup sounds a lot more like  a laptop's feature, especially considering I've never seen or even heard of such a thing in Ubuntu itself.

If that doesn't help enough, could you provide a screenshot, and perhaps a bit more information about the machine itself. And also, what do the *other* function keys do?

---

### Post by theaceoffire on 2011-03-05
This was bothering me FOREVER. Nothing but F1 worked, and it popped up a black box with a blue icon saying "Power Information". 

Turns out there is a black key with black text that says "F Mode" on my keyboard. No lights signify you hit it, and no where does ubuntu mention it... but if you hit it, all F keys will stop working.

**I am replying to this old topic because it is the number 1 google result that I got, and no one else knew the answer.

---

### Post by asmoore82 on 2011-03-06
A lot of new laptop designs are doing this &#8212;
I'm not sure that Ubuntu even can be aware of it.

The OS has to take whatever input the keyboard hardware sends and
we would all assume that the keyboard keys are clearly labeled
for the user, but it's getting where it's not easy to tell whether
the *Function* key is "Naturally On" or "Naturally Off."

---

### Post by mcduck on 2011-03-06
> **theaceoffire said:**
> This was bothering me FOREVER. Nothing but F1 worked, and it popped up a black box with a blue icon saying "Power Information". 

Turns out there is a black key with black text that says "F Mode" on my keyboard. No lights signify you hit it, and no where does ubuntu mention it... but if you hit it, all F keys will stop working.

**I am replying to this old topic because it is the number 1 google result that I got, and no one else knew the answer.

Usually that kind of functionality is handled directly by the computer's BIOS, the Fn/F Mode -key might not even be visible to the OS at all. It just receives the resulting function- or special keypresses.

So not getting any indication for Fn switch keys really isn't Ubuntu's fault, you'll have to blame the computer's manufacturer instead. (On the other hand that's the kind of thing that definitely is mentioned in the computer's manuals... ;))

---

