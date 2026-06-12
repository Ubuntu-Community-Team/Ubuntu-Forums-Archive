---
title: "wierd alpha problem with &quot;battle for wesnoth&quot; and i assume xgl is causing it"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Choad on 2006-06-11
dapper 6.06 + radeon 9550 + xgl + compiz 

just tried to install battle for wesnoth from the dapper universe repo, and it all went fine, game loads etc. but all alpha effects seem to alpha straight through to whatever is behind it on the desktop.

you can see this here
[[IMG]http://img78.imageshack.us/img78/7645/screenshot10vi.th.png[/IMG]](http://img78.imageshack.us/my.php?image=screenshot10vi.png)

before i got that screen i tried grabbing it with gimp's built in window grabber and it came out perfectly!? how wierd. that can be seen here
[[IMG]http://img78.imageshack.us/img78/5290/screenshot27fa.th.png[/IMG]](http://img78.imageshack.us/my.php?image=screenshot27fa.png)

anyone got any ideas?

---

### Post by Choad on 2006-06-11
bump???

---

### Post by jimjawn on 2006-07-15
[http://www.wesnoth.org/forum/viewtopic.php?t=11388&highlight=xgl](http://www.wesnoth.org/forum/viewtopic.php?t=11388&highlight=xgl)

run XLIB_SKIP_ARGB_VISUALS=1 wesnoth on the command line.

---

