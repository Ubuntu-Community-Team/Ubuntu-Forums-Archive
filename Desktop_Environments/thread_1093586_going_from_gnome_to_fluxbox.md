---
title: "going from gnome to fluxbox"
date: 2009-03-11
forum: Desktop Environments
---

### Post by powerplayground on 2009-03-11
alright so I switched over to fluxbox on my laptop. It works great except I can't get it to use thunar by default instead of nautilus, and it re-enables sounds for specific functions. (ie. clicking buttons, closing windows, errors, etc.)

---

### Post by kerry_s on 2009-03-11
i don't understand what you mean.
what do you have in your fluxbox startup?

---

### Post by powerplayground on 2009-03-11
well I don't need thunar on all the time, just when I'm browsing in my files. I just want stuff to automatically open with thunar instead of nautilus.

with the sound issue, I don't want any drum noises to play when I hit a button or get an error.

---

### Post by kerry_s on 2009-03-11
sounds like your using "nautilus" instead of "nautilus --no-desktop" so it's taking over everything, just change the launcher.
do you have gnome-settings-daemon in your startup? if so, remove it.
install lxappearance to set the settings.

---

### Post by pw_f100_220 on 2009-04-24
just installed jaunty and now fluxbox has mouse click sounds...gnome settings daemon is not in startup...how do you specifically nix the sounds?

---

### Post by cos4 on 2009-05-01
> **pw_f100_220 said:**
> just installed jaunty and now fluxbox has mouse click sounds...gnome settings daemon is not in startup...how do you specifically nix the sounds?

I've got the same problem and no clue how to solve it. If anyone has got a solution please let me know.


edit:I think I've found a solution. Run gconf-editor and go to 
desktop/gnome/sound and disable "event_sounds"

---

### Post by Anzan on 2009-05-01
I was going to say "run gconf-editor" but cos4 got it.

I have menu entries for it, gtkchtheme, and GNOME Control Centre, Update Manager and sudo synaptic to make getting to these things easy.

---

### Post by ve4cib on 2009-06-07
Sorry to drege up an old thread, but I just installed 9.04 today and I'm running into this exact same problem.

When I have the Gnome Settings Daemon running everything is great; I don't hear any obnoxious noises every time I click on a button.  But as soon as that process is killed the sounds are back.

I've opened up gconf editor and unchecked the event_sounds and input_feedback_sounds options, but the problem persists.

Does anyone have any other ideas?  (And no, simply leaving the gnome settings daemon is not an option.)

---

### Post by VampyrePrince on 2009-06-07
Is this error in just whatever file manager you're using, or in everything?

---

### Post by ve4cib on 2009-06-07
It's a problem with pretty much every GTK+ app (as far as I can tell).  Thunar is the biggest culprit, but the graphical printer manager does it as well, as do all pop-up/message/alert boxes (whatever you want to call those).

Since I have the sounds turned off in Gnome anyway I've simply purged the Ubuntu-Sounds package from my system.  It still feels like a hack, but I guess it works.  And it beats having to have gnome settngs daemon running while I'm using Fluxbox.

---

