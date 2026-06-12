---
title: "Clear KDE Drop Down Menus"
date: 2006-10-12
forum: Desktop Environments
---

### Post by PigCorpse on 2006-10-12
Hi!

Anyone know of a way to clear the recent files from those drop down menus? I'm referring to the kinds in save dialogs, etc. There is a drop down menu that saves your recently used filenames. It's filled with old stuff now so I'm trying to clear all of them.

Thanks!

---

### Post by wieman01 on 2006-10-13
Where are these drop-down menus again? Are you referring to the panel? Or the actual program menu?

If you're talking about the program menu, then you can edit it using the ControlCenter ("kcontrol" from terminal). There is a section that let's you configure your desktop & menu. Since I am not in front of my own computer, I can attach a screeshot only later today.

---

### Post by kerry_s on 2006-10-13
kmenu> settings/kcontrol> security&privacy> privacy

---

### Post by PigCorpse on 2006-10-13
I'll try that.

Basically, I mean something like:

1. Go to the place where you change your wallpaper.
2. Try to select a wallpaper from a file, it'll bring up a dialog.
3. There is a box for the filename.

That box will have your recent names saved.

---

### Post by wieman01 on 2006-10-13
Ok, got it.

1. Fire up "Konqueror" (file or Internet browser, does not matter).
2. Go to: Settings->Configure Konqueror->History Sidebar
3. Press "Clear History" & confirm.

That's it.

_**EDIT:**_
D@#! it... Have just deleted my own history...

---

### Post by PigCorpse on 2006-10-13
Nope, didn't work. I cleared everything, but the recent files are still there.

---

### Post by PigCorpse on 2006-10-13
Heh, sorry, my last post was a few seconds after your's lol.

And it didn't work.

---

### Post by wieman01 on 2006-10-13
> **PigCorpse said:**
> Heh, sorry, my last post was a few seconds after your's lol.

And it didn't work.
Beats me... Can't figure it out. You're right, the background image history won't disappear, nor does KControl have a menu or configuration tool.

---

### Post by PigCorpse on 2006-10-13
WAIT!!!!

I got it!

Well, I didn't solve my problem, but I know why it won't work.

It's because the particular dialog I was using was in the wallpaper for the login screen, which is only accessible as root, and clearing the history clears only the user's history.

---

### Post by wieman01 on 2006-10-13
Have you got it then?

---

### Post by PigCorpse on 2006-10-13
Nope, not yet. I'll try some other time.

Hmm, do you have any idea if these entries are stored in a file somewhere?

---

