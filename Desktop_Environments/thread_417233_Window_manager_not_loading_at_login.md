---
title: "Window manager not loading at login"
date: 2007-04-21
forum: Desktop Environments
---

### Post by Notclive on 2007-04-21
When I login the splash image stays for ages and only disappears if I click it. My startup applications take ages to load and any application I open doesn't have a border and titlebar. When I type metacity in the command line I get the normal window borders and it acts normally but get 'Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"' returned.

---

### Post by Kaladar on 2007-04-24
I have a similar issue. I'm running Ubuntu 7.04 (fresh install). It was fine for two or three days, but now, after logging in from GDM, The 'splash' goes away very quickly. I have gnome panels, but when I open an application, it has no titlebar, minimize, maximize, or close controls.

I do not get the .xsession-error about "toggle_shaded". I get an error that a theme file could not be found. I changed themes back to 'Human' and the error went away (after restarting X), but Metacity still did not load with Gnome.

Any ideas/suggestions?

I can get metacity back by simply typing "metacity", but I shouldn't 'have to' if you know what I mean.

**Edit** This seems to be isolated to 'my' login. If another user signs in, metacity seems to be fine.

---

### Post by firfin on 2007-04-27
> **Kaladar said:**
> I have a similar issue. I'm running Ubuntu 7.04 (fresh install). It was fine for two or three days, but now, after logging in from GDM, The 'splash' goes away very quickly. I have gnome panels, but when I open an application, it has no titlebar, minimize, maximize, or close controls.

Any ideas/suggestions?
Have you tried deleting you session information? That did the trick for me.
It's in ~/.gnome2/session

Good luck. I have no idea how or when this happens btw. Any more info on your part?

---

### Post by firfin on 2007-05-25
Removing the session file was only a temporary solution. A permanent one was found in en update of metacity.

---

### Post by loathsome on 2007-05-25
A workaround could also be to add *metacity --reload* in your startup session.

---

