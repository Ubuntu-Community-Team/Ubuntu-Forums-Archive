---
title: "VNC Keyboard Problems"
date: 2005-04-15
forum: Desktop Environments
---

### Post by jasbur on 2005-04-15
Here's the setup. I have a file server setup in the other room running Ubuntu. When I connect from my OSX machine through VNC the keyboard doesn't quite work right. The letter keys work fine, but when I hit the left arrow I get a ~ backspace and enter are also regestered as key strokes, but they don't perform the proper action (i.e. delete the character or carriage return).

I do remember a message from gnome about the keyboard when I first logged in through VNC about the keyboard layout. I answered what I thought was appropriate, but appearently I was wrong.

Any Ideas?

---

### Post by roberTO on 2005-04-15
probe left ctrl+alt+your character.....

---

### Post by buxtor on 2005-05-04
Did you ever figure out this VNC issue?  I'm running into the same thing on fresh installs of Ubuntu 5.  Why is the key mapping all funny?

---

### Post by fortytwo on 2005-08-16
Here's another vote for the same problem...I'm guessing no one has figured this out yet?

---

### Post by erikdhansen on 2005-08-24
I'm seeing this same problem with remote X sessions instead of VNC.  I'm assuming it's a GNOME problem as I can log in to the X session at the GDM login fine, but once the session starts, all of my keyboard keys output the wrong characters.

---

### Post by kblood on 2005-08-24
Same problem here!! :(

---

### Post by fortytwo on 2005-08-24
[QUOTE=kblood]Same problem here!! :([/QUOTE]
 I can't say I have a solid solution, but I did get mine fixed.  For what it's worth, while signed in, I went into the keyboard properties and messed around with things a bit, trying different keyboards, etc, none of which made much difference.  But after a restart, things had magically been set correctly and the keyboard was working.

Not much help, I'm sure....but there's hope...try messing around a bit.

---

### Post by promet on 2005-08-31
I am having this problem as well, has anyone figured this out?

---

### Post by ::DoGG:: on 2005-11-30
Well, there is a workaround for this, when You reset keyboard setting to default in gnome (system-preferences-keyboard) and then restart vnc, everything wokrs ok. Try that one out.

---

