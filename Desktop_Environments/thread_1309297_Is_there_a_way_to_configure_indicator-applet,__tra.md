---
title: "Is there a way to configure indicator-applet,  track popup from players are annoying"
date: 2009-11-01
forum: Desktop Environments
---

### Post by zubaran on 2009-11-01
Is there a way to configure indicator-applet, even by config. files I find infos about changing song track very disturbing. Guess what, it switched off OSD notifications in Exaile for what? To see the same messages from indicator-applet!?!

---

### Post by diskotek on 2009-11-10
bump :) i'm also looking for an answer. but as i see it's only for evolution & telepathy, pidgin. but there should be a configuring file...well,i'm looking for it since i screwed it and can not see evolution anymore on my indicator list

---

### Post by bashphoenux on 2010-03-03
see if this[ article]("http://superuser.com/questions/73200/remove-or-add-entry-in-indicator-applet-ubuntu-gnome") helps

---

### Post by OzzyFrank on 2010-05-04
Looking around, it seems that Indicator Applet is MASSIVELY unconfigurable. And the unfathomably-large spacing between indicators - which of course cannot be adjusted - certainly doesn't get my vote!

---

### Post by obscenic on 2010-05-10
YES! FINALLY FOUND SOME MINIMAL CUSTOMIZATION!

I had to dig this up because evolution just totally disappeared from the applet one day....

Head on over to /usr/share/indicators/messages/applications

In there you'll find the applications that are listed under the messages icon. You can add and remove them.  Each entry is a text file. The format is just 1 line, and the file should be named the same as the application ie "evolution".
Format: 

```
/usr/share/applications/evolution.desktop
```

etc... You can head on over to /usr/share/applications to check out the name of the application you're trying to add if you're trying to add one that disappeared.

---

