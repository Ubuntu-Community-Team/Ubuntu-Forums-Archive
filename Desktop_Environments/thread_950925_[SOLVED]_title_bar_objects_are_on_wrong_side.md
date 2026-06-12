---
title: "[SOLVED] title bar objects are on wrong side"
date: 2008-10-17
forum: Desktop Environments
---

### Post by decipher on 2008-10-17
Howdy all. :)
I've got a strange problem with my windows. It started when i stupidly decided to try out once of those max osx themes, which changed the placement of the title bar objects (the restore, min and max buttons are on the left, and the window icon + menu is on the right).
I've since reverted back to a previous theme, but the placement of the title bar objects are in the wrong place! (See attached)
I can't seem to find any obvious options that will allow me to correct this, can someone point me in the right direction?

---

### Post by sparky-steve on 2008-10-17
Hi,

Assuming you're using metacity:

you need to run gconf-editor, navigate to apps/metacity/general/button_layout and change it to:

menu:minimize,maximize,close

If memory serves, you'll need to restart the window manager, but that should do as you need.

---

### Post by decipher on 2008-10-17
Awesome sparky-steve! thanks alot, that's fixed it. :)
Gotta remember about gconf-editor, it seems very useful.

---

### Post by sparky-steve on 2008-10-17
Hey :-)

Glad it helped.....

:guitar:

PS: mark the thread as solved - it helps people in the future :-)

---

### Post by decipher on 2008-10-17
have done, will remember to in the future :)

---

### Post by Shazaam on 2008-10-18
gconf-editor is also in your main menu; usually under System Tools. It is called "Configuration Editor".

---

### Post by imana86 on 2008-10-18
Cool guestbook, interesting information... Keep it UP. excellent site i really like your stuff. ------ Bobby ([Hot Kicks](http://www.2345kicks.com)).

---

