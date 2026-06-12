---
title: "Keyboard misbehaves in Evolution mail under Ubuntu 9.04"
date: 2009-06-24
forum: Desktop Environments
---

### Post by obform on 2009-06-24
A few days ago my keyboard started to act strangely in Evolution when I reply to mail or create new mail: the comma key acts as a backspace, and the a key produces no character. The keyboard works perfectly for the rest of my Gnome desktop and in all applications.

My only recent change was to switch my mail default from plain text to HTML (so I could insert links easily). Changing it back didn't solve the problem.

I have been using Evolution mail under Ubuntu for over a year with no complaints. The transition to Ubuntu 9.04 seemed to go smoothly.

I don't understand the function of the files in my .evolution directories well enough to tamper directly.

Can someone help?

Many thanks,
--obform

---

### Post by Joypiper on 2009-07-28
I have had similar troubles with Evolution under 9.04.

But, for me, even when creating a NEW email, the letter 'y' had the same effect as a backspace.

This is very annoying, and makes writing emails impossibly unreliable.

Any help on this?  What other info do you need to diagnose?

-Joypiper

---

### Post by Pawcatuck on 2009-07-28
I'm at my 8.04 desktop now, but could you go Edit | Preferences | Composer Preferences and tell us what the character set is? Unicode UTF-8 works great for me; maybe you ended up with an unexpected setting there.

---

### Post by obform on 2009-07-28
Please forgive me for not posting earlier; I found the answer late last week, and am indebted to Matthew Barnes's posts at [http://www.nabble.com/Configuring-keyboard-shortcuts-td22739866.html]("http://www.nabble.com/Configuring-keyboard-shortcuts-td22739866.html")

The problem was that I inadvertently created keyboard shortcuts by touching a key when I was mousing over a command.

Matthew Barnes wrote,

> Your shortcut changes will be stored in ~/.gnome2/accels/evolution.
Just delete the file to restore all the defaults.

Instead, I opened that file in gedit, found the line that referred to the misbehaving key, and deleted it.  All has been fine since.

He also wrote,

> I should also mention that for this to work, you need to have editable
menu shortcut keys enabled.  Assuming you're using GNOME, this setting
is in the "Appearance Preferences" app under the Interface tab.

Since my awkward fingers can't be trusted, I disabled it.

--obform

---

### Post by Joypiper on 2009-07-28
That was it.

Thanks, Obform.

-Joypiper

---

