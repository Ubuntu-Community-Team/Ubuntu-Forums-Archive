---
title: "Starting apps from Terminal"
date: 2007-09-28
forum: Desktop Environments
---

### Post by johnjust on 2007-09-28
I'm running Kubuntu 7.04, but I don't think this is a KDE-only problem...

I took a Linux class this past fall, but, my how fast we forget...

I want to run programs from the Konsole, and my roommate told me to include the "&" at the end, so the Konsole isn't bound to the app, and it can be closed independently of the Konsole.

Problem is, let's say I run "firefox &".  I'm getting the "cannot connect to X Server" message.  Then, the Konsole hangs there, I have to ctrl+c to get out.  I should add that this is a brand new install of Kubuntu (I originally installed Ubuntu, then wanted to go back to KDE, so I installed Kubuntu on top, and had some problems here and there, so I reformatted and started fresh), and I'm wondering what the problem is.

I know there's a way to resolve it (I had a similar problem getting an install of FC5 to work the same way), and I'm sure I'll be kicking myself in the pants when I see how easy the solution is.

---

### Post by kshane on 2007-09-28
Sorry to say I don't have an answer for you.  I was just curious as to why you're starting gui apps from the terminal?

Kevin

---

### Post by johnjust on 2007-09-28
No reason imparticular, it's just something that should work, and I'd like to get it working correctly.  At the very least, so when I'm working in the Konsole, I don't have to use my touchpad to launch an app (I'm working from a laptop, touchpad sucks, not a lot of desk space for an external mouse)

---

### Post by Wolki on 2007-09-28
> **johnjust said:**
> I want to run programs from the Konsole, and my roommate told me to include the "&" at the end, so the Konsole isn't bound to the app, and it can be closed independently of the Konsole.

That's not exactly true. What the & does is execute the command in the background, so that you can still do other things in that terminal. If you close the terminal, the app is gone too.

> Problem is, let's say I run "firefox &".  I'm getting the "cannot connect to X Server" message.  Then, the Konsole hangs there, I have to ctrl+c to get out.  I should add that this is a brand new install of Kubuntu (I originally installed Ubuntu, then wanted to go back to KDE, so I installed Kubuntu on top, and had some problems here and there, so I reformatted and started fresh), and I'm wondering what the problem is.

Hm, that's odd. Are you doing it as your user or as superuser?

---

### Post by johnjust on 2007-09-28
> **Wolki said:**
> That's not exactly true. What the & does is execute the command in the background, so that you can still do other things in that terminal. If you close the terminal, the app is gone too.



Hm, that's odd. Are you doing it as your user or as superuser?

I've tried both regular and superuser, same errors.

EDIT: actually, looking back at my Konsole output, I was doing it as root the whole time.  1 exit, and it's all working now, thanks for that.  It's not the solution I thought it would be, but it's still a pretty dumbass mistake on my part

This is me kicking myself...

---

### Post by Wolki on 2007-09-28
> **johnjust said:**
> I've tried both regular and superuser, same errors.

What's the output of "echo $DISPLAY"?

---

### Post by kshane on 2007-09-28
> **johnjust said:**
> I'm running Kubuntu 7.04, but I don't think this is a KDE-only problem...

I took a Linux class this past fall, but, my how fast we forget...

I want to run programs from the Konsole, and my roommate told me to include the "&" at the end, so the Konsole isn't bound to the app, and it can be closed independently of the Konsole.

Problem is, let's say I run "firefox &".  I'm getting the "cannot connect to X Server" message.  Then, the Konsole hangs there, I have to ctrl+c to get out.  I should add that this is a brand new install of Kubuntu (I originally installed Ubuntu, then wanted to go back to KDE, so I installed Kubuntu on top, and had some problems here and there, so I reformatted and started fresh), and I'm wondering what the problem is.

I know there's a way to resolve it (I had a similar problem getting an install of FC5 to work the same way), and I'm sure I'll be kicking myself in the pants when I see how easy the solution is.

I just tried what your friend suggested:  I added the ampersand after the firefox command.  It did allow the terminal to return to the command prompt for me having also a new instance of Firefox, at which time I was free to enter a new command.  Perhaps it is a problem only with Konsole?  I am using Gnome...

---

### Post by johnjust on 2007-09-28
Woliki solved my problem, I was logged as root, that seems to be the problem.  I seem to remember editing a .conf file in the X11 directory to solve it, but this is working for me now.

---

### Post by mandrill on 2007-09-28
probably wrong thread, but installed bittorrent gui, no can find, any help?

---

