---
title: "gnome-panel doesn't launch automatically"
date: 2011-07-30
forum: Desktop Environments
---

### Post by Jouke S on 2011-07-30
I'm using 11.04 with the old panels, no side panel.
For some reason gnome-panel doesn't launch automatically so I have to do it via terminal, which means I have to keep the terminal tab open if I want to keep my panels. 

Adding it to startup programs resulted in invisible panels (Cannot register the panel shell: there is already one running.), which I bypassed by typing gnome-panel --replace.
I would like a permanent solution though..

---

### Post by drpjkurian on 2011-07-30
try the command ```
gnome-panel &
```

---

### Post by Jouke S on 2011-07-30
> **drpjkurian said:**
> try the command ```
gnome-panel &
```

The panels still close as I close the terminal :(

---

### Post by westie457 on 2011-07-30
I know the following resets missing panels. No idea if it will keep them after a reboot.
No harm in trying though. Run ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

---

### Post by Jouke S on 2011-07-30
> **westie457 said:**
> I know the following resets missing panels. No idea if it will keep them after a reboot.
No harm in trying though. Run ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

Not sure what exactly happened but it's fixed, thanks :p
After the command the panels reset to their defaults and in the right top corner it said 'root', I also didn't have access to any of my files and folders in nautilus, which scared me a bit :P 

But after restarting X everything works again, the panels appeared instantly

---

### Post by _rH on 2011-07-30
Thanks for the tips guys. 

I noticed the latest 11.04 updates removed the "classic" desktop option, and seemed to replace it with KDE Plasma and user-defined (the latter of which did not work). 

Panels were not happening in KDE, however, gnome-panel fixed that. 

Cheers!

---

