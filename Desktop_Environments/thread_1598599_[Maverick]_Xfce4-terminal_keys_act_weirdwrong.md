---
title: "[Maverick] Xfce4-terminal keys act weird/wrong"
date: 2010-10-16
forum: Desktop Environments
---

### Post by Hero of Time on 2010-10-16
Since the upgrade to Xubuntu 10.10, I'm having issues with Xfce4-terminal. When I use aptitude, the home and end keys don't scroll the list to the top or bottom. With vim, it generates input of adding a new line with F or H on it above the current line. Ctrl+arrow left/right also generate unwanted signals/characters.
This does not happen with Kubuntu or Ubuntu and when I install Gnome-terminal and use that, everything works as you expect. This even happens on the live environment. I don't want to use gnome-terminal, as it pulls in more packages than I need and the Xfce4-terminal should just work.

Another thing that happens is that when I read a man page or close vim or aptitude, it behaves as if it's in a TTY: the text it just showed stays on screen or it clears the bunch in the current view and puts the prompt at the bottom. It should be that the application just closes and you get the prompt back the way it was before you started to read the man page for example.

It is purely a terminal emulator problem. Does anyone have a solution for these issues?

---

### Post by Hero of Time on 2010-10-19
Anybody?

---

### Post by Hero of Time on 2010-11-05
Ok, I figured out it's a bug and should be fixed according to [https://bugs.launchpad.net/ubuntu/+source/guake/+bug/621927](https://bugs.launchpad.net/ubuntu/+source/guake/+bug/621927). But when I check the output of 'env', the TERM variable is linux, not xterm as what should be set by xfce4-terminal. Does anyone know of a solution, other than putting export TERM=xterm in .bashrc or some other file?

---

### Post by themtx on 2010-11-05
> **Hero of Time said:**
> putting export TERM=xterm in .bashrc

That's what I ended up doing.

---

### Post by Hero of Time on 2010-11-06
So you upgraded from 10.04 to 10.10 too? Then it would appear that's the problem. Somewhere in the upgrade, this problem arises. I have a clean 10.10 install at work and that one doesn't give a problem. Got a clean install on a VM and that too doesn't give a problem. Maybe it's something in our terminalrc file.

---

### Post by Hero of Time on 2010-11-14
I figured it's not there when you use GDM or KDM (no idea about other login managers). I use LXDM and that gives this issue. I'm keeping track of [https://bugs.launchpad.net/ubuntu/+source/guake/+bug/621927](https://bugs.launchpad.net/ubuntu/+source/guake/+bug/621927) and have already posted a few replies there.

---

