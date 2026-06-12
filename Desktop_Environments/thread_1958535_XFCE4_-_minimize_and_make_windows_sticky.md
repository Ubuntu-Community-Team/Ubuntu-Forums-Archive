---
title: "XFCE4 - minimize and make windows sticky"
date: 2012-04-14
forum: Desktop Environments
---

### Post by darioshanghai on 2012-04-14
Hi guys,

I wrote a small script that launches a local web server and then opens the main page of the service I want to use into a browser.

I'd like the browser window to be sticky and minimized. How do I do this in a bash script? I hoped I could use wmctrl, but I just wasted one hour trying because minimize (called "hidden") does not work.

How can I do this?

Thank you.

---

### Post by darioshanghai on 2012-04-14
the browser is chromium which, as the manual says, responds to gtk+ commands.

Does gtk+ have a command to do these things that I can stick on a command line?

---

### Post by Jose Catre-Vandis on 2012-04-14
To minimize/maximise try xdotool:
```
xdotool search --name "Google - Chromium" windowminimize
xdotool search --name "Google - Chromium" windowraise
```

---

### Post by darioshanghai on 2012-04-14
Hi,

I got to the same conclusion, thanks.

To emulate the stickiness I used
xdotool key alt+F8

But since you can only use keystrokes if the window is not minimized I ended up with
 
```
xdotool search --name 'WINDOW-TITLE-HERE' windowactivate
xdotool key alt+F8
xdotool key alt+F9
```

Thank you

---

