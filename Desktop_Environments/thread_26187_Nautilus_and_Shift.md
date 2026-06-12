---
title: "Nautilus and Shift"
date: 2005-04-12
forum: Desktop Environments
---

### Post by ankitmalik on 2005-04-12
Hi

Actually call it personal tastes but I hate a new window opening for each folder I click @... I like the spatial view but I dont like tens of folders opened up..

I know I can use SHIFT so that the previous window closes when the new window opens ...but how do I set this as default

I am using Ubuntu HH PR...

---

### Post by heimo on 2005-04-12
run gconf-editor (sudo gconf-editor) and enable setting:
/apps/nautilus/preferences/always_use_browser

I haven't tried it, so I don't know if this works.

Just found this:
Nautilus -> edit -> preferences -> behaviour -> always open in browser windows
[http://www.ubuntuforums.org/showthread.php?t=26140](http://www.ubuntuforums.org/showthread.php?t=26140)

---

### Post by ankitmalik on 2005-04-12
[QUOTE=heimo]run gconf-editor (sudo gconf-editor) and enable setting:
/apps/nautilus/preferences/always_use_browser

I haven't tried it, so I don't know if this works.

Just found this:
Nautilus -> edit -> preferences -> behaviour -> always open in browser windows
[http://www.ubuntuforums.org/showthread.php?t=26140](http://www.ubuntuforums.org/showthread.php?t=26140)[/QUOTE]
 nope...that brings me to nonspatial view :(

but apt-get install nautilus did the trick

---

### Post by burlap on 2005-04-12
I know you solved it, but for the future: there is an option in gconf (apps->nautilus->preferences) "no ubuntu spatial" - when it's checked, default Nautilus behavior is back. 

However, "ubuntu spatial" actually doesn't work for me - I mean no shift or middle click works, but folders open new windows anyway...

---

### Post by heimo on 2005-04-12
Oh, I misread your question. What you wanted is original Gnome spatial... not the Ubuntu "close parent" spatial. 'no_ubuntu_spatial' setting somewhere... :) I'm going to do the same thing when I get back to my computer.

EDIT: burlap was fast! :) Thanks!

---

### Post by ankitmalik on 2005-04-12
[QUOTE=burlap]I know you solved it, but for the future: there is an option in gconf (apps->nautilus->preferences) "no ubuntu spatial" - when it's checked, default Nautilus behavior is back. 

However, "ubuntu spatial" actually doesn't work for me - I mean no shift or middle click works, but folders open new windows anyway...[/QUOTE]
 thanks :-)

---

