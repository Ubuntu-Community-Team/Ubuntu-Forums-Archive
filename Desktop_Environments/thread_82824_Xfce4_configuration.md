---
title: "Xfce4 configuration"
date: 2005-10-27
forum: Desktop Environments
---

### Post by zarathustra on 2005-10-27
How do I configure the default apps for it? I have Epiphany installed and Firefox 1.5 beta, but the latter one in a custom place. It treats Epiphany as the default browser in some applications, and I'd like to change it.

---

### Post by aysiu on 2005-10-29
Which applications treat Epiphany as the default? I'm wondering, too, if maybe changing the default browser in Gnome somehow affects the default browser in XFCE?

You also mentioned that Firefox 1.5 is in a "custom place." Does it have a symlink to /usr/bin, too?

---

### Post by unclben on 2006-01-26
Time to bump this old thread. I want XFCE to treat Fx (1.0.7) as my default browser, instead of Epiphany. Fx thinks that it is default, but whenever I click a link in a non-Fx app, the web page opens in Epiphany.

---

### Post by kaamos on 2006-01-26
I think xfce uses the sensible-browser script. So if you want to use ff:
```
export BROWSER=/usr/bin/mozilla-firefox
```
Now ff should open with "sensible-browser" if you are still on the same terminal.

If you wish to make this permanent, I think adding the above line to the end of /home/username/.bashrc and /home/username/bash_profile could work. You might have to log out before it takes effect..

Hope this works!

---

### Post by unclben on 2006-01-28
[QUOTE=kaamos]I think xfce uses the sensible-browser script. So if you want to use ff:
```
export BROWSER=/usr/bin/mozilla-firefox
```
Now ff should open with "sensible-browser" if you are still on the same terminal.

If you wish to make this permanent, I think adding the above line to the end of /home/username/.bashrc and /home/username/bash_profile could work. You might have to log out before it takes effect..

Hope this works![/QUOTE] XFCE does use sensible-browser, and your terminal command worked exactly as you said it would. As far as making the change permanent ... Is there any way to manually tell sensible-browser which app /I/ consider to be the 'sensible browser'? I'd rather fix the problem at the source than use the hack* of overriding the default at every session start.

*Note that I don't mean hacks are bad ... just 'impure', if you will. I am an OCD sort of fellow, so it pleases me to use 'cleaner' solutions in situations like this. Regardless, your help is greatly appreciated. :)

---

