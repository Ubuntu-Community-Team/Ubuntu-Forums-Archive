---
title: "Problem with login after using compiz config"
date: 2009-01-25
forum: General Help
---

### Post by Clavera on 2009-01-25
Hello!

I have a problem with logging in. I'm currently using an Eee PC 1000H.

I installed Compiz Config and tried to enable some effect (I don't remember the name) and it came up a box that said it would be bad if I enabled that effect because of some other effect that was enabled at that time, so I choosed not to use that effect.

Then everything turned black for a second, and then the screen was filled with black and purple lines all over for two seconds, then it took me to the log-in screen, and whenever I try to log in, the purple and black lines come up and then im back at the log-in screen again. I have also tried to log in with the safe gnome login, but the same thing happens there.

What can I do to make things normal again?

---

### Post by Sam Lars on 2009-01-25
If you chose not to enable it, I don't know why this happened...

If you kill the X server with Ctrl+Alt+Backspace enough times right after another, it will get the idea that there's a problem and ask if you want to start in low graphics mode.  This is what you want.  It should let you log in and change some Compiz settings.

Another option you could try:
Ctrl+Alt+F1, log in, and do
```
sudo aptitude purge compiz
sudo aptitude install compiz
```
That will remove Compiz and its settings, and then reinstall it with the defaults.  We hope.

---

### Post by Wartender on 2009-01-25
wait, before purging compiz, what plugin did you enable? because if it was the magnifier, i have a solution, as the same happens to me on my mom's laptop.
try this: log onto failsafe terminal and type: ```
key="gconftool-2 /apps/compiz/general/allscreens/options/active_plugins" ; $key -s -t string $($key -g | sed -e 's/,mag//g')
```
(if it' wasn't magnifier you can try replacing mag with the name of the plugin)

---

### Post by Clavera on 2009-01-26
> **Wartender said:**
> wait, before purging compiz, what plugin did you enable? because if it was the magnifier, i have a solution, as the same happens to me on my mom's laptop.
try this: log onto failsafe terminal and type: ```
key="gconftool-2 /apps/compiz/general/allscreens/options/active_plugins" ; $key -s -t string $($key -g | sed -e 's/,mag//g')
```
(if it' wasn't magnifier you can try replacing mag with the name of the plugin)

Thank you, but the only thing the terminal tells me when trying this is:

```

No value set for `/apps[...]active-plugins'
No value to set for key `/apps[...]active-plugins'
```

:/

---

### Post by Clavera on 2009-01-26
> **Sam Lars said:**
> If you chose not to enable it, I don't know why this happened...

If you kill the X server with Ctrl+Alt+Backspace enough times right after another, it will get the idea that there's a problem and ask if you want to start in low graphics mode.  This is what you want.  It should let you log in and change some Compiz settings.

Another option you could try:
Ctrl+Alt+F1, log in, and do
```
sudo aptitude purge compiz
sudo aptitude install compiz
```
That will remove Compiz and its settings, and then reinstall it with the defaults.  We hope.

Thank you, but nothing happens after this, things is still the same.

Low graphics mode with CTRL+ALT+BackSpace did not work either... Sucks that I don't have an external dvd-rom right now as the Eee PC doesent have one so I can't just install ubuntu over again.

---

### Post by nelskurian on 2009-03-17
> **Wartender said:**
> wait, before purging compiz, what plugin did you enable? because if it was the magnifier, i have a solution, as the same happens to me on my mom's laptop.
try this: log onto failsafe terminal and type: ```
key="gconftool-2 /apps/compiz/general/allscreens/options/active_plugins" ; $key -s -t string $($key -g | sed -e 's/,mag//g')
```
(if it' wasn't magnifier you can try replacing mag with the name of the plugin)

i was in total confusion what to do..after getting the login error...You give me the cool idea..wherever their is trouble,their is someone always to help me...Thanks buddy..thanks a lot..:popcorn:

---

