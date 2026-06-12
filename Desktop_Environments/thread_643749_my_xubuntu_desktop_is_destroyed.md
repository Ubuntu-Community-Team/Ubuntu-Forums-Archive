---
title: "my xubuntu desktop is destroyed"
date: 2007-12-18
forum: Desktop Environments
---

### Post by hygum on 2007-12-18
I installed xubuntu on harddisk with no probs. Everything worked well until i changed the display mode. Now when xubuntu starts the screen is f... up. I can only see some lines. The login screen is still ok, but there there's no option for changing the display mode before starting up. Is there a commanline utility i can use to go back the default in safe mode before starting up?

---

### Post by kpkeerthi on 2007-12-18
Can you explain a bit more as to what "display mode" means? Did you edit some file? What exactly did you change?

---

### Post by hygum on 2007-12-18
the change i made was in xubuntus normal gui for changing display mode, i changed display mode. i cant remember the name of the window, but its that little one, you get in the preferences menu. i cant remember what i changed it to, but it dodnt give any problems before restart. After restart the display mode is something the screen doesnt like.

if i start the window manager from safe mode with startx, it starts without probs though, but using that options result in a desktop where nothing works, no network and such, like many progs hasnt been started, only the window manager

---

### Post by Geistjaeger on 2007-12-19
Though not a perfect fix to the problem...mostly because I never found where the settings necessarily were so I could change them...

Here's what I did when I did the same to myself:

1. At the login, you can tell the system to login under a command line session.
2. Create a new administrative account for yourself.
3. Reboot or log out, and then re-login using the new account.
4. If your preference is to use the previous login name, you'll have to delete out the account, and then recreate it. 

Once you recreate the account, all previous settings will be gone which is the bad part, but the positive part is that the screen issues will be gone too...as everything is set to initial settings.

---

