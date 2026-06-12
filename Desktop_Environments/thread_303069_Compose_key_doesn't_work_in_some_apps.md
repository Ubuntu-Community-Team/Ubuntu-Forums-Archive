---
title: "Compose key doesn't work in some apps"
date: 2006-11-19
forum: Desktop Environments
---

### Post by Aber_Adrian on 2006-11-19
I'm using Kubuntu, Dapper Drake.

I have set up the compose key (right windows key); I tried two ways:

a .Xmodmap file with the line:

keycode 116 = Multi_key

And then adding the line

Option          "XkbOptions"    "compose:rwin"

to my xorg.conf file in the InputDevice section.

Both ways work, but they don't work in all applications. Specifically, they don't work in the SecondLife Linux client. That's a real shame, because the main use for me for SecondLife is practicing my languages!

I also tried activating them through the Setting - Regional & Accessibility -Keyboard Layout - Xkb Options menu, and setting "Compose Key Position" and "Right Win-key is Compose".

I had FC5 on this computer before, and it worked fine in SecondLife. The problem is, of course, I can't remember what I did in Fedora. 

Thanks for any help you can give,

Adrian

---

