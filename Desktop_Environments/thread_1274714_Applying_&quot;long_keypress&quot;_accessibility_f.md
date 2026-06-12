---
title: "Applying &quot;long keypress&quot; accessibility feature to only one key"
date: 2009-09-24
forum: Desktop Environments
---

### Post by tmetro on 2009-09-24
I've encountered a common problem where I accidentally hit the caps lock key. My preference is not to remap it to something else or make it a dead key. The ideal behavior would be to have the key continue to work, but respond only after a delay, and even better, provide audio confirmation (see [this other post]("http://ubuntuforums.org/showthread.php?p=8002712#post8002712")) that the caps lock state has been toggled. In searching for how to implement this, I've read that Apple recently implemented such a caps lock delay in OS X.

It turns out that the accessibility features (System -> Preferences -> Keyboard, Accessibility tab) in GNOME already provides the desired feature - called "Slow Keys"/"Only accept long keypresses" - and has an adjustable delay. The problem is that this feature applies to all keys, not just ones you specify.

Anyone know of a hack to get the delay feature to apply to a specific key? Is there a lower layer interface for configuring the accessibility features?

 -Tom

---

### Post by Giblet5 on 2009-09-25
There's a discussion of capslock [here]("http://www.linuxquestions.org/linux/answers/Hardware/Getting_Control_on_Caps_Lock_A_How_To").

---

