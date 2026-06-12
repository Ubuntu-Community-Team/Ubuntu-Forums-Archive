---
title: "[SOLVED] No window manager (ubuntu unity)"
date: 2014-06-26
forum: Desktop Environments
---

### Post by user8583 on 2014-06-26
When I log in onto my account, no window manager appears. The top bar and left launcher are missing, as well as window decorations. I cannot move windows nor launch a terminal pressing Ctrl+Alt+T.

When I delete simulatneously the .cache, .config and .compiz folders, windows decoration appears again. However, this lasts until I log out and log in again.

This seems to be an account configuration problem as another account on the same computer is not affected by this problem.

I tried to reinstall unity and compiz, but it did not change much. I actually noticed that executing the following commands supposed to clear unity would kill window decorations if I summuned them back up by clearing the aforementionned folders:

```

sudo dconf reset -f /org/compiz/
setsid unity

```

I don't have any NVidia or AMD graphics cards, only an HD 4600 IGP.

 Any idea? Any help appreciated.

---

### Post by grumblebum2 on 2014-06-26
Reinstalling unity and compiz will do nothing if the problem is due to configs in your home folder.
As this appears to be the problem, why are you using **sudo**. 

If you can bring up a terminal, run....
```
dconf reset -f /org/compiz/ && setsid unity
```
Sometimes it may be necessary to run just **setsid unity** again.

If you can't bring up a terminal, switch to tty1 with ctrl+alt+F1, login and run...
```
DISPLAY=:0 dconf reset -f /org/compiz/
```

Then reboot with
```
sudo reboot
```

---

