---
title: "tool that show each mouse action as command line in terminal"
date: 2009-05-25
forum: General Help
---

### Post by forum4programs on 2009-05-25
[SOLVED]
hi,

somebody know what tool I need to install, so I know what command line is being executed by each mouse action?

For example: 
             - if I click firefox-icon in the top panel, the command line to be shown is "firefox".
             - if I click my Home-folder (desktop icon), the command line to be shown is "thunar /home"

and so on.

---

### Post by x33a on 2009-05-25
i don't exactly get what you mean, but if you want to know the exact command for a running application, you have many options.

1. ps aux | less.

2. top command gives you a list of running apps.

3. best option is to use htop (install it through aptitude or synaptic). it will give a similar output as top, but in a much better format.

---

### Post by forum4programs on 2009-05-25
Hopefully, you understand after I modify your's text, below (second paragraph with "=>"):

> **x33a said:**
> if you want to know the exact command for a running application => ".... if you want to know the exact command just executed".

that "ps aux" feel somehow closer to my answer, but better one is "history"-command.

Unfortunately, "history"-command doesn't show time executed, doesn't detect executed command after a mouse-click and it is not real-time (like "top"-command).

real-time is not important in this part.

---

### Post by x33a on 2009-05-26
now that i have understood what you want, you should definitely try htop.

it's just like ps aux, but with a better presentation.

just enable tree view in htop, and you'll be able to see each process as it is created and its parent.

---

### Post by forum4programs on 2009-05-26
htop is excellent. It is what I need. Thank you x33a

---

