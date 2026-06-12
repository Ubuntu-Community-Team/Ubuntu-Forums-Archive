---
title: "HELP - &quot;sticky&quot; fonts"
date: 2004-12-07
forum: Desktop Environments
---

### Post by kresten on 2004-12-07
Hi everyone!
I have ttttttttttttttttttttttthis reallyyyyyyyyyyyyyyyyyyyyyy annoying problem with what i call sticky fonts. Whenever I write the fonts seems to stick(see above). I have been experiencing the same problem with annother distro(suse 9.1) so I doubt the problem is exclusive to Ubuntu, but rather a general linux problem. Does anyone have a solution to this problem?


PS. I run Ubuntu on a Toshiba laptop satellite pro M30

---

### Post by burlap on 2004-12-07
Try Computer -> Desktop preferences -> Keyboard. You can set values for repeating keystrokes.

---

### Post by kresten on 2004-12-17
[QUOTE=kresten]Hi everyone!
I have ttttttttttttttttttttttthis reallyyyyyyyyyyyyyyyyyyyyyy annoying problem with what i call sticky fonts. Whenever I write the fonts seems to stick(see above). I have been experiencing the same problem with annother distro(suse 9.1) so I doubt the problem is exclusive to Ubuntu, but rather a general linux problem. Does anyone have a solution to this problem?


PS. I run Ubuntu on a Toshiba laptop satellite pro M30[/QUOTE]

OK I think I found the solution myself here is how

sudo emacs /etc/X11/XF86Config-4

and add a line:

Option "XkbDisable"

BUT AS STATED EARLIER I AM A TOTAL NOOB AND I DON*T KNOW IF IT IS SAFE
I FOUND THE SOLUTION AT

[http://imnes.tripod.com/gouge/satellite/#keystick](http://imnes.tripod.com/gouge/satellite/#keystick)

---

