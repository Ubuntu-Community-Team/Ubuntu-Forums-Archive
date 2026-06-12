---
title: "How to configure Awesome window manager?"
date: 2015-02-23
forum: Desktop Environments
---

### Post by prakash7 on 2015-02-23
Hello everybody,
             I wanted to use a minimal desktop hence I installed Awesome 3.5.6 which I assume is the latest version. I know you need to be geek to use a WM and not DE. I am a regular user but I want to use awesome so please help me out.
What are the exact steps to configure Awesome wm? I got links to themes: [https://github.com/Morley93/awesome-themes-3.5](https://github.com/Morley93/awesome-themes-3.5)

Please also inform me about the best file manager for awesome wm and any more tips/ tricks if you can. :p


Thank you.

---

### Post by Frogs Hair on 2015-02-23
Below is link that may be helpful.

 awesome.naquadah.org/wiki/Main_Page

---

### Post by prakash7 on 2015-02-23
> **Frogs Hair said:**
> Below is link that may be helpful.

 awesome.naquadah.org/wiki/Main_Page

Thanks for replying. I knew about the site and I checked it but it wasnt much useful.
On its configuration page, it says > **Files[[edit]("http://awesome.naquadah.org/w/index.php?title=Awesome_3_configuration&action=edit&section=2")]**


[LIST]
[*]~/.config/awesome/rc.lua
[*]/etc/xdg/awesome/rc.lua
[/LIST]
[COLOR=#000000][FONT=sans-serif]If awesome cannot find ~/.config/awesome/rc.lua, or fails to load it, it falls back to using /etc/xdg/awesome/rc.lua.[/FONT][/COLOR]

So which ru.lua should I edit or both? The first one? And if that fails to load should I edit the second file in xgd?
And what else I need to do? Just restart the wm or log out and log in? Is that it?

Sorry that I am asking rather than experimenting because I do not want to mess up my system. Hopefully we could make my awesome AWESOME. :p

---

### Post by oldos2er on 2015-02-23
Edit the one in your home folder (the first one listed). If you're the only user of your computer, you shouldn't need to edit /etc/xdg/awesome/rc.lua.

---

