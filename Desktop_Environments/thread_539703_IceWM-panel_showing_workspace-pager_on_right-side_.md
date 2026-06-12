---
title: "IceWM-panel showing workspace-pager on right-side option - WEIRD RESULT!"
date: 2007-08-31
forum: Desktop Environments
---

### Post by jdackle on 2007-08-31
Ok, so I set the IceWM's pnael workspace-switcher to appear on the right side instead of the default left. That is I want it to appear right of the taskbar and left of the clock and hide-panel button, instead of next to the menu as is the default IceWM behaviour.

So I edited the ~/.icewm/preferences file as thus:
```
#  Place workspace pager on left, not right
TaskBarWorkspacesLeft=0 # 0/1
```

So now the pager does appear on the right-side of the panel, only on the farthest right, right of the clock and hide-button! (see attached pic)

How can I fix this?

Thanks in advance :)

---

### Post by jdackle on 2007-09-04
bump!

---

### Post by jdackle on 2007-09-28
*Update #1:*

I went to the IceWM e-mail list and asked about this.

Only one response basically saying that's how it is and won't change anytime soon... :(

I filed a feature-request for it here:
[https://sourceforge.net/tracker/?func=detail&atid=350031&aid=1801173&group_id=31](https://sourceforge.net/tracker/?func=detail&atid=350031&aid=1801173&group_id=31)

---

### Post by jdackle on 2007-09-30
*Update #2:*

I tried [lxp-icewm]("http://lxp.sourceforge.net/"), which, amnogst other things, sort of "fixes" that behaviour in icewm, though I'd prefer a little more freedom myself to choose the exact position ... or would have chosen a different position. But overall I'm satisfied with this solution and have ditched the original icewm for it. :)

In case you're wondering... lxp stands for LookXP... :( BUT they do have a Human theme - the one I'm using! ;) And also a .deb to download right-off! :D

[COLOR="Red"]Please note: LXP ist still BETA software.[/COLOR]

[SIZE="1"]NOTE: I will not however mark this tread as "SOLVED" as the problem in icewm persists...[/SIZE]

---

