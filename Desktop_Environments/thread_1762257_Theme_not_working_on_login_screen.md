---
title: "Theme not working on login screen?"
date: 2011-05-19
forum: Desktop Environments
---

### Post by Hamani on 2011-05-19
Hi guys. 

So I've downloaded and installed the 'Tropical' theme from here: [http://francois.vogelweith.com/](http://francois.vogelweith.com/)

Its working and I like it, but the effects haven't changed the login screen style or background. Its not big deal but its kind of annoying. Any idea's why it didn't change that too? Is there something specific you have to do other than just apply the theme?

I'm running Ubuntu 10.04.

Thanks for any help =]

- Ga.

---

### Post by mcduck on 2011-05-19
Any themes you set apply only to the user who sets the theme (makes sense, it's a multi-user system anyway, and of course every user might want to have their own themes and wallpapers etc).

If you wish to change the theme for the login screen, you have to do it as the user "gdm". And also the theme you use must be installed system-wide (in /usr/share/themes) and not just in your normal user's home.

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

---

### Post by Hamani on 2011-05-19
Ah, ok. I get it. Thanks for the good description of why it didn't work =] 

Got it sorted now, but after running the command there is now a universal access widget in the top panel. How do I remove this again?

Also, I've been playing around with the top panel, but is there a way to re-set it back to its defaults? 

Thanks again. 

- Ga.

---

### Post by mcduck on 2011-05-19
oh, sorry about that. I forgot the UAC icon thing. It's easy to solve, though, just go to Control Center->Keyboard and on the Accessibility-tab turn off the "Accessibility features can be toggled with keyboard shortcuts"-option.

(In case you got two UAC icons instead of one, the first one disappears when you follow the above instructions, then second one goes away on it's own if you log out and back again)


What comes to top panel settings, I suppose that depends on what settings you might have changed...

If it's just things you have changed in CompizConfig Settings Manager, then every setting there has a reset button (or you can run "unity --reset" to reset them all).

---

### Post by Hamani on 2011-05-19
Its actually gnome, not unity I'm using sorry. And I've done nothing as fancy as compiz, just added and removed some of the widgets. I managed to accidentally remove the shutdown, restart, etc ... button. I've replaced it but there were only two separate icons available and they don't produce the drop down menu like the original one.  

- Ga.

---

### Post by mcduck on 2011-05-19
Ah, classic Gnome.... In that case it's the "Indicator Applet Session" you'll want to add to the panel.

---

### Post by Hamani on 2011-05-19
Perfect!

Thanks for all the help dude!

- Ga.

---

