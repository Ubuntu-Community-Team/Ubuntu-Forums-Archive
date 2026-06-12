---
title: "How can I not shoot my leg off?"
date: 2005-04-21
forum: Desktop Environments
---

### Post by Molerat on 2005-04-21
Today I discovered CTRL+ALT+BACKSPACE.  The hard way.

I was hacking away in emacs and typing up a report in OpenOffice.  I was trying to figure out the key combination to decrease indent when I happenned to press the aforementioned key combination.  Just like that X was gone, along with my work!  I practice the "save early and often philosophy," but my window arrangemnt and concentration was lost.

My question to you:  how to disable this wonderfully destructive feature?  More importantly, are there other key combinations I should disable before I find it myself?

---

### Post by Buffalo Soldier on 2005-04-21
[http://ubuntuguide.org/#disablectrlaltdelconsole](http://ubuntuguide.org/#disablectrlaltdelconsole)

Hope the information on that link is what you're looking for. If not, please do tell.

---

### Post by Sam on 2005-04-21
Just add the DontZap option in your xorg.conf:

```
Section "Serverflags"
  Option "DontZap" "yes"
EndSection
```

---

### Post by Molerat on 2005-04-21
Buffalo Soldier, thanks for that link, but CTRL+ALT+DEL is forever burned into my consciousness.  It'll be a sad, sad day when I *accidentally* stumble on that one!

Sam, that did the trick, thank you.

Are there other destructive keyboard combinations I should be aware of (other than the function (FN) combinations on my laptop)?

---

### Post by Fab on 2005-04-21
[QUOTE=Molerat]Buffalo Soldier, thanks for that link, but CTRL+ALT+DEL is forever burned into my consciousness.  It'll be a sad, sad day when I *accidentally* stumble on that one!

Sam, that did the trick, thank you.

Are there other destructive keyboard combinations I should be aware of (other than the function (FN) combinations on my laptop)?[/QUOTE]
 not destructive, but to avoid  surprises:
alt+ctrl+f-keys switches to virtual consoles,  press ctrl+alt+f7 to go back  to your first session :)

---

### Post by Alexander Kirillov on 2005-04-21
[QUOTE=Molerat]Buffalo Soldier, thanks for that link, but CTRL+ALT+DEL is forever burned into my consciousness.  It'll be a sad, sad day when I *accidentally* stumble on that one!

Sam, that did the trick, thank you.

Are there other destructive keyboard combinations I should be aware of (other than the function (FN) combinations on my laptop)?[/QUOTE]
 Also: Ctrl-Alt-+, Ctrl-Alt--(on numeric keyboard) change X server modelines (resolution, etc); result is ugly.

---

