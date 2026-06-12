---
title: "Elisa and separate x-server problem om Jaunty"
date: 2009-04-17
forum: General Help
---

### Post by Bo Rosén on 2009-04-17
I just upgraded my Ibex to Jaunty RC, and so far everything seems fine with one exception.

I have a TV for a second monitor configured with a separate x-server via Nvidia X-server Settings. I mainly use the TV for Elisa.

After the upgrade, however, Elisa will only start on my main monitor and not on the TV. Any suggestions?

EDIT: Actually, it seems all programs I try start on screen 0 and not on screen 1 (the tv) so it's not limited to Elisa.

---

### Post by ajmorris on 2009-04-18
> **Bo Rosén said:**
> I just upgraded my Ibex to Jaunty RC, and so far everything seems fine with one exception.

I have a TV for a second monitor configured with a separate x-server via Nvidia X-server Settings. I mainly use the TV for Elisa.

After the upgrade, however, Elisa will only start on my main monitor and not on the TV. Any suggestions?

EDIT: Actually, it seems all programs I try start on screen 0 and not on screen 1 (the tv) so it's not limited to Elisa.

hi there,
do you any errors trying to start them on screen 1 when they start on screen 0 instead? also, does running (using xterm as a test) ```
xinit xterm -- :1
``` work?

AJ

---

### Post by Bo Rosén on 2009-04-18
Something ate my reply :o

Thanks for trying to help, much appreciated.

I do not get any errors when I start a program on screen 1 and as I'm unable to open a terminal I can't check by starting a program on the CLI.

The xinit command didn't help, but I am uncertain if I did what you intended. I opened a terminal on screen 0 and entered the command (with sudo). 
Both screens went black and a small xterm appeared on screen 0.

You may have seen that I asked about the same problem, adding a few details in [http://ubuntuforums.org/showthread.php?t=1128900](http://ubuntuforums.org/showthread.php?t=1128900) as that is probably a better place for the discussion.

---

