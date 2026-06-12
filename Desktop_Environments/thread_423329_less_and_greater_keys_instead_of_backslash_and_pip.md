---
title: "less and greater keys instead of backslash and pipe (US keyboard)"
date: 2007-04-25
forum: Desktop Environments
---

### Post by beaudoin996 on 2007-04-25
I have a 104 keys PS2 keyboard with the US layout.  Here is a link to the manufacturer 

[http://www.labtec.com/index.cfm/gear/details/AMR/EN,crid=28,contentid=706]("http://www.labtec.com/index.cfm/gear/details/AMR/EN,crid=28,contentid=706")

My problem is that everything is working fine except the backslash (\) and pipe (|) key.  When I press it shows a less sign (<) and with shift, a greater sign (>). In the keyboard config I choose "PC generic 104 keys" with the "English US" layout.

Does someone know how to change the keyboard mapping manually ?
Does someone have the same problem ?

---

### Post by beaudoin996 on 2007-04-25
I found a solution

$ xmodmap -pke > ~/xmodmap.conf

I edited the files and at the line with keycode 51, I replaced "less" with "backslash" and "greater" with "bar"

Then

$ xmodmap ~/xmodmap.conf

---

