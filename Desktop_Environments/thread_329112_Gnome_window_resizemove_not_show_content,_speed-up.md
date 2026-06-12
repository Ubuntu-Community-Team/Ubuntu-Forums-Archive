---
title: "Gnome window resize/move not show content, speed-up?"
date: 2007-01-01
forum: Desktop Environments
---

### Post by weird7192 on 2007-01-01
Hi,

I'm running dapper drake with the default gnome window manager, is there somewhere to switch the window resizing/moving eye-candy off? The equivalent in MS Windows of unchecking the 'Show window content while dragging' option?

I'd just like a more responsive system and I don't need this particular eye-candy, but I can't find any place to do this. Don't mind editing config files if needs be as I'm familiar with doing that (in Slackware, in CLI, with vim, god it was soo tedious ;)  )


Cheers

And Happy new year to all

---

### Post by weird7192 on 2007-01-01
I've figured it out, for the record:

Ubuntu 6.06 (dapper drake), Gnome 2.14.3

Use gconf-editor (in Terminal, or if you un-hide it using the menu editor, it's the Configuration Editor under Applications --> System Tools),

set &#8220;/apps/metacity/general/reduced_resources&#8221; to true



Cheers

---

### Post by NoobieDoobieDo on 2008-05-07
Worked like a charm in 8.04 as well, didn't even have to restart Gnome.

Thanks

---

