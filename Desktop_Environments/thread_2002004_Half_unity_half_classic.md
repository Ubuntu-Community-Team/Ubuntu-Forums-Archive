---
title: "Half unity half classic"
date: 2012-06-12
forum: Desktop Environments
---

### Post by tokintmash on 2012-06-12
Hi,

I reverted back to gnome classic in Ubuntu 11.04 and was mostly happy with it. I  though I install CompizConfic and see if I can get my desktop cube back.

I do not unfortunately remember what did I exactly click (it was on  desktop tab), but the result is that I have old menus but windows do not  have borders anymore (like in unity). I cannot resize them or move them.

The "logout and choose gnome classic" does not work either.

What can I do? Is there are way to revert first to proper Unity and then again to proper Classic?

Thanks

---

### Post by wilee-nilee on 2012-06-12
> **tokintmash said:**
> Hi,

I reverted back to gnome classic in Ubuntu 11.04 and was mostly happy with it. I  though I install CompizConfic and see if I can get my desktop cube back.

I do not unfortunately remember what did I exactly click (it was on  desktop tab), but the result is that I have old menus but windows do not  have borders anymore (like in unity). I cannot resize them or move them.

The "logout and choose gnome classic" does not work either.

What can I do? Is there are way to revert first to proper Unity and then again to proper Classic?

Thanks

Try in unity just resetting unity, this resets compiz as well in a perfect world.

alt-f2
```
unity --reset
```If alt-f2 does not work use a terminal.

Check the rest options here as well.
[http://askubuntu.com/questions/71926/resetting-compizconfig-settings-manager-settings](http://askubuntu.com/questions/71926/resetting-compizconfig-settings-manager-settings)

I am not sure if compiz now has a autostart in the classic now, or what its window manager actually is.

---

### Post by tokintmash on 2012-06-12
I got this error:

```
unity-panel-service: no process found
compiz (core) - Error: Couldn't load plugin 'reset'
compiz (core) - Error: Couldn't load plugin 'reset'
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
```

---

### Post by wilee-nilee on 2012-06-12
When, where, and how was it run, **context is so important**. 

Always post everything including the command.

I gave you multiple options including a link.

If you have removed anything this info is important as well.

---

### Post by tokintmash on 2012-06-12
That error was a response to "unity -- reset".

I may have removed something when I first got rid of Unity. I read a couple of how-tos and one of them worked.

But now I have removed nothing.

---

