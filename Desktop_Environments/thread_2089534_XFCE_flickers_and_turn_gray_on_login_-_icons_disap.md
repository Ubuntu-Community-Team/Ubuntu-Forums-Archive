---
title: "XFCE flickers and turn gray on login - icons disappear - panel crashes"
date: 2012-11-29
forum: Desktop Environments
---

### Post by bigwalk on 2012-11-29
Greetings everyone,

[SIZE=1]First off, I just wanted to express how GRAND and IMPORTANT I believe the linux communit[SIZE=1]ies[/SIZE] [SIZE=1]are[/SIZE]. In the about 5 months it's been since I really started to get into linux, I've[SIZE=1] convinced many of the people close to me, including colleagues and friends[SIZE=1],[/SIZE][/SIZE] to run [SIZE=1]it.[/SIZE] My entire family has made the switch, including my uncle that[SIZE=1] is[/SIZE] terrified of computers. [SIZE=1]They've[/SIZE] never been happier with th[SIZE=1]e[SIZE=1]ir machines![/SIZE][/SIZE] I am therefore honored to be able to contribute by submitting my problem, and hopefully finding a so[SIZE=1]lution[/SIZE]. May it also help others in the future.[/SIZE]

I was using my XFCE session in Xubuntu 12.04 like always, when the desktop suddenly started to flicker. It flickered 4 or 5 times before the desktop turned completely gray, and all the desktop icons disappeared.

When I tried to click *Xfce-applications-menu* ( from the top panel), the whole panel flickered. I clicked the button a couple more times, and the panel crashed completely. 

I can relaunch the panel with no hassle, but the problem persists.

The strange part is that the rest of the panel, that contains the launchers, window buttons, action buttons, calendar and more, are working just fine. For instance, I can reboot my computer using the action buttons. I can also apparently run any program using Alt+F2, or by using my still-working docky-bar. I did, however, notice that I can't access the *display-settings* from* xfce4-settings-manager*. I get an error saying "Unable to start the Xfce Display Settings".

Another strange thing happens when I launch the file manager (nautilus): The desktop icons reappear, and the desktop turns blue! All the other problems remain.

So yeah, I'm beat. ^^

Any suggestions are welcome.

---

### Post by LewisTM on 2012-11-29
The first thing to do when diagnosing a problem is to determine if it's at the system level or caused by a user setting.

You could start off with a default user setup, either by creating a new user and logging into Xfce, or by resetting you Xfce config. If the problem persists, it's a system problem and you should reinstall Xfce and maybe then entire Ubuntu OS (after having backed up the contents of your home folder).

To reset your config:
1) Log out of Xfce
2) At the login prompt, switch to TTY1 (Ctrl-Alt-F1) and login
3) Execute [FONT="Courier New"]mv ~/.config/xfce4 ~/.config/xfce4.bak[/FONT]
4) Go back to the login manager (Ctrl-Alt-F7) and log into Xfce/Xubuntu session.
5) You panels will be recreated from default settings. Hopefully they won't crash.

Good luck!

P.S. Launching nautilus will replace the Xfce desktop with the one for GNOME, which is what you experience when you see the background change color. To just use it as a file manager, use this command:
```
nautilus --no-desktop
```

---

### Post by bigwalk on 2012-11-29
Thank you for your swift reply, good sir.

Resetting my config had no effect on the old profile whatsoever, but creating a new one did work. After a  reboot, the default setup was working again. So yay!

Oh, the nautilus tip was most excellent!

---

### Post by LewisTM on 2012-11-29
If resetting your Xfce settings didn't work but a new profile did, then the problem was most likely caused by some conflicting program or setting outside of Xfce.

Glad you got your desktop working again! Please mark as SOLVED.

---

