---
title: "How to Get Back to Desktop from TTY4 Login Prompt After Ctrl+Alt+F4??"
date: 2009-06-17
forum: General Help
---

### Post by OzzyFrank on 2009-06-17
I've both accidentally and intentionally hit **Ctrl+Alt+F4** in the past (intentionally when everything is frozen and even Ctrl+Alt+Backspace does nothing) and the only useful command I've been able to use at the prompt that appears is **reboot**. I've tried **startx**, only to have it tell me the X Server is already running. I've tried other commands like **gdm** to no avail, so it begs the question:

**[COLOR="Indigo"]How do you get back to the desktop you just left once you end up at this prompt??[/COLOR]**

Everything I've tried either tells me whatever I've tried to invoke is already running, or it tells me I don't have permission (and when I try with sudo I'm usually given arcane info on why it can't be started), and the only thing to do is use **reboot** (which at least gives me a clean shutdown). But there _has_ to be a command that can just return me to the desktop... so what is it?? Cheers.

---

### Post by rolleander on 2009-06-17
after logging in to prompt, simply type the command logout
$ logout
should get ya right back to desktop

---

### Post by Therion on 2009-06-17
[COLOR="White"].[/COLOR]

**Ctrl+Alt+F7** will do it.

---

### Post by OzzyFrank on 2009-06-17
Thanks buddy, just tried it and **[COLOR="Indigo"]logout[/COLOR]** did the trick! Never thought to try that - I did try the opposite, **login**, to no effect. Do you know whether things still run in the background, like downloads in particular? Cheers.

---

### Post by redilyn on 2009-06-17
If you press CTRL+ALT+F4 to switch to a terminal the desktop is still running.

Just press CTRL+ALT+F7 to get back to the desktop. Any programs which were running when you switched to terminal will still be running when you switch back to the desktop

---

