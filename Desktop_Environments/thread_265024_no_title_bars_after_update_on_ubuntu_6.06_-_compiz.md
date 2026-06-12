---
title: "no title bars after update on ubuntu 6.06 - compiz problem"
date: 2006-09-25
forum: Desktop Environments
---

### Post by Vlatko on 2006-09-25
i just updated my ubuntu and yet again i have no title bars, no top panel as well.
i don't know what to do, where to look nor what to look for. i'm confused with all these changes.

can someone help me out?

---

### Post by Vlatko on 2006-09-25
is something wrong with the forum? i posted the same thread an hour ago and couldn't find it anywhere so i made this one and i can't see it anywhere as well...

---

### Post by Vlatko on 2006-09-26
can anyone help out?
i had the same problem about 10 days ago when i had to edit the "/usr/local/bin/compiz-start" file with these instructions:

> CGWD is loading but your decorator settings are not, Compiz is going through a heavy developement process and gconf settings have been discontinued in the later builds so make sure your start script has been updated.

mine used to be:
"cgwd &
compiz --replace gconf &"

my new one looks like this

"cgwd &
compiz --replace dbus csm & "

The decorator comes back and everything should work.
Do not forget that all of your move, cube, decorator funtions are all plugins and if those are not intializing you will first believe that Compiz is not fuctioning when the truth of the matter is you need to make sure your plugins are loading.

that solved it for me back than but now i don't know what to do.

---

