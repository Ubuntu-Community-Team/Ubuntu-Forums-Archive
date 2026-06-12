---
title: "&gt;&gt;&gt;&gt;&gt;&gt;all Effects Aren't Working&lt;&lt;&lt;&lt;&lt;&lt;"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by amneziac on 2007-08-06
I made a stupid mistake by changing my theme with default themes which completely disabled my beryl effects. I cant rotate cube, no wobbly windows or anything else. Anything I change in the beryl settings manager doesn't get applied.
I know there is something in the terminal I can type in that will fix all of this.
PLEASE HELP

---

### Post by walkerk on 2007-08-06
> **amneziac said:**
> I made a stupid mistake by changing my theme with default themes which completely disabled my beryl effects. I cant rotate cube, no wobbly windows or anything else. Anything I change in the beryl settings manager doesn't get applied.
I know there is something in the terminal I can type in that will fix all of this.
PLEASE HELP

```
compiz --replace &
```
```
emerald --repalce &
```

---

### Post by operator207 on 2007-08-06
Do you have the beryl manager "ruby" on the toolbar? if so, click on it, and highlight "Select Window Manager" what is checked off? If beryl, switch to Metacity, let the desktop settle, then select Beryl. See if that fixes it. If NOT beryl, then thats your problem, and select beryl.

Mine will occasionally come up without beryl running, defaults to Metacity, even though I have told it in the session manager to only use beryl.

---

