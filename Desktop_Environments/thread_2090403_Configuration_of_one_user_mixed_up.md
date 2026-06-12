---
title: "Configuration of one user mixed up"
date: 2012-12-02
forum: Desktop Environments
---

### Post by Impavidus on 2012-12-02
I've a problem with running an xfce session on a desktop computer. All window decorations are gone, in the settings manager I can't change the settings of the window manager (clicking on window manager gives me an empty screen, with just the return, help and close buttons). In firefox the menu's are unusable. Clicking on the menu bar gives a menu, but as soon as the cursor moves onto the menu itself it disappears most of the time (sometimes it works). In some other programs the menus work fine. Also, for a different user everything is fine and there are no problems running a unity 2D session.

The solution might be to just reset some settings, but I haven't succeeded in that.

PS: Using ubuntu 12.04 32 bit

---

### Post by ajgreeny on 2012-12-02
Have you installed and enabled compiz?

That can remove all window decorations very easily, so if this is what you've done, just enable the "Window decoration" plugin using compizconfig-settings-manager, which you will possibly have to install first.

For the firefox problem it may need a new user profile in the ~/.mozilla folder, so try renaming the **~/.mozilla/firefox/x#x#x#x.default** folder as a backup **~/.mozilla/firefox/x#x#x#x.backup** and restart firefox; that may be all that's needed.

---

### Post by Impavidus on 2012-12-02
Compiz has been installed, compiz-settings-manager and compiz-plugins haven't. When I rename the firefox profile firefox doesn't start any more (complaning it cannot find a profile), when I rename the entire .mozilla directory firefox starts, creates a new .mozilla directory and still shows the problems I descibed.

Edit: Installing compizconfig-settings-manager + dependencies and enabling decorations had no effect, even after logging out and back in. Furthermore, it would be strange to have to install packages to repair something that still works for another user. The best thing would be resetting the defaults, getting nice settings is easy afterwards.

Edit 2: In some programs, like the evolution email composer or gedit, the text input cursor is invisible. However, in the test field for the keyboard setting it's present.

I'm thinking of copying the settings of my account, which works fine, to the other guys account, or just deleting everything and resetting the defaults, but I'm a bit worried that I'll destroy his email settings or leave some things in an inconsistent state. I'm not sure where all desktop environment related configurations are stored.

---

### Post by LewisTM on 2012-12-02
This sounds like a recurrent problem with the window manager (xfwm4).
See here
[http://ubuntuforums.org/archive/index.php/t-2002853.html](http://ubuntuforums.org/archive/index.php/t-2002853.html)

Cheers!

---

### Post by Impavidus on 2012-12-03
Thanks, that solved the problem.

Unfortunately I was too fast yesterday and in the process of resetting stuff I deleted some email settings. Lesson learned: make backups, even of faulty settings.

---

### Post by RobertoRecordo on 2012-12-04
> **Impavidus said:**
> Thanks, that solved the problem.

Unfortunately I was too fast yesterday and in the process of resetting stuff I deleted some email settings. Lesson learned: make backups, even of faulty settings.

I followed the posted link
[http://ubuntuforums.org/archive/index.php/t-2002853.html](http://ubuntuforums.org/archive/index.php/t-2002853.html)

and there is quite a bit of back and forth - exactly what solved your problem?

Unfortunately I was too stressed yesterday and didn't read your post carefully: I am having the same problem.

Not only are the minimize controls gone, and the menus messed up (arrowing allows access to menu) but even the "minimize all windows" widget at the bottom of the screen does nothing.

So what was it that solved your problem?

Rob

---

### Post by Impavidus on 2013-02-04
Oh, sorry I didn't reply to that one.

The solution was the command```
xfwm4 --replace
```

---

