---
title: "problem with gnome 3 shell"
date: 2011-12-25
forum: Desktop Environments
---

### Post by jackal_79 on 2011-12-25
iam using ubuntu 11.10 with gnome 3 shell.It was working fine from more than a month until today.The problem is like this:
It boots up fine.Iam able to open applications by pressing windows key.After i open any application the top bar disappears.If i open a browser it does not open in maximized mode and if i try to maximize either it shuts down or nothing happens.Now, after i open any app iam unable to use the windows key any more and even alt + tab of alt f2 doesn't work.i have to press ctrl + alt + f1 and reset lightgdm.And then the process continues.Now iam using gnome classic and it is working fine.
      Someone please suggest how to make gnome 3 work again.

---

### Post by cybergalvez on 2011-12-26
have you checked "looking glass" to see if you are getting any shell errors? if not try Alt-F2 and enter the command lg and check the errors tab

---

### Post by jackal_79 on 2011-12-26
> **cybergalvez said:**
> have you checked "looking glass" to see if you are getting any shell errors? if not try Alt-F2 and enter the command lg and check the errors tab

As i said earlier once the top panel disappears i won't be able to use alt + tab , Windows key as well as alt f2 also.

---

### Post by Spr0k3t on 2011-12-26
Post up a list of your extensions.  I'm getting the same problem from time to time.  Perhaps we can track down where the issue stems from.  Here's mine.

Dash Click Fix: [https://extensions.gnome.org/extension/67/](https://extensions.gnome.org/extension/67/)
Evil Status Icon Forever: [https://extensions.gnome.org/extension/99/](https://extensions.gnome.org/extension/99/)
Extend Left Box: [https://extensions.gnome.org/extension/51/](https://extensions.gnome.org/extension/51/)
Frippery Applications Menu: [https://extensions.gnome.org/extension/13/](https://extensions.gnome.org/extension/13/)
Frippery Bottom Panel: [https://extensions.gnome.org/extension/3/](https://extensions.gnome.org/extension/3/)
Frippery Move Clock: [https://extensions.gnome.org/extension/2/](https://extensions.gnome.org/extension/2/)
Frippery Shut Down Menu: [https://extensions.gnome.org/extension/14/](https://extensions.gnome.org/extension/14/)
Frippery Static Workspaces: [https://extensions.gnome.org/extension/12/](https://extensions.gnome.org/extension/12/)
Media Player Indicator: [https://extensions.gnome.org/extension/55/](https://extensions.gnome.org/extension/55/)
Power Alt-Tab: [https://extensions.gnome.org/extension/58/](https://extensions.gnome.org/extension/58/)
Presentation Mode: [https://extensions.gnome.org/extension/94/](https://extensions.gnome.org/extension/94/)
Remove Panel App Menu: [https://extensions.gnome.org/extension/32/](https://extensions.gnome.org/extension/32/)
WWWDOTORG Quick Launch: [https://extensions.gnome.org/extension/57/](https://extensions.gnome.org/extension/57/)

If there's one or more in common, it could be an issue with the extension.  This happens to me when my screen blanks (even though I have it set to never shut off in screen settings).

---

### Post by cybergalvez on 2011-12-26
log in with a different shell, like unity, and turn off all the extensions, then you can turn them on one at a time to see which is causing you issues

---

### Post by lolpenguin on 2011-12-26
> **cybergalvez said:**
> log in with a different shell, like unity, and turn off all the extensions, then you can turn them on one at a time to see which is causing you issues

Can't turn off extensions from another desktop environment. You'll have to delete the from /usr/share/gnome-shell/extensions/ or ~/.local/share/gnome-shell/extensions/.

---

### Post by cybergalvez on 2011-12-27
> **lolpenguin said:**
> Can't turn off extensions from another desktop environment. You'll have to delete the from /usr/share/gnome-shell/extensions/ or ~/.local/share/gnome-shell/extensions/.

True not the way I said to do it, but if you log in with a different shell, you can use dconf-editor you can edit the list of extensions under org.gnome.shell.enabled-extensions.  Then you can try turning them on again one at a time

---

