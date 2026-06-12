---
title: "crazy question"
date: 2008-06-27
forum: Desktop Environments
---

### Post by Riffer on 2008-06-27
I'm doing a down and dirty installation of xbuntu for classroom at school.  I want to switch off the panel, and just have 3 icons on the desktop, an app, terminal, and the shutdown/log-off applet.

I know I can use the right click launcher feature, but what are the commands?  Thanks for your help.

---

### Post by bubba_169 on 2008-06-27
1. App - depends on what application you want to run...

2. Terminal - you want 'gnome-terminal' or is it 'xterm' for xfce? One or the other...

3. Shutdown - 'sudo shutdown -h now' (check 'run in terminal')

---

### Post by wrtpeeps on 2008-06-27
> **bubba_169 said:**
> 1. App - depends on what application you want to run...

2. Terminal - you want 'gnome-terminal' or is it 'xterm' for xfce? One or the other...

3. Shutdown - 'sudo shutdown -h now' (check 'run in terminal')

2. The command to run a terminal in xfce is xfce4-terminal. :)

---

### Post by Riffer on 2008-06-27
Thanks so much.  

Is the shutdown command just shuts down the machine?

How can you do it for logging off?

---

### Post by wrtpeeps on 2008-06-27
I googled for logoff and a few posts on this site seem to say killing your gnome session is the way to do it, though I doubt that will work on xfce4?

---

### Post by Ozor Mox on 2008-06-27
> How can you do it for logging off?

'logout' logs out at the command line, would this work?

---

### Post by bubba_169 on 2008-06-27
To logout do 'sudo killall Xorg'

Make sure you have a capital X in the name or it wont work!

---

### Post by Riffer on 2008-06-27
nope logout didn't work, and the sudo one wasn't what I was looking for.  I want the students or guest to be able to logout.

---

### Post by wrtpeeps on 2008-06-27
Won't killing X just bring them out of the gui, but keep them logged in at a command prompt?

---

### Post by imbjr on 2008-06-27
For my young son, I have a logout button on his desktop that calls:

gnome-session-save --kill --silent

This allows any account mods made to be retained.

---

### Post by bubba_169 on 2008-06-27
> **imbjr said:**
> For my young son, I have a logout button on his desktop that calls:

gnome-session-save --kill --silent

This allows any account mods made to be retained.

Thats OK but Riffer is using XFCE not gnome ... :)

---

### Post by Riffer on 2008-06-27
Though it seems that XFCE uses alot of gnome features.  I'll check it out.  :)

---

### Post by madjr on 2008-06-27
> **Riffer said:**
> I'm doing a down and dirty installation of xbuntu for classroom at school.  I want to switch off the panel, and just have 3 icons on the desktop, an app, terminal, and the shutdown/log-off applet.

I know I can use the right click launcher feature, but what are the commands?  Thanks for your help.

when you edit the xfce menu, you can see all it's commands

[IMG]http://img503.imageshack.us/img503/4821/untitleded2.png[/IMG]

[IMG]http://turkey.fvdh.net/~hanumizzle/xfce4-review/menu-editor.png[/IMG]

---

### Post by K.Mandla on 2008-06-27
Moved to Desktop Environments.

---

