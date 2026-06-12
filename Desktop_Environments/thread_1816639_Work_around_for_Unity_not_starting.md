---
title: "Work around for Unity not starting"
date: 2011-08-02
forum: Desktop Environments
---

### Post by jony121 on 2011-08-02
My little How-To:
I have much patience for Ubuntu but my patience wares thin. Especially when after I login I get nothing other than my desktop background and my right click menu!
However all is not lost:
Update: I realised later that day that there is a much easier way of doing this that I didn't think of at the time. I am looking into what has caused this. I think gnome-session might be starting after unity. I tried deleting all the gnome configuration files in my home directory but no effect. If any one has any input then feel free to chime in.

Step1:
Log in to the affected account using the GUI login.

Step2:
Switch to terminal 1 (Ctrl+Alt+F1) and log in.

Step3:
In the terminal type: ```
export DISPLAY=:0
```
and hit enter. Then type ```
gnome-session-properties
```
and hit enter.

Step4:
Switch back to terminal 7 (Ctrl+Alt+F7)

Step5:
Hit Add and under command type ```
unity --replace
``` then call it what you like and hit Add.

Step6:
Either exit terminal 1 and then log out and back in to 7 or just restart the computer.

---

