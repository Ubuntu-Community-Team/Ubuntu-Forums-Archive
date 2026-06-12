---
title: "Installing Programs..."
date: 2009-01-26
forum: General Help
---

### Post by ryezak on 2009-01-26
I installed Childsplay Educational game for my son with the synaptic.
It seemed to install normally but when I click on the shortcut in games it does nothing at all.

Any ideas?

How do I try run it with the terminal shell? or open any program from terminal shell.

thanks...nooby

---

### Post by adamlau on 2009-01-27
```
sudo apt-get purge childsplay && sudo -f install childsplay
```

---

### Post by mb_webguy on 2009-01-27
And you would most likely run it from the terminal by typing "childsplay".  Running GUI applications from the terminal is useful if you're having problems, since it will show error messages that are normally hidden.

---

