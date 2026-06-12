---
title: "Command line annoyances"
date: 2009-01-01
forum: General Help
---

### Post by DBQ on 2009-01-01
Hi everybody.  I have a command line program which I run in bash. When I type something, and need to correct it, I try to use cursor keys to find the position of the character I want to change.  However, when I do the cursor does not move back, and instead prints: ^[[D when I press left arrow key and ^[[C when I press the right arrow key.  Is there some setting of bash (or anywhere else) that I can change to make moving using cursor keys around the input possible? If it is it would be great, since its REALLY REALLY annoying having to retype the whose input (inputs can be very long strings).  Thank you all.

---

### Post by dcstar on 2009-01-01
> **DBQ said:**
> Hi everybody.  I have a command line program which I run in bash. When I type something, and need to correct it, I try to use cursor keys to find the position of the character I want to change.  However, when I do the cursor does not move back, and instead prints: ^[[D when I press left arrow key and ^[[C when I press the right arrow key.  Is there some setting of bash (or anywhere else) that I can change to make moving using cursor keys around the input possible? If it is it would be great, since its REALLY REALLY annoying having to retype the whose input (inputs can be very long strings).  Thank you all.

All my cursor keys work correctly either in a X terminal window or in a full screen CTRL-ALT-Fx window, so I would suggest something has altered your system from default behaviour.

---

### Post by snova on 2009-01-01
> **dcstar said:**
> All my cursor keys work correctly either in a X terminal window or in a full screen CTRL-ALT-Fx window, so I would suggest something has altered your system from default behaviour.

Not necessarily. They work here, too, but this is a script.

In particular, try 'read' at a prompt, which I can only guess is what he is using in his script. It doesn't work for me...

---

