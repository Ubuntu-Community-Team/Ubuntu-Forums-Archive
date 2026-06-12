---
title: "Evolution problem"
date: 2007-06-12
forum: Desktop Environments
---

### Post by Caligula on 2007-06-12
Hello everyone,
I've got a very weird problem with evolution, since it crashed, a few weeks ago, every time I open it it comes up with a dialog saying:

> Unable to connect to POP server tern.riseup.net.
Error sending username: 

Please enter the POP password for (my-user-name) on host tern.riseup.net
followed by a space to enter my password.

I need to click cancel, go back to online mode, and only then I can retrieve any emails, has anyone got any idea how to fix this?

Thanks

---

### Post by bapoumba on 2007-06-12
Did you check everything was correct in > Edit > Preferences > Edit your account > Identity & Receiving email tabs ?

---

### Post by Caligula on 2007-06-12
> **bapoumba said:**
> Did you check everything was correct in > Edit > Preferences > Edit your account > Identity & Receiving email tabs ?

Yes, it works in general, only on startup this notice appears... :(

---

### Post by bapoumba on 2007-06-12
Any error message when you start up evolution from a terminal ?

---

### Post by Caligula on 2007-06-12
> **bapoumba said:**
> Any error message when you start up evolution from a terminal ?

That's what my terminal shows:

> caligula@danarchy:~$ evolution
CalDAV Eplugin starting up ...

(evolution-2.10:27911): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:27911): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:27911): DEBUG: mailto URL command: evolution --component=mail %s
** (evolution-2.10:27911): DEBUG: mailto URL program: evolution


Thanks for helping me :)

---

### Post by bapoumba on 2007-06-12
I'm not using gnome. Can you find the menu where you say that evolution is your preferred mail application and see what command launches it ?

---

### Post by Caligula on 2007-06-12
what menu exactly do you mean?

the above happens with any command, either just "evolution" or the more specific "evolution --component=mail".

---

### Post by bapoumba on 2007-06-13
Should be a menu in Administration menu (Preferred applications). Is there a launcher associated to evolution (I'm on Xfce, I'll have to check with GNOME somehow)?

---

### Post by Caligula on 2007-06-13
Yes, there is one, and it's for the mail reader - evolution --component=mail %s

But the problem has mysteriously been solved! It just doesn't happen anymore :O

---

### Post by bapoumba on 2007-06-13
> **Caligula said:**
> Yes, there is one, and it's for the mail reader - evolution --component=mail %s

But the problem has mysteriously been solved! It just doesn't happen anymore :O
Okay, mystery then ^^
And upgrade ? A reboot ?

---

