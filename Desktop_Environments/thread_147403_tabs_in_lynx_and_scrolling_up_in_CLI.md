---
title: "tabs in lynx and scrolling up in CLI"
date: 2006-03-20
forum: Desktop Environments
---

### Post by rjs on 2006-03-20
Is there any equivalent of tabbed browsing with lynx? I am so used to tabs i just can't function without them. Also when one gets a whole heap of output (for example ls -a of a big directory) how does one scroll up. In a terminal emulator its easy as pie, you use the mouse, but i can't figure out how to do it on the old school real terminal.

-rjs.

---

### Post by jrib on 2006-03-20
don't know about the tabs, but to scroll up it's usually either PgUp or shift-PgUp.  What you usually do is pipe to 'less' or 'more' so that it displays one page at a time and you press a button to see the next one.  Like this:

```
cat /etc/X11/xorg.conf | less
```

---

### Post by kabus on 2006-03-20
I don't know about lynx, but both elinks and w3m have tabs.

---

