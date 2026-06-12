---
title: "Problem with gnome-terminal: Floating point exception"
date: 2011-05-27
forum: Desktop Environments
---

### Post by Stelian Andrei on 2011-05-27
Hello.

This is the first time I post a question on these forums and I'm sure there must be someone here that can help me.

My problem is as follows: I can't start gnome-terminal from the Applications->Accesories menu or from the Alt+F2 application launcher. I get a "Starting Terminal" in the task-bar that disappears after a few seconds and no terminal. I'm pretty sure there is something I did, but I can't really figure out what it is.

The things I've tried so far: 
1. I used synaptic to remove and reinstall gnome-terminal. That didn't work
2. Started Xterm and tried to run "gnome-terminal". This is where it gets weird for me: 
   a. running the command as normal user I get a "Floating point exception" error and obviosly no terminal
   b. when I do "sudo gnome-terminal" and enter the root password I get, as expected, a root terminal. I could live with that, but it's not ideal. 

So if anyone can help me figure this one out, I would really appreciate it. Thanks

---

### Post by Krytarik on 2011-05-27
Try restoring the defaults for bash by copying the content of "/etc/skel" into your home directory.

Greetings.

---

### Post by Stelian Andrei on 2011-05-28
Hi Krytarik.

I tried as you suggested. There are 3 files there (.bashrc, .bash_logout and .profile). I copied all in my home directory, overwriting the old ones. Logged out and back in, but no change. The "Floating point exception" still appears in xterm when trying to run gnome-terminal.

---

### Post by Krytarik on 2011-05-28
> **Stelian Andrei said:**
> The "Floating point exception" still appears in xterm when trying to run gnome-terminal.
Running gnome-terminal directly also still doesn't work?

---

### Post by Stelian Andrei on 2011-05-28
No, it still doesn't work. It's the same thing. Trying to run from Applcations menu displays a "Starting terminal" that disappears after a few seconds and running from the Alt+F2 shortcut does nothing, visible at least. And from xterm shows the error I talked about. Running "sudo gnome-terminal" still works

Is it possible to be caused by come software I installed? A few days ago I tried installing Google Sketch Up. When I found out they have no Ubuntu version I tried installing several CAD alternatives from the official repositories. But I removed them because they didn't do what I needed. Is there a way that one of those apps could cause the problem?

Right now I don't remember what apps I tried because I left my laptop at work and I won't know until Monday. I guess I can remember the name of the apps by then and I'll let you know

---

### Post by Krytarik on 2011-05-28
No, I don't think that the mentioned apps may have caused the issue.

Try resetting gnome-terminal's settings in Gconf the next time you get your hands on your laptop:
```
gconftool-2 --recursive-unset /apps/gnome-terminal
```

---

### Post by Stelian Andrei on 2011-05-30
Tried the command you gave me, but it didn't work. You put me on the right track though.

I started playing with gconf-editor and I managed to fix it. Apparently it was because I changed the fixed width font in the System->Preferences->Appearence menu from Monospace to Monaco and gnome-terminal was set to use system font. When I changed it back to Monospace, everything was OK.

Thanks for all the help

---

### Post by Krytarik on 2011-05-30
> **Stelian Andrei said:**
> Apparently it was because I changed the fixed width font in the System->Preferences->Appearence menu from Monospace to Monaco and gnome-terminal was set to use system font. When I changed it back to Monospace, everything was OK.
Hmm, unexpected! It seems like those font in particular is the issue, because I just tested some different fonts and it worked just fine, even with "Webdings". :P

Was "Monaco" installed by default (not at my system)?
If not, how did you install it?

Anyway, glad that you fixed it!

---

### Post by Stelian Andrei on 2011-05-31
No it wasn't installed by default. I got it from [here]("http://www.gringod.com/2006/02/24/return-of-monacottf/").

I also tried several other fornts and it seems to be working OK. Maybe it's because that font is TrueType or maybe because it's an older format. I don't know

---

### Post by kerub on 2012-05-09
I had the same problem. I had played the fonts settings with ubuntu-tweak. After, I have reset it to the default fonts but nothing is changed. Then, I installed myunity and run it. You will see the fonts tab and from there, click on the default settings. As result, gnome-terminal was started again. Problem was solved.

---

