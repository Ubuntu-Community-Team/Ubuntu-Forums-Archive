---
title: "Gnome Terminal CR/LF issues on Procurve Switches"
date: 2011-08-22
forum: Desktop Environments
---

### Post by ro345 on 2011-08-22
Hello,

When using ssh or telnet to access a Procurve switch, the CR/LF doesnt always seem to work.  It works fine on xterm or konsole.  For example, if I simply hit enter at the default procurve prompt, I should see the prompt repeat itself and increment the line.  For example, if I hit enter 4 times I would expect this:

Procurve Switch# 
Procurve Switch# 
Procurve Switch# 
Procurve Switch# 
Procurve Switch# 

What I get instead is just this:
Procurve Switch# 

it makes it look like the switch is just hung.  

If I use xterm or konsole, it works correctly.  I have not noticed this issue with any other equipment.  Thanks for any help.

---

