---
title: "Openbox - black font on black background in terminal window"
date: 2013-06-27
forum: Desktop Environments
---

### Post by PeterTaps on 2013-06-27
Folks,

Environment: Ubuntu 13.04 + Openbox

When I open a terminal window, I do not see the prompt. All I see is a black background. If I type "ls," for example, I see the list of files. My guess is that the font color for prompt as well as input text has been set to black. 

Using "XTerm*Foreground" and "XTerm*Background" in .Xresources and well as .Xdefaults doesn't seem to make any difference.

Fortunately, I have found a workaround. I blindly type "xterm -bg white &" to open a new xterm.

I am wondering if there is a way to fix this problem.

Thank you in advance for your help.

Regards,
Peter

---

### Post by dbass81 on 2013-06-27
I am running Ubuntu 13.04 minimal with LightDM-GTK-Greeter + Openbox as my WM.  I never much cared for xterm.  I use lxterminal.  It doesn't have any dependencies, and it is light-weight.

---

### Post by PeterTaps on 2013-06-27
Thank you for your help. lxterminal seems to work great. Plus, it has a scrollbar that xterm didn't have.

Do you just edit menu.xml and replace "x-terminal-emulator" with "lxterminal" or is there a better way?

Regards,
Peter

---

### Post by dbass81 on 2013-06-27
Are you trying to replace xterm with lxterminal?  Just run "sudo update-alternatives --config x-terminal-emulator" and pick lxterminal.

If you mean the openbox menu use obmenu, you will need to install it its not installed by default.

---

### Post by PeterTaps on 2013-06-29
Thank you for your help.

Regards,
Peter

---

