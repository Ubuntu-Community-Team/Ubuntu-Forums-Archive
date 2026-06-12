---
title: "panel"
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by Jack to Jill on 2008-04-15
My panel disapears when I close the terminal, I cant seem to fix it.

---

### Post by chewearn on 2008-04-16
Could you elaborate a bit more please?
What panel are we talking about here?

When you close a terminal, all child processes of the terminal will close with it.  If the panel you are referring to was run in the terminal, then it is expected that the panel will close, once the terminal is closed.

---

### Post by Zorael on 2008-04-16
While we wait for more information, if you ever want to start something in a terminal and you don't want it to terminate upon closing the terminal itself, just add an ampersand (& sign) after the command to make it run in the background.

```
$ gedit &
```
You can then terminate the process either by invoking **kill** and supplying the PID number that was output upon running the command itself (right after gedit there in that example), or by calling **killall gedit** (or whatever the name was of the command you ran). Do note that if you have several processes with the same name, all with get terminated. Hence, kill**all**.

---

### Post by chewearn on 2008-04-16
> **Zorael said:**
> While we wait for more information, if you ever want to start something in a terminal and you don't want it to terminate upon closing the terminal itself, just add an ampersand (& sign)

Ermm, that won't work.  The process will still be a child process of the terminal and will close upon closing the terminal.

Rather, use the run dialog, invoked by ALT+F2.

---

### Post by Zorael on 2008-04-16
> **AstalaVista said:**
> Ermm, that won't work.  The process will still be a child process of the terminal and will close upon closing the terminal.

Curious.

I understand where you're coming from, and the logic seems sound, but as long as we're talking about gnome-terminal, konsole or similar I dare say you're wrong, not because of expertise but rather personal experience.

I have many a time run compiz --replace &, kate &, gedit &, kicker &, pidgin &, skype &, azureus &, and a plethora of other apps, and closing konsole did not kill their processes.

---

### Post by chewearn on 2008-04-16
Curious.

I did another test; if you close the terminal by using command: exit<enter>, it close without closing the "gedit &".  But if you close the terminal by clicking on the [x], both closes.

---

### Post by Jack to Jill on 2008-04-16
Well that is strange, exiting the window any other way than typing 'exit' makes the panel go away...       The panel I am talking about is my desktop panel, with the windows and the applications. But, that seems to have done the trick.

---

### Post by Zorael on 2008-04-16
Is this with gnome-terminal? I didn't notice this at all with Konsole, and I'm fairly sure that by now I would've closed at least one session with the buttons.

---

### Post by chewearn on 2008-04-16
> **Zorael said:**
> Is this with gnome-terminal? I didn't notice this at all with Konsole, and I'm fairly sure that by now I would've closed at least one session with the buttons.

I checked with gnome-terminal and xfce4-terminal.  Both behave in this manner.

---

