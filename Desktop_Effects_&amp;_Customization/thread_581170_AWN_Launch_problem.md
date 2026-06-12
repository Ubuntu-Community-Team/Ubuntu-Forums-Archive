---
title: "AWN Launch problem"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by Linder on 2007-10-19
Hi there! 

Having some issues launching AWN on my machine. It's a Compaq EVO N610 and I ran AWN semi-successfully on Feisty. Now upgraded to Gutsy, Compiz-Fusion running smoothly. However, I installed AWN following [this]("http://ubuntuforums.org/showthread.php?t=385981&highlight=AWN") guide. I also installed AWN Curve addon themes. When I try to run AWN nothing at all happens. So I tried launching it in a terminal to see the error, and this is what shows up:

```
tobias@Evo-Ubuntu:~$ avant-window-navigator
Screen is composited.
APPLET : /usr/local/lib/awn/applets/taskman.desktop
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_shared_mem_create
tobias@Evo-Ubuntu:~$
```

---

### Post by digitalfiz on 2007-11-03
Hey man I was having same exact error and I found the solution on another site. I uninstalled awm-curves and it started working. I still havent figured out how to get it working WITH awn-curves but for now to make it work you can uninstall it. Just though I'd let you know this much so you arnt left hanging like I was. If i find out how to get it working with awn-curves I'll repost


Here is where I found it:

[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=853&page=3&isLive=true](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=853&page=3&isLive=true)

It says latest trunk of awn-curves fixes it but I though thats what I grabbed. Guess not

---

### Post by Linder on 2007-11-23
Thanks mate! I've given up COmpiz for now. It's a tad too buggy with all settings on. And I've realised I don't like AWN anyway :P It's pretty, but I have no use for it.

---

### Post by Stu09 on 2008-03-06
Has anyone got any more info regarding this ?
I get the same error. I would like it to work however, not just un-install it.

---

