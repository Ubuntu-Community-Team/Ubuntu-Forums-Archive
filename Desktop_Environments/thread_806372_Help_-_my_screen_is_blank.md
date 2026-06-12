---
title: "Help - my screen is blank"
date: 2008-05-24
forum: Desktop Environments
---

### Post by MountainX on 2008-05-24
I had been working in Hardy with several applications open. A family member came along and switched to their user account for a little while. When finished, they clicked switch user and left the computer at the GDM login screen so I could log in and switch back to my session.

When I got back to the computer, the screen was a white-silverish color and blank. It has a mouse cursor, but nothing else.

I used ctrl-alt-F1 to switch to a virtual console and with top I see that all my processes are running. However, I cannot figure out how to get my gnome desktop back. Alt-F7 just returns me to the blank white screen.

I'm running compiz and nvidia restricted drivers. I do not want to use ctrl-del-backspace or reboot because I was in the middle of unsaved work when we switched users.

---

### Post by MountainX on 2008-05-24
bump

---

### Post by prshah on 2008-05-25
> **MountainX said:**
> 
I'm running compiz and nvidia restricted drivers. I do not want to use ctrl-del-backspace or reboot because I was in the middle of unsaved work when we switched users.

Try switching to metacity; maybe compiz got stuck? In the F1 virtual terminal ```
metacity --replace
``` This will replace compiz as the window manager, while at the same time not distrub gdm and/or running programs.

---

### Post by MountainX on 2008-05-25
when I ctrl-alt-F1 to a virtual terminal and run
```
metacity --replace
```
I get this error message:
```
Window manager error: unable to open X display
```
What should I try next?
Thanks

---

### Post by pixel :-) on 2008-05-25
Kill unimportant applications,maybe one of them blocks the hole thing

Somewhat far fetched.Set your computer to accept outside logins,and you log in your computer,with an other computer.I have no idea how to do this.

Can you close cleanly you precious applications with the terminal?Certain applications can accept commands of this kind

They are applications that do an autosave in regular intervals.

What application has the unsaved work?

This should teach you a lesson about managing your presions data.

---

### Post by MountainX on 2008-05-25
any other suggestions? How would I attempt to relogin to my desktop from a virtual console?

---

### Post by Nameless Neko on 2008-05-25
> **MountainX said:**
> I had been working in Hardy with several applications open. A family member came along and switched to their user account for a little while. When finished, they clicked switch user and left the computer at the GDM login screen so I could log in and switch back to my session.

When I got back to the computer, the screen was a white-silverish color and blank. It has a mouse cursor, but nothing else.

I used ctrl-alt-F1 to switch to a virtual console and with top I see that all my processes are running. However, I cannot figure out how to get my gnome desktop back. Alt-F7 just returns me to the blank white screen.

I'm running compiz and nvidia restricted drivers. I do not want to use ctrl-del-backspace or reboot because I was in the middle of unsaved work when we switched users.
I've had this same trouble in the past day or so actually.  If you move your mouse around you'll find a spot where you can enter text.  It's around the center of the screen for me.  If you enter your password there, it usually drops you back into the Gnome desktop.
Not sure what's causing this bug to be honest, but this seems to work most of the time for me.  I have had to reboot once or twice because of this, though.

Edit:  Don't think it's a compiz bug.  I'm not running compiz on my installation and I still get this bug when switching between the root account and my regular account.

---

### Post by MountainX on 2008-05-25
> **Nameless Neko said:**
> I've had this same trouble in the past day or so actually.  If you move your mouse around you'll find a spot where you can enter text.  It's around the center of the screen for me.  If you enter your password there, it usually drops you back into the Gnome desktop.
Not sure what's causing this bug to be honest, but this seems to work most of the time for me.  I have had to reboot once or twice because of this, though.

Edit:  Don't think it's a compiz bug.  I'm not running compiz on my installation and I still get this bug when switching between the root account and my regular account.

Thank you!!! This was the solution. Since we had used the "user switching" feature, I had to first type my username, then the password and like magic my whole desktop appeared with all my running apps and data!

This must be a bug in either the screen saver or the monitor power saving features. However, I have no idea how to report this bug.

---

### Post by MountainX on 2008-05-25
I reported it as a bug here: [https://bugs.launchpad.net/ubuntu/+bug/234824](https://bugs.launchpad.net/ubuntu/+bug/234824)

I would appreciate it if anyone else can help improve the bug report. I did the best I could.

---

### Post by Nameless Neko on 2008-05-25
> **MountainX said:**
> Thank you!!! This was the solution. Since we had used the "user switching" feature, I had to first type my username, then the password and like magic my whole desktop appeared with all my running apps and data!

This must be a bug in either the screen saver or the monitor power saving features. However, I have no idea how to report this bug.
Not sure.  I just disabled both to test, and still got the bug while switching.

---

### Post by MountainX on 2008-05-25
> **Nameless Neko said:**
> Not sure.  I just disabled both to test, and still got the bug while switching.

I don't see any error messages that would give a clue either. 

Are you also running Hardy? What video card are you using?

I'm running dual monitors. I assume you are using a single monitor, right?

---

### Post by Nameless Neko on 2008-05-25
> **MountainX said:**
> I don't see any error messages that would give a clue either. 

Are you also running Hardy? What video card are you using?

I'm running dual monitors. I assume you are using a single monitor, right?

Single monitor, using the nvidia restricted drivers with a Geforce 8600 GTS.  Perhaps it's an issue with the restricted drivers?  I'll have to do some tests with that and see if perhaps that's the issue.

Edit:  And yeah, I'm running Hardy right now, freshly installed yesterday.

---

