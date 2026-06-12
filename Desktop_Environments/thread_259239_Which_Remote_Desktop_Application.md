---
title: "Which Remote Desktop Application?"
date: 2006-09-17
forum: Desktop Environments
---

### Post by tobaccoman on 2006-09-17
Hello!

I'm a newbie and have installed Ubuntu on two machines, A and B.

Now I would like to use a Remote Desktop to see computer A from computer B (As I did with Win XP machines).

I'm confused because found various applications (Krdc, Terminal Server Client, etc.) and don't know how to start.

What should I install on both computers?

And, is there something that would allow me “remote desktoping” my LINUX from Win XP?

(note: i'm currently making my trials in a home network)


Thank you for any feedback!

Cheers!

Daniel

---

### Post by mitch.c on 2006-09-17
> **tobaccoman said:**
> Now I would like to use a Remote Desktop to see computer A from computer B (As I did with Win XP machines).

I'm confused because found various applications (Krdc, Terminal Server Client, etc.) and don't know how to start.

If you want to make it easy on yourself, use Terminal Server Client (since it's already installed) to view winxp from ubuntu. If you don't like it... try something else! O:) 

> **tobaccoman said:**
> What should I install on both computers?

And, is there something that would allow me “remote desktoping” my LINUX from Win XP?

On you ubuntu machine:
System -> Preferences -> Remote Desktop
Enable Allow other users to view your desktop
Enable Allow other user to control your desktop

On your win xp machine:
Download/install vncviewer [http://prdownloads.sourceforge.net/vnc-tight/tightvnc-1.2.9_x86_viewer.zip?download](http://prdownloads.sourceforge.net/vnc-tight/tightvnc-1.2.9_x86_viewer.zip?download)
Start vncviewer and connect to ubuntumachine:0

Good luck!

---

### Post by tobaccoman on 2006-09-18
Thank you!

I will immediatly try this.

What about communicating between two Linux machines ?

Best regards,

Daniel Staempfli

---

### Post by lamego on 2006-09-18
Juse install the vnc on the linux system and connect to the other system using the viewer.

---

