---
title: "Transparency not working in mate-terminal"
date: 2016-09-17
forum: Desktop Environments
---

### Post by jwbrase on 2016-09-17
In preparation for switching my main desktop over, I upgraded my laptop from Ubuntu-Mate Trusty to Xenial. I have a setup where I use compiz window rules to overlay a transparent, borderless gnome-terminal window over my desktop background. This setup was originally put together under Jaunty before Gnome went south, and has so far used gnome-terminal. When Gnome fell apart and I switched to mate, I did not immediately give up gnome-terminal as, aside from not honoring my gtk2 system theme, gnome terminal was still in good shape, and mate-terminal did not have the patches applied that gnome-terminal has on Ubuntu for using mousewheel scroll in the terminal. In Xenial, that is no longer an issue for mate-terminal, and gnome-terminal has officially jumped the shark: It no longer allows you to set a Window title for a given profile, which means that I can't apply my compiz Window rules to a gnome-terminal instance, which means I will now have to switch over to mate-terminal. 

I've just run into one hiccup: mate-terminal, despite having a transparency setting in its profile options, does not appear under any circumstances to honor that setting. Most Google results for the problem suggest turning on compositing in marco/metacity/whatever, but I'm using compiz, and all of compiz's own transparency effects (such as trailfocus) are working just fine for mate-terminal windows.

Does anyone know what this issue is here?

---

