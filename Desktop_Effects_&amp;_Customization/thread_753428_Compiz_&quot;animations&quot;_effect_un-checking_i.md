---
title: "Compiz &quot;animations&quot; effect un-checking itself?"
date: 2008-04-12
forum: Desktop Effects &amp; Customization
---

### Post by SomeGuyDude on 2008-04-12
Hey guys. I have Compiz rolling in Hardy pretty well, but I ran into a weird problem.

Abruptly, all my "animations" settings went away. Alla them. So I checked it out, and somehow the "animations" setting got un-checked. No big deal, I hit the little box. But as soon as I move my mouse away, it un-checks again. I literally CANNOT enable animations, the box de-selects itself. Everything else works fine.

What's going on?

---

### Post by caradeporra on 2008-04-14
Ok, just to make sure, have you tried restarting your pc?  that is rule number one, and it might sound stupid being as if you are running linux you probably are saying 'DUH'...but sometimes people try so many complicated solutions they forget the simple stuff.  If you have not restarted, do that first.

---

### Post by Zorael on 2008-04-14
You may want to migrate to a flat-file configuration backend.

Go into Preferences in ccsm, export your profile, change Backend to flat-file, import again.

Then try enabling your effects.



edit: As for restarting, remember that you can restart the graphical environment without restarting the whole system, with Ctrl+Alt+Backspace. Or just log out and in again.

---

### Post by SomeGuyDude on 2008-04-14
I "fixed" it, but I'm not sure what the problem was. I just uninstalled and then reinstalled. Still have no idea what the initial problem was, but at least I'm not having it now.

---

### Post by russo.mic on 2008-04-14
> **caradeporra said:**
> Ok, just to make sure, have you tried restarting your pc?  that is rule number one, and it might sound stupid being as if you are running linux you probably are saying 'DUH'...but sometimes people try so many complicated solutions they forget the simple stuff.  If you have not restarted, do that first.

Sounds like a windows solution.  Although in Windows sometimes that helps with those mystery problems,  I find that generally not effective in Linux.  Any opinions?

Russo

---

### Post by TheMemphisExperience on 2008-04-14
> **russo.mic said:**
> Sounds like a windows solution.  Although in Windows sometimes that helps with those mystery problems,  I find that generally not effective in Linux.  Any opinions?

Russo

Generally, I'd agree that it does solve some "mystery bugs" in Windows.  Probably something that shouldn't be running is "kind-of" running. Or the registry caught fire. 

In Linux, the log-out/log-in trick(or full restart) works as well. Though Ubuntu doesn't have that strange problem Vista does in which the menu bar's power options stop working. Sometimes things do break, though.

---

