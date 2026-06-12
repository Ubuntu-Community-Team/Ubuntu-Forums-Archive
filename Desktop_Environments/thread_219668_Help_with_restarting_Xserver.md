---
title: "Help with restarting Xserver?"
date: 2006-07-20
forum: Desktop Environments
---

### Post by mhafren on 2006-07-20
Hi.

I wonder if anybody could help me with this issue. I can't seem to restart the Xserver with "sudo /etc/init.d/gdm restart" command. The Ctrl-Alt-BackSpace works fine but I need to restart the Xserver from a script. When I run "sudo /etc/init.d/gdm restart" it does stop the xserver but it throws me to console login mode on tty1. It does not start the Xserver back. Now taking into account that Ctrl-Alt-Backspace does work I should be able to restart the Xserver from the terminal also, right?

Help would really be appreciated.

---

### Post by goobers on 2006-07-20
Does it not come up with an error message?

---

### Post by mhafren on 2006-07-20
Thanx for the prompt reply. No visible error messages, it just goes to text mode login after running "/etc/init.d/gdm restart". I am still wondering what command the ctrl-alt-backspace does, as that works? It can't be the same, can it?

---

### Post by ardchoille on 2006-07-20
When i do sudo /etc/init.d/gdm restart it throws me to tty1 also, but I found that when I do ctrl+alt+f7, x has indeed restarted, I just needed to get back to tty7. Have you tried to ctrl+alt+f7 after sudo /etc/init.d/gdm restart ?

---

### Post by mhafren on 2006-07-21
Actually when I press ctrl-alt-f7 after the restart of gdm my screen is blank. I guess there is a problem somewhere but this would not matter to me. If I still have to press something I can just press ctrl-alt-backspace to begin with. The reason why I don't want to have to press any keys is that I want to restart the x-server from a script.

---

### Post by pdc303 on 2006-07-21
> **mhafren said:**
> No visible error messages, it just goes to text mode login after running "/etc/init.d/gdm restart"

Are you running this from a console in X? If so, you will certainly be missing any errors outputted.

Log in to tty1 (ctrl+alt+F1) then run the command from there.

Mine looks like this:

```

>/etc/init.d/gdm restart

 * Stopping GNOME Display Manager... [ ok ]
 * Starting GNOME Display Manager... [ ok ]
```

---

