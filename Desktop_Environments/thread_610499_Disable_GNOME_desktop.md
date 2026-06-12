---
title: "Disable GNOME desktop"
date: 2007-11-12
forum: Desktop Environments
---

### Post by mopok on 2007-11-12
Hi everyone!
Well, I've got a pretty interesting question arised while digging into Gutsy in an effort to provide a comfortable and in the same time security solution for some special situation. I need to force some users after login into Gutsy box to use a special (Firefox indeed) application and not to be able to run anything else. I've managed to create a special skel folder for this users and to place there .config/autostart folder containing the script which starts firefox and logs user off the box when firefox is closed. But this solution cannot prevent users from running all other stuff. Then I understood I have to disable the GNOME desktop and panels to solve this issue. But I did not find out how. Please help.

---

### Post by ofb on 2007-11-12
I haven't done this but you might want to look at the Lockdown Editor (Pessulus) that comes with Edubuntu.

Other 2 cents from memory of another discussion was Opera's kiosk mode seemed to be better idea than Firefox. Opera, at that moment, had better features, and the Firefox version relied on extensions, which had the usual extension problem of breaking with upgrades.

Good luck with it.

---

### Post by mopok on 2007-11-12
Thanks ofb!
But it seems pessulus is, at first, graphicps mode tool, and, at second, I didn't find out, whether it can provide personalized settings for different users i.e. administrators have full options, but regular users dont. I need something like a script backend, I think, something like gnome-.... (I used gnome-session-save to force user logout).

---

### Post by mopok on 2007-11-12
Well, it seems I've found the GNOME component which is responsible for displaying toolbars and desktop icons very similar with the way windows explorer.exe does - it is gnome-panel... Any ideas how to configure GNOME not to load this component?

---

### Post by eye208 on 2007-11-12
All you need to do is put a script file ".Xsession" into a user's home folder. When the user logs in, the X session manager will execute this script. It will not do anything else, i.e. the GNOME/KDE window manager will not be started. This is ideal for kiosk systems where the user is supposed to work with only one application and nothing else. As soon as the user exits the application in the usual way, he will be logged out.

---

### Post by mopok on 2007-11-12
Thanks eye208! I was just going to describe this solution and found your description :)... There is even more comprehensive approach to this solution - use .xinitrc file together with .xsession file and placing both of them into user's skel folder...

---

