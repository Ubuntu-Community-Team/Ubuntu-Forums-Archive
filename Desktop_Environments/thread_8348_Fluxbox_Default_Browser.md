---
title: "Fluxbox Default Browser"
date: 2004-12-16
forum: Desktop Environments
---

### Post by ThePrawn on 2004-12-16
Have been searching (forums and elsewhere) to little avail . . .  how do I (re)configure the default browser/mailreader/etc. in fluxbox?

---

### Post by jdong on 2004-12-16
Hmm, Flux really is a Window Manager, not a Desktop Environment... So it's not responsible for ensuring ANY interoperability between apps.

---

### Post by ThePrawn on 2004-12-16
. . . and it would be inappropriate to ask "Then how do I do it?" in this particular corner of the forums, eh? :-)

Thanks anyway.

---

### Post by Rancoras on 2004-12-16
[QUOTE=ThePrawn]. . . and it would be inappropriate to ask "Then how do I do it?" in this particular corner of the forums, eh? :-)

Thanks anyway.[/QUOTE]

Well, yeah, it's the right place.  After googling a bit, I see a lot of requests from users on adding the ability to do what you ask.  That tells me that it's currently not an option and, and jdong pointed out, it may never be.

---

### Post by ThePrawn on 2004-12-16
Gnome does allow you to edit your default browser/mail client/text editor and terminal -- but other than that [I'm] on my own.  I'm fine without a GUI for it, if I can just figure out how to do it manually -- a feat I've thus far had little luck with.

For now, I guess I'll fireup gnome, ensure the associations are correct, then skip back to fluxbox.

---

### Post by Rancoras on 2004-12-16
[QUOTE=ThePrawn]Gnome does allow you to edit your default browser/mail client/text editor and terminal -- [/QUOTE]

That's what jdong is saying, Flux is a window manager, and Gnome is a DE (desktop environment).  They do different things.

---

### Post by ThePrawn on 2004-12-16
. . . but can't these things essentially be done manually? I mean, aren't these GUI elements simply "easy" ways of altering configuration files here and there? Or in a "window manager" is there no way to, say, have a link clicked on in thunderbird open in firefox?

---

### Post by jdong on 2004-12-16
[QUOTE=ThePrawn]. . . but can't these things essentially be done manually? I mean, aren't these GUI elements simply "easy" ways of altering configuration files here and there? Or in a "window manager" is there no way to, say, have a link clicked on in thunderbird open in firefox?[/QUOTE]

Let's try saying this again:

A window manager **does not provide these services**. It's up to the individual program in question to make sure it launches the right program.

---

### Post by ThePrawn on 2004-12-16
Talking to myself here, I'm assuming ~/.mime.types.  I have a few questions along that vein, but I'll take them to more general forums, since it's not a desktop issue. . . Thanks, guys.

Edit: Jdong, I understand that much -- but the applications have to get their information somewhere, don't they?  All I know, is that by editing the default application in gnome, it now works correctly in Icewm, fluxbox and xfce --whereas previously, it did not . . .

---

