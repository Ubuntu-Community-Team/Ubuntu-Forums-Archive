---
title: "Disable middle &amp; right click on trackpad"
date: 2022-04-20
forum: Desktop Environments
---

### Post by dwater on 2022-04-20
I keep accidentally closing tabs on Chrome when I try to select a tab...it seems to be that I do a 'middle click' on the trackpad, when I am trying to do a 'left click'.

Is there a way to disable the middle and right click emulation on the trackpad?

It's a Lenovo ThinkPad T480S, running imposh 21.10.

---

### Post by him610 on 2022-04-20
> Is there a way to disable the middle and right click emulation on the trackpad?
I don't know how to disable the emulated buttons; however I know how to disable the trackpad. When using a laptop, sometimes I would inadvertently cause some unintended action when my wrist, sleeve, or lazy finger dragged across the trackpad. I normally use a mouse anyway - not the trackpad, so I disable the trackpad.  I defined two aliases that I put into *~/.bash_aliases* file that disable/enable the trackpad.
```

alias trkoff='synclient TouchpadOff=1'
alias trkon='synclient TouchpadOff=0'

```
I intended to write a little program that would detect whenever a mouse was connected, but I never got around to it. Mental hurdle was just too much, or I just took the easy way out - probably both.

---

### Post by dwater on 2022-04-22
Thanks...yes, synclient seems to be the key, but I want to specifically disable the middle button emulation, so it stops me from accidentally closing chrome tabs. I can't quite see which of the options on synclient would do that :/

---

