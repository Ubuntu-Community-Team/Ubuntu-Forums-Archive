---
title: "Possible Corruption with Gnome Shell/Unity"
date: 2013-02-18
forum: Desktop Environments
---

### Post by Sky93 on 2013-02-18
Hello all. I was attempting to install user themes for Gnome shell when the instructions told me to press 'alt+f2' then enter 'r' in the dialog. I followed, then everything disappeared except for my wallpaper, and never returned. I rebooted my computer via terminal, and everything started looking wonky. I no longer had the option to select unity from the theme menu at login, and everything just looked weird in general. Now, none of my gnome extensions work, my clock is stuck in 24 hour format, my icons on the top bar are broken, and I cannot access unity. 

I have some screenshots below. ANY help would be appreciated because I have no idea what happened

Note: I am connected to wifi in the screenshots

---

### Post by aarons6 on 2013-02-18
where did you put the themes..

gnome is kinda picky, putting them in ~/.themes doesnt always work..
you can put them in ~/.local/share/themes or better yet, make a link from ~/.local/share/themes to ~/.themes
seems some gtk apps need one and the system needs the other.. i dunno why.

also you can put them in /usr/share/themes for best results.
themes here you can use for the login screen too. if you use the gtk one.

---

### Post by Sky93 on 2013-02-18
I put them in /usr/share/themes at first but that didn't work, and then I moved them to ~/.themes and they showed up. But when I actually applied a them, everything got all wonky. Even when I returned everything back to the default theme they stayed wonky (i.e. 24 hour clock and weirdly colored top bar buttons) and that still doesn't explain why I now no longer have the option to select unity at log in.. /:

---

### Post by aarons6 on 2013-02-18
you didn't accidently move them to /.themes as root?

---

### Post by Sky93 on 2013-02-18
I'm pretty sure I didn't. And I just purged gnome-shell and everything is still messed up looking.

---

