---
title: "Issues with Fluxbox at 1024x600"
date: 2009-03-07
forum: Desktop Environments
---

### Post by nikki on 2009-03-07
Today I started using Fluxbox within Ubuntu on my eeePC which has a small resolution. Fluxbox seems to be working find, but every GTK app has a huge interface and huge fonts. Right now I am using Firefox for example. The fonts on web pages are fine, but in the interface for firefox, I have huge fonts and the menus are oversized. Some preference panes cover the entire screen.

So far I've tried editing my Fluxbox startup script to have lxappearance and when that didn't work I tried changing it to add gnome-settings-daemon, but I am having no luck.

Any other suggestions?

---

### Post by nikki on 2009-03-07
I ended up solving the issue. The problem was I was being dyslexic and didn't notice I was supposed to have an & symbol at the end of gnome-settings-daemon.

I also followed this blog post that completely fixed the issue further.
[http://devilzdriv3rpy.wordpress.com/2009/01/02/fluxboxgtkgnome-apps-look-weird/](http://devilzdriv3rpy.wordpress.com/2009/01/02/fluxboxgtkgnome-apps-look-weird/)

---

