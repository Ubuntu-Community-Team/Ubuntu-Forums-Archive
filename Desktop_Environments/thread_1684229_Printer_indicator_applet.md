---
title: "Printer indicator applet?"
date: 2011-02-08
forum: Desktop Environments
---

### Post by darthpenguin on 2011-02-08
Hey guys,

Is there a printer app for the indicator applet? I would like to get rid of the notification area completly but I still use it to check my print status. Anyway to get that on the indicator applet?

Thanks

---

### Post by Frogs Hair on 2011-02-08
Try ```
sudo apt-get install printer-applet 
``` you will find it on the add to panel menu after installation.

---

### Post by darthpenguin on 2011-02-08
Thanks man,

Just a few things. First, this shows in the indicator-applet (i tested with printer-applet --show in the terminal). So that is great. I can't add it from the add to panel option as you say. I can run it from the command line or from alt+f2. my problem is, i don't know if it is actually running. if I run "printer-applet" from alt+f2 and then run a "ps -A | grep printer-applet" in the terminal I get nothing. is it running? do I need to add it to the startup applications?

also it is obviously a kde application and is does not have a monochrome icon. but it shows in the indicator-applet, so that's progress.

---

### Post by darthpenguin on 2011-02-08
Answered my own questions.

if anyone else does this;

sudo apt-get install printer-applet

add printer-applet to startup applications (if you want the icon to always show use the command printer-applet --show)

remove notification area from gnome-panel

just live with the fact that it's a KDE app (you only use it to check the print que anyway) and that is is not a monochrome icon.

also ps -A |grep printer-applet still shows nothing. in fact a read through of ps -A |more shows nothing that could remotely be the print applet. WTF? but it does work

Solved

---

