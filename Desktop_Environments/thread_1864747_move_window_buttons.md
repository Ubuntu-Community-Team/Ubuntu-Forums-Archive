---
title: "move window buttons"
date: 2011-10-19
forum: Desktop Environments
---

### Post by sderrick on 2011-10-19
Ubuntu 11.10

I moved my window buttons from the left to the right side using gconf-editor.  Changing the apps/metacity/general setting to :minimize,maximize,close

I wanted to move them back so I changed it back to close,maximize,minimize:

But they won't move back!  They are still in the right side?

Whats with that?

---

### Post by Bao2 on 2011-10-19
apps/metacity/general/button_layout I checked and it is set to:

close,minimize,maximize:

(you inverted the two at the end, perhaps that affects?)

---

### Post by sderrick on 2011-10-19
> **Bao2 said:**
> apps/metacity/general/button_layout I checked and it is set to:

close,minimize,maximize:

(you inverted the two at the end, perhaps that affects?)

Wouldn't that be nice!   The point is you can put what buttons you want in in what ever order you want! I changed it just in case it was that lame, but they are still on the right.

I also ran Unity --reset to no avail.

---

### Post by pgrim91 on 2011-10-24
You still have the colon ":" in there which differentiates between buttons on the left and right.  I believe the correct string is (without the quotes) "close,minimize,maximize"

Or at least thats what worked for me, hope it works for you

---

### Post by Copper Bezel on 2011-10-24
No, the colon refers to the title text. It comes last if you want the buttons on the left. That string is right and should have worked.

---

### Post by martinr on 2011-10-24
Try restarting X to make your new settings effective.

The more graceful way to do it is:
```
Alt Gr+SysRq+K
```

(First close all your windows to prevent losing your work.)

---

### Post by sderrick on 2011-10-24
> **martinr said:**
> Try restarting X to make your new settings effective.

The more graceful way to do it is:
```
Alt Gr+SysRq+K
```

(First close all your windows to prevent losing your work.)

Come-on! I've probably powered cycled 20 times since I made the change!  I think X has been restarted!

---

### Post by nicentral on 2012-01-25
> **sderrick said:**
> Come-on! I've probably powered cycled 20 times since I made the change!  I think X has been restarted!

I too was just fighting with this.  The exact command I issued was:
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"

It didn't seem to work at first, but then miraculously it did.  I didn't even have to restart X.

---

