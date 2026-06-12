---
title: "sound stoped working..."
date: 2005-12-21
forum: General Help
---

### Post by sijp on 2005-12-21
I don't know what caused this, but suddenly my laptop don't play any sound :(. I think I just loged in to KDE for a moment to check something, and when I came back to gnome, there was no sound for any user on any desktop...

I am using breezy, with the backports enabled on IBM t41 thinkpad.
the system acts as if there is sound, but plays nothing (neither through esd, alsa nor artsd).

running the ubuntu live-cd produces sound well.
additionally, this problem is not user-specific, it started to happen globally on my machine.

I could not find any log that has anything to do with alsa.
I would like to reconfigure alsa's configs  how can I do that ?

I probably missed something (it's late here), if I did, please ask for it...

edit: it's a 82801DB-ICH4 intel card.

Shlomi

---

### Post by sijp on 2005-12-22
solved...

there is nothing like a good night sleep to clear your mind and find the answers to all of your problems... :P

I googled more for it the first thing I woke up, and accidently found this thread:
[http://ubuntuforums.org/showthread.php?t=75694](http://ubuntuforums.org/showthread.php?t=75694)
I ran alsamixer, and noticed headphone was enabled (who enabled it? who? :)), I disabled it and everything came back to normal...

---

