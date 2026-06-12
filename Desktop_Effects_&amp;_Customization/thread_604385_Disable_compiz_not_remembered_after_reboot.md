---
title: "Disable compiz not remembered after reboot"
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by janhurst on 2007-11-06
Hi,

I use wine to play warcraft. there is a bug post 0.9.45 which stops warcraft from connecting to battlenet. wine 0.9.45 doesn't do window hints or something correctly which means when compiz is enabled gnomes panels are on top of the warcraft/wine window

to get around this i disable compiz from gl desktop preferences. of note, gl desktop preferences NEVER loads first time, i have to run it twice for it to pop up. once i disable compiz i can happily play my game.

unfortunately, when i reboot, this change is not remembered.... and i have to go through the annoying process of running gl desktop preferences twice to disable compiz again

can anyone help!!!!!

jan

---

### Post by sergm on 2007-11-06
you may try killing compiz, then running metacity& from terminal and after that save your session. (Preferences->Sessions)
it should be ok after reboot.

---

### Post by frodon on 2007-11-06
Open Gconf editor and check the "desktop > gnome > application > window_manager > current" and "desktop > gnome > application > window_manager > default" keys, they might not be up to date.
Once this checked just save your session (you can use the gnome-session-save command for this).

---

### Post by janhurst on 2007-11-08
what should the keys be?

---

### Post by frodon on 2007-11-08
It should be "/usr/bin/metacity".

---

### Post by Forlong on 2007-11-08
If you're on Gutsy: do not use GL Desktop.
Use *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects* instead.
That's the only GUI that can handle the startup preferences for Compiz on Gutsy properly.

---

### Post by frodon on 2007-11-08
> **Forlong said:**
> That's the only GUI that can handle the startup preferences for Compiz on Gutsy properly.I have fill a bug report about it because it seems that it don't work properly in some cases and don't update the needed gconf keys which are used to save the session.
This is the reason of my question.

---

### Post by Forlong on 2007-11-08
> **frodon said:**
> I have fill a bug report about it because it seems that it don't work properly in some cases and don't update the needed gconf keys which are used to save the session.
Are you talking about *GL Desktop* or *Visual Effects*?
In all the time I'm doing support here, in the CF forums and the german Ubuntu community I have never encountered a person who had problems with the gconf key not being set up properly.

In most cases it's an upgrade issue (where people had Compiz or Beryl in their autostart) or an issue with *GL Desktop*.

---

### Post by frodon on 2007-11-09
> **Forlong said:**
> Are you talking about *GL Desktop* or *Visual Effects*?
In all the time I'm doing support here, in the CF forums and the german Ubuntu community I have never encountered a person who had problems with the gconf key not being set up properly.I do have, if i change my WM and use gnome-session-save the modification is not taken in consideration because the Gconf key is not updated.

---

### Post by Forlong on 2007-11-09
Yeah well... the whole thing is just not designed for users that change WMs themselves, I guess.

---

### Post by frodon on 2007-11-09
It's my guess too and it's why i filled a bug report as i think this can be really easily fixed.

---

