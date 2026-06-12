---
title: "Terminal issue"
date: 2022-03-02
forum: Desktop Environments
---

### Post by asai on 2022-03-02
For some strange reason the Terminal wont work.
I am running Ubuntu 20.04 and Wayland desktop environment.
Any suggestions?

---

### Post by TheFu on 2022-03-02
Option a: Install a different terminal program and use that?  There are 20+ of them. "Terminal" is a type of program, not a specific program, often called a terminal emulator, to point back to the olden days when it was common for computers to have 50 terminals in the next room for users.  Also called a shell or the CLI for even more general use.
Option b: use a different computer and ssh into the linux one using the local terminal from that other machine.
Option c: check the system logs to see what may be happening.

---

### Post by ajgreeny on 2022-03-02
What do you mean by "won't work"?

Does the terminal open or does nothing open when you try to open it from the menu equivalent in gnome, or by using Ctrl+Alt+T?

Or does it do nothing when you type any commands in the terminal and hit enter?  Please tell us all the details.

---

### Post by #&amp;thj^% on 2022-03-02
Along with others, I'm also confused, if the terminal window wont open try:
Ctrl + Alt + F3 and enter:

```
sudo apt remove gnome-terminal
```

After, re-install it with:

```
sudo apt install gnome-terminal
```
Also along with what the others have said, you can always use an alternative terminal emulator.

---

### Post by guiverc on 2022-03-02
This question was placed in the **Lubuntu** area; which is [**Xorg** **only**]("https://github.com/lxqt/lxqt/issues/10") (LXQt) & uses `qterminal` by default (as it's a Qt5 system).

LWQt is *experimental* only  (ie. *LXQt is for Xorg, LWQt for Wayland*) where Lubuntu supports only LXQt currently.

---

### Post by #&amp;thj^% on 2022-03-02
> **guiverc said:**
> This question was placed in the **Lubuntu** area; which is [**Xorg** **only**]("https://github.com/lxqt/lxqt/issues/10") (LXQt) & uses `qterminal` by default (as it's a Qt5 system).

LWQt is *experimental* only  (ie. *LXQt is for Xorg, LWQt for Wayland*) where Lubuntu supports only LXQt currently.

Good Catch "Lubuntu" I blew right by that.
My money's on gnome though. :p

---

### Post by asai on 2022-03-03
> **ajgreeny said:**
> What do you mean by "won't work"?

Does the terminal open or does nothing open when you try to open it from the menu equivalent in gnome, or by using Ctrl+Alt+T?

Or does it do nothing when you type any commands in the terminal and hit enter?  Please tell us all the details.

Nothing opens when I try to open the menu item or CTRL+ALT+T. Nothing happens.

---

### Post by TheFu on 2022-03-03
And did you try any of the the suggestions above?
Did they work? If not, what was the result?

---

### Post by asai on 2022-03-03
> **TheFu said:**
> And did you try any of the the suggestions above?
Did they work? If not, what was the result?

No not yet. Will try tonight. Was just to clearify what the problem is.
Will try your suggestions with your number 3 first, and so fort. :)
I will update the thread with information how I fixed it. ;)

---

### Post by asai on 2022-03-03
Heres syslog entry:

```
Mar  3 16:36:43 server1 systemd[2190]: Starting GNOME Terminal Server...
Mar  3 16:36:43 server1 gnome-terminal-server[6929]: Non UTF-8 locale (ANSI_X3.4-1968) is not supported!
Mar  3 16:36:43 server1 systemd[2190]: gnome-terminal-server.service: Main process exited, code=exited, status=8/n/a
Mar  3 16:36:43 server1 systemd[2190]: gnome-terminal-server.service: Failed with result 'exit-code'.
Mar  3 16:36:43 server1 systemd[2190]: Failed to start GNOME Terminal Server.
```

Suggestions?

---

### Post by TheFu on 2022-03-03
Change your locale to be UTF-8 ... or use a different terminal program ... like an xterm or lxterminal.  There are 20+ options.
[https://access.redhat.com/solutions/5644681](https://access.redhat.com/solutions/5644681) 

[https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale) explains how to do it on Ubuntu. I don't know if that applies to LXQt or not. Sorry. Maybe the lubuntu website and forums have more info?

This has been fixed for at least 6 months, so I have to ask, is the system currently supported AND fully patched?

---

### Post by ActionParsnip on 2022-03-03
or press CTRL + ALT + T to launch the terminal

---

### Post by GhX6GZMB on 2022-03-03
The OP already tried that. But OK, why read the thread?

---

### Post by guiverc on 2022-03-03
The thread is a little confusing; why Lubuntu is tagged still hasn't been explained by *Original Poster*. Wayland isn't yet supported on Lubuntu; as LXQt is Xorg.

If it was a Lubuntu 18.04 LTS or LXDE issue; that was upgraded to 20.04; there were numerous warnings that it would break which is why the upgrade was ***unsupported***. That **could** explain why Ctrl+Alt+T doesn't work.


if it's still LXDE on 20.04; it's a different system to prior releases as it's no longer configured by Lubuntu; ie. it's pure Debian LXDE from 18.10 and upwards so configs managed by Lubuntu up to 18.04 are no longer provided. However that's not Lubuntu (LXQt); again why is Lubuntu tagged?  LXDE is not Lubuntu (*and LXDE isn't capable of Wayland anyway*).


If ctrl+alt+T and menu options for terminal don't cause a GUI `gnome-terminal` (or other) to open; I'd check to ensure you python3 defaults are normal for your release; as both those CAN FAIL if default python3 has been changed; and this applies to main Ubuntu as well as *flavors* like Lubuntu. Many Ubuntu tools rely on the *default* python3.

---

### Post by #&amp;thj^% on 2022-03-03
> **guiverc said:**
> The thread is a little confusing; why Lubuntu is tagged still hasn't been explained by *Original Poster*. Wayland isn't yet supported on Lubuntu; as LXQt is Xorg.

+1
I think we should bring them in for questioning.:lolflag:

---

### Post by asai on 2022-03-04
> **1fallen said:**
> +1
I think we should bring them in for questioning.:lolflag:

Well, I'm sorry for the confusing tag in the post... This is a question for UBUNTU, not LUBUNTU.
Changed it now.

---

### Post by TheFu on 2022-03-04
The error says that a non-UTF8 character set is being used. gnome-terminal requires utf8 according to the link.  Check that your locale is set to use utf8 as links in #11 above say.

As you can see, providing correct details are very important.

---

### Post by asai on 2022-03-05
> **TheFu said:**
> The error says that a non-UTF8 character set is being used. gnome-terminal requires utf8 according to the link.  Check that your locale is set to use utf8 as links in #11 above say.

As you can see, providing correct details are very important.

Yes, I am very sorry for that. Problem solved. 
A bit embarrassed here now... :redface:
If I just had read the error properly, the problem would have been solved quickly...

Thank you all for the help. :)

---

