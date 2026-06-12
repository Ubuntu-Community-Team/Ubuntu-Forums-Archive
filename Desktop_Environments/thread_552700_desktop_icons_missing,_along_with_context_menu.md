---
title: "desktop icons missing, along with context menu"
date: 2007-09-16
forum: Desktop Environments
---

### Post by swiftor on 2007-09-16
after logging in none of my desktop icons appear, nor the context menu when i right click on the desktop. the wallpaper still draws, and when i open nautilus by going places -> desktop everything is listed and working. 

i have been okay with this for a while, but it has started to bug me lately. but since i have been working around it, i dont rember the last thing i did before this issue arose :( 

i have tryed putitng this command in "nautilus --no-default-window --sm-client-id default2 &" per [http://ubuntuforums.org/showthread.php?t=152677&highlight=desktop+icons+missing+context+menu](http://ubuntuforums.org/showthread.php?t=152677&highlight=desktop+icons+missing+context+menu) this thread, with no results... any help? :)

---

### Post by Happy_Man on 2007-09-16
Were you messing with Gconf? Go to Applications --> System Tools --> Configuration Editor, and then in there go to apps/nautilus/desktop/preferences/show_desktop and make sure that checkbox is selected.

---

### Post by swiftor on 2007-09-16
configuration editer is not in my system tools menu :(

---

### Post by Wolki on 2007-09-17
> **swiftor said:**
> configuration editer is not in my system tools menu :(

Ubuntu hides the configuration editor by default (a questionable decision if you ask me). To enable it, use the menu editor. You can also start it directly with "gconf-editor".

---

### Post by offchance on 2007-09-17
I had exactly the same problem (I thought it was a compiz update glitch, but it was a problem in metacity too). I ran gconf-editor, checked show desktop, and ctrl+alt+bksp to restart my session. the final result: I can now see all the text files stored on my desktop again. great advice, thanks!

---

### Post by swiftor on 2007-09-17
yep this solved it for me! i have no idea how that got unchecked, but that solved it.

thanks abunch!

---

