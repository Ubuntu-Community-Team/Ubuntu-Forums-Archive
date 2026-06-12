---
title: "'Places' panel menu item does not work"
date: 2009-10-19
forum: Desktop Environments
---

### Post by Redsandro on 2009-10-19
A small question for something annoying:
All the shortcuts in Places on the top panel from Ubuntu 9.04 are NOT working, except for 'computer'.

I think it happened after an upgrade or update, and it has been too annoying for too long. My shamefully bad solution would be to reinstall Ubuntu, but I really don't want to do that and loose all my settings.

So I hope it rings a bell for someone and can give me a solution that's more hassle-free. :)

---

### Post by Redsandro on 2009-10-31
Anyone? I just upgraded to Ubuntu 9.10 and still have the same problem. :(

---

### Post by lavadisco on 2009-11-27
Me too. I get a popup error whenever I try to click on any of the places with a folder icon:

```
Could not open location 'file:///home/username'. No application is registered as handling this file
```

---

### Post by JustinR on 2009-11-27
It looks like Nautilus (The file manager) isn't configured correctly - I'm not sure how to reconfigure it though.

Try going to the run application by hitting the keys, ALT+F2, then type:

"nautilus file:///home/[username]"

without the quotes, replace [username] with your username without the grouping symbols and it should open correctly.

---

### Post by lavadisco on 2009-11-27
It's not a problem for me to get to the home folder, as the "computer" shortcut in the places menu still works and is faster than opening the run prompt and typing a bunch of stuff. So hopefully somebody knows how to fix nautilus.

---

