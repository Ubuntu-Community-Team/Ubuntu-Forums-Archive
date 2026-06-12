---
title: "Disable Compiz by Default"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by gdi2k on 2007-11-09
[SOLVED - See **[here]("http://ubuntuforums.org/showthread?p=3770282")**]

I need to disable compiz by default when new users are created. I really like the effects, but it doesn't play nice with 3D games, and often makes OpenOffice go awry too. It's a shared PC with many new users being added, and it's a hassle to disable compiz for each one after account creation. 

Just removing the compiz package doesn't do anything (compiz still works). Removing compiz-core dusables it, but does not enable metacity, so no window manager. Reinstalling metacity after removing compiz-core doesn't solve the issue. 

Any ideas?

---

### Post by lpb331 on 2007-11-09
Did you try adding metacity to your startup programs?

---

### Post by gdi2k on 2007-11-09
This would work if I could find a way of adding it to all users sessions, and making it part of new users' sessions. Otherwise I'd have to do it all manually, which is just as bad as disabling compiz manually in the first place (through the Appearance dialog).

---

### Post by lpb331 on 2007-11-09
Yeah, that won't work. Would it be possible to make a script that starts metacity on startup, regardless of user? I'm not exactly sure where it would be put, but I would think that would be the way to go.

---

### Post by gdi2k on 2007-11-12
Anyone else any other ideas? Where does Ubuntu store its Gnome session defaults for new users? This issue is really driving me nutty - I can't believe it can be that hard to disable compiz by default. I'm sure there are plenty of corporate customers who will want to do this.

---

### Post by FuturePilot on 2007-11-12
Did you try System>Preferences>Appearance. Go to the Effects tab and select None.

---

### Post by gdi2k on 2007-11-12
Yes, and this works fine. My issue is that I need to disable it for newly created users. I'm running machines in a public space where new user accounts are created all day long, and it's a real hassle to disable it manually for each new user.

---

### Post by gdi2k on 2007-11-14
OK, I've found a default WM setting using gconf tool, but it's marked as deprecated since Gnome 2.12. How is the default window manager defined these days for Gnome? I looked for an "Appearance" or "Effects" section in gconf, but nothing is there. There are plenty of compiz and metacity settings, but they all relate to the window managers themselves, not which window manager should appear by default. 

If anyone has any ideas where I should look next, it would be greatly appreciated! This issue is causing me a bit of a headache; a lot of users who have never encountered Ubuntu (or Linux) before are facing embarrassing hangups and blank screens, which isn't a good first impression.

---

### Post by gdi2k on 2007-11-14
To complete the monologue, I've figured out a solution to this. In the hopes that it will help someone in the future, here's the solution: 

As root (sudo gedit), modify: /usr/share/gnome/default.session and change ```
0,RestartCommand=gnome-wm --sm-client-id default0
``` To:```
0,RestartCommand=gnome-wm --default-wm /usr/bin/metacity --sm-client-id default0
```

Also see the gnome-wm manual page, and have a read of the script. There are some issues with the script apparently [this bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/132772"). The theory is that by removing compiz from the system, the script is supposed to launch metacity in compiz's absence - that doesn't work though, as reported above.

---

