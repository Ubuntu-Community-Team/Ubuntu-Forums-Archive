---
title: "PCMan hosed my desktop"
date: 2010-06-30
forum: Desktop Environments
---

### Post by tharp on 2010-06-30
I heard good things about PCMan and wanted to try it because I hate Nautilus. When I installed it and rebooted, all my desktop icons are gone. So I uninstalled pcman and still no icons. I can go to a terminal and type "Nautilus" and they come back but they disappear when I exit the terminal.
HELP! Please!

---

### Post by kerry_s on 2010-06-30
use alt+f2 to launch nautilus

go to preferences-> startup
save the session so it can start just like that.

---

### Post by yossell on 2010-06-30
I believe that Nautilus is, on a default gnome set-up, responsible for drawing the icons on your desktop. So, in the absence anything else to draw your desktop, if Nautilus isn't running, you won't see the icons. If you're starting Nautilus from a terminal then, when you kill the terminal, you kill nautilus, and that's why you're seeing the behaviour you see. 

I think you have two options: either (a) go back to Ubuntu's default behaviour of running nautilus on start up and leave it running, and use it to draw the desktop; (b) keep nautilus turned of and install and deploy another programme to draw the desktop. I can't give any advice on (b) - a quick flick through software centre revealed idesk. Maybe try it or perhaps others could chip in with suggestions.

---

### Post by tharp on 2010-06-30
kerry_s, thanks but no go.
yossell, I would like it to default like it was, but not sure how to make it right again.
I want Nautilus to start when the system loads but I can't make it default again.
Man, I should have left it alone.

---

### Post by yossell on 2010-06-30
hmmm

it's likely to be buried somewhere in one of the eye-wateringly many boxes in configuration editor. I'm guessing here, but my first go would be to  try the following.

Type

gconf-editor

in a terminal. In the left hand panel, navigate to desktop-gnome-session-required_components.

Selecting required_components should, on the right hand panel, bring up filemanager and panel and windowmanager. If the value for filemanager is pcmanfm, there's your problem. Select it, and replace it with nautilus. When you log out and log in, hopefully it will run at startup.

---

