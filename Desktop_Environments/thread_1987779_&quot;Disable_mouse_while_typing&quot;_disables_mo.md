---
title: "&quot;Disable mouse while typing&quot; disables mouse too long."
date: 2012-05-26
forum: Desktop Environments
---

### Post by crosstalk on 2012-05-26
In Xubuntu, when I go into the settings and hit the setting to disable the mouse while typing, it disables the mouse for quite a while (2 seconds, according to a quick ps).

Is there a config file I don't know about where I can easily change this? If not, I'll just add syndaemon with my own favorite options to startup.

Thank you for any help.

---

### Post by fredlb on 2012-06-20
I'm having the same issue and I'm unsure of how to use syndaemon properly. Any help is appreciated!

---

### Post by crosstalk on 2012-06-20
Note: the following instructions are for Xubuntu 12.04 and may not work (without modifications) in earlier or later versions.

First, go into your mouse settings and turn off the "Disable mouse while typing" feature (otherwise, Xubuntu's fix will conflict with ours).

To set up Syndaemon, launch the "Session and Startup" program in the Settings Manager. In this program, select the "Application Autostart" tab.

In the bottom left corner, there should be an "Add" button. Press it. Go ahead and call the new entry "Syndaemon" and put "Disables mouse while typing" in the description (you can change these; they're not very important).

In the "Command" box, I suggest putting the following command:
```
syndaemon -i 0.5 -d -t -K
```

You can find an explanation of all syndaemon options by running "syndaemon -h" in a terminal, but I'll also describe the ones I use here.

"-i 0.5" describes the amount of time the mousepad is disabled. In this case, it is half a second.

"-d" runs it as a "daemon". You should leave this here.

"-t" tells it not to disable mouse movements while typing, just scrolling and button-pressing.

Last, "-K" tells it to ignore stuff like Ctrl-C, Shift, and other "modifier" keys and combinations.

Let me know if you have any issues with these instructions.

---

### Post by fredlb on 2012-06-21
Thanks for the thorough explanation! Seems to work great :) (also running Xubuntu 12.04)

---

