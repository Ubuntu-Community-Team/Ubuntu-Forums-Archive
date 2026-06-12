---
title: "CPU temperature montoring"
date: 2005-12-15
forum: General Help
---

### Post by sanmadjack on 2005-12-15
I'm having trouble figuring out how to use the gnome sensors applet. It keeps saying No Sensors found. I've installed lm-sensors and such, but I can't get it to display anything but the RAM I have. Any help?

---

### Post by earobinson on 2005-12-15
maybe your motherbord dose not report this information?

---

### Post by sanmadjack on 2005-12-15
If that's so, then my BIOS is pulling CPU temps out of it's butt.
I'm pretty sure it does.

---

### Post by mcduck on 2005-12-15
Have you configured lm-sensors? Run 'sensors' in terminal, does it work?

---

### Post by ekarni on 2005-12-15
I ran into something similar, and eventually tracked it down to some kind of problem with pnpacpi (pnp=plug and play, acpi = advanced computer power interface, pretty much laptops only AFAIK).  My fix is written up [here]("http://www.ubuntuforums.org/showthread.php?t=86341").  Note that identical symptoms might be caused by different problems, but it's worth a shot.

---

### Post by kingsidy on 2005-12-15
i have the same problem. How did the people get it to work. I get a lot of error and sometimes when i turn the computer off, the text says critical temperature reached. I am guessing that ACPI is not working

---

### Post by sanmadjack on 2005-12-15
As I said earlier, running sensors only outputs data on my RAM

---

