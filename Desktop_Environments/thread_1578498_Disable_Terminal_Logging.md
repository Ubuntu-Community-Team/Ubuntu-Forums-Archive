---
title: "Disable Terminal Logging"
date: 2010-09-20
forum: Desktop Environments
---

### Post by Arkitekt on 2010-09-20
I am trying to accomplish 2 things:
1) Disable terminal logging of command history and,
2) Discover a command that will actually clear the terminal screen, not just jump it to a new line.

I am using UNR 9.10, output of 'echo $TERM' is xterm, I am also using guake as a drop down terminal. 

I have used 'history -c' to clear session history, but if I open up a new tab within guake the history is still there. It only seems to delete it for the specific tab.

I have also used 'rm -rf ~/.bash_history' but don't want to do that all the time. also, does bash still store within RAM and then get written to bash_history upon logoff? 

Is there a away to set xterm or bash to not log anything at all ever? 

regarding clearing the terminal screen, the 'clear' command just seems to jump to a new line (meaning that I can scroll up and still see the buffer history). Is there a command to easily clear that without having to CTRL-W my tab within guake and then F12 again to bring up guake?

---

### Post by mcduck on 2010-09-20
I can't say anything about removing the history feature, never tried doing that since I actually find it very useful. Probably there is a variable for this in some Bash configuration file, but it definitely isn't in the terminal emulator's options (since it's a feature of the shell itself, not the terminal you use to run the shell).

Anyway, the command for clearing your terminal session is "reset". Like you said, "clear" or Ctrl-L just clears the screen while "reset" actually re-initializes the shell.

edit: A quick Google search for "bash history" gave me this guide: [http://www.ducea.com/2006/05/15/linux-tips-take-control-of-your-bash_history/]("http://www.ducea.com/2006/05/15/linux-tips-take-control-of-your-bash_history/")

---

### Post by Arkitekt on 2010-09-21
Thanks :), that page provided me with the information I needed

---

