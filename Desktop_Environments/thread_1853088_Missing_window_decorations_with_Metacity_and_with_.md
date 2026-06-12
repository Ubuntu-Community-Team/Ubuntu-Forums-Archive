---
title: "Missing window decorations with Metacity and with Compiz"
date: 2011-10-01
forum: Desktop Environments
---

### Post by gwi on 2011-10-01
Since a few weeks my window decorations are missing. Only my account is affected, two other accounts on the same machine are not affected.

Disabling compiz, reverting to metacity does not solve the problem. The only way to get the window decorations back is by running ```
metacity --replace &
``` or ```
compiz --replace &
```, but that has to be done after every login.

I cleared the directory ~/.gconf/apps/compiz, and copied the contents of the .gconf/apps/compiz directory of one of the not affected accounts into it. No change: after every login the window decorations are gone, keys like alt-F1, alt-tab are not working. (What do those keys have to do with window decorations?)

How can this problem be solved? (And with solved I don't mean putting ```
compiz --replace
``` in a place where it will be run automatically after login. That's not a solution, but a workaround.)

---

### Post by egeezer on 2011-10-01
If you have Emerald installed, window decorations are often lost.  You might try removing Emerald and see how it goes.

---

### Post by Copper Bezel on 2011-10-01
> I cleared the directory ~/.gconf/apps/compiz, and copied the contents of the .gconf/apps/compiz directory of one of the not affected accounts into it. No change: after every login the window decorations are gone, keys like alt-F1, alt-tab are not working. (What do those keys have to do with window decorations?)
Nothing, except that they're both provided by the window manager, which is breaking somehow at startup. You're looking in the right place - it's most certainly a gconf issue - but if resetting the keys for Compiz didn't help, and your default WM in gconf is Compiz, I wouldn't be certain what else to check. (On 10.10 - on 11.04 and later, there are three Compiz directories in gconf.)

---

### Post by gwi on 2011-10-02
> **egeezer said:**
> If you have Emerald installed, window decorations are often lost.  You might try removing Emerald and see how it goes.
Emerald is not installed.

---

### Post by gwi on 2011-10-02
> **Copper Bezel said:**
> Nothing, except that they're both provided by the window manager, which is breaking somehow at startup. You're looking in the right place - it's most certainly a gconf issue - but if resetting the keys for Compiz didn't help, and your default WM in gconf is Compiz, I wouldn't be certain what else to check. (On 10.10 - on 11.04 and later, there are three Compiz directories in gconf.)
I am having the same problem when I use Metacity. Does that point in a direction where I could search?

---

### Post by Copper Bezel on 2011-10-02
Well, as I said, it unfortunately points in the places you're already looking. = )

This is drastic, but have you tried logging out, logging into a tty, and using it to rename the whole .gconf directory so that it will be re-created when you log in? That way we can confirm that it is indeed a gconf setting, somewhere in there, causing the problem. (And then you can switch them back, of course.)

---

### Post by gwi on 2011-10-02
Well, drastic...
I tried it. My desktop returned to a default Ubuntu look, but still no window decorations, until I ran metacity --replace.
So it looks like it is not a gconf issue. But what else can it be?

---

### Post by Copper Bezel on 2011-10-02
I don't honestly know. You can change it back now, of course, if you haven't done.

Yeah, so it's not settings for Compiz, Metacity, or Gnome defaults, and yet it doesn't affect the other user accounts. Something else unique to your account is breaking the window manager on startup. Startup applications are separate from gconf - I'm drawing a blank at what else that's relevant might be.

Oh, by the way - is this 10.04 or 10.10?

---

### Post by gwi on 2011-10-02
I am at 10.10.
But the strange thing is that System - About Ubuntu says I am using 11.04. But I didn't upgrade to 11.04. And the update manager everytime remembers me that there is a release upgrade to 11.04 available.
Kernel is 2.6.35-30-generic x86_64.

---

### Post by Copper Bezel on 2011-10-02
Yeah, and that's a 10.10 kernel, so if you're not experiencing any problems with package management in general, you can probably ignore the "About Ubuntu" box.

In any case, since the software isn't broken and nuking gconf didn't solve the problem, I don't know what to suggest. This symptom is almost always caused by a .gconf problem. You could try doing the same trick with .local and .config/autostart (and these would be safe to rename from inside the GUI) to narrow down the possibilities.

---

### Post by gwi on 2011-10-02
Thanks for mentioning .local and .config/autostart. After renaming, and one by one unrenaming them, I found the cause:
In .local/share/applications is a file (among 30 other ones) called metacity.desktop. I don't know why it is there. There's also a compiz.desktop and a gnome-wm.desktop.
Here are the contents:
```
[Desktop Entry]
Exec=metacity
Hidden=true
Name=Metacity
NoDisplay=true
Type=Application
X-GNOME-Autostart-Notify=true
X-GNOME-Autostart-Phase=WindowManager
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Product=metacity
X-GNOME-Provides=windowmanager
X-GNOME-WMName=Metacity
X-GNOME-WMSettingsModule=metacity
X-GnomeWMSettingsLibrary=metacity
X-Ubuntu-Gettext-Domain=metacity
```

If I remove this file, the problem is gone.
So far I haven't discovered any side effects of removing the file.

Unfortunately the problem reappeared after switching back from metacity to compiz. After removing compiz.desktop, the problem was solved again.
I don't know what theses files are meant for, but I seem to be better off without them.

Thanks very much for your help (and for making me log on and off more times in an hour than I ever did before ;) )

---

### Post by Copper Bezel on 2011-10-02
Yeah, I know that awful process of closing things down, logging out, then waiting in suspense to see what godawful shape your session is going to come back in. Yuck.

In any case, very cool - I'm glad that worked, although I'm not certain what those files are for, either.

---

### Post by kelvinelk on 2011-11-27
Well, well - Thank you for posting this information. After a weekend of looking at various mis-information surrounding this problem. This is what I needed to fix up my partners account when other accounts were fine. 

I really can't thank you enough for enabling me to remove the awful hack of launching compiz as a startup application.

---

