---
title: "Making a program run with a specific GTK2 theme"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Kaiko36 on 2006-10-03
I was trying to get firefox to run with a certain GTK2 theme but it's not working.
I was wondering if anyone has had some success with this and how they did it.
I have instructions to do this:

3. Add this command to the Gnome Sessions "Startup Programs" (gnome-session-properties):
export GTK2_RC_FILES=~/.themes/Neutronium-FF/gtk-2.0/gtkrc firefox
4. Restart Gnome.

But of course that didn't work. SO I put it in my .gnomerc file 
but to no avail I cannot get firefox to use this theme. 
I'm using a darak theme that doesn't work well with firefox so I have
a better one that I want firefox to use to make text more readable.
Any suggestions??

---

### Post by orb9220 on 2006-10-03
You cannot have firefox or any app use one theme then have gnome desktop a different theme.

If default firefox theme is not to your liking then go here to install firefox theme [https://addons.mozilla.org/firefox/themes/](https://addons.mozilla.org/firefox/themes/) But the windows decorations which is the bar,minimize,maximize,close buttons is a desktop wide change to all.

You can't even do that in windowsXP with styleXP or Windowblinds.

---

### Post by RRS on 2006-10-04
You can use the Menu-X extension in Firefox to hide the gnome panels.

---

