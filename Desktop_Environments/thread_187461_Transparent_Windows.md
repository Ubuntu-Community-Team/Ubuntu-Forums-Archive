---
title: "Transparent Windows"
date: 2006-06-03
forum: Desktop Environments
---

### Post by BoneyOne on 2006-06-03
How do I make the windows transparent? Mainly I'm looking for the inactive windows to become about 50%-80% transparent and then active window to be normal.

I've looked all around and couldn't find anything for this.

BTW: Not sure if it matters but I'm running Dapper with Xgl+Compiz

---

### Post by BoneyOne on 2006-06-03
Does no one know how to do this?

I know it's possible as I've seen screenshots and videos with these effects, I just can't seem to find any documentation on how to do it.

---

### Post by justinflavin on 2006-06-03
xgl is alpha software, so i wouldnt be surprised if its not working for you.

you can read more about it here:
[https://wiki.ubuntu.com/CompositeManager?action=show&redirect=Xgl](https://wiki.ubuntu.com/CompositeManager?action=show&redirect=Xgl)

---

### Post by justinflavin on 2006-06-03
i found this - which might be of help:

[http://www.ubuntuforums.org/showthread.php?t=147049](http://www.ubuntuforums.org/showthread.php?t=147049)

---

### Post by angkor on 2006-06-03
[QUOTE=BoneyOne]I've looked all around and couldn't find anything for this.
[/QUOTE]

Try the compiz forum. I think I read somewhere there is a plugin for this.

[http://www.compiz.net/](http://www.compiz.net/)

---

### Post by steveneddy on 2006-06-03
[QUOTE=angkor]Try the compiz forum. I think I read somewhere there is a plugin for this.

[http://www.compiz.net/](http://www.compiz.net/)[/QUOTE]

Um, you try transset? Type in a terminal:

transset 0.8

A cross appears where the curser is and click the window you want to be transparant. You can also add transset to the launcher of any app.

example: firefox transset 0.8

Firefox will launch with transset started and an 80% transparancy.

---

### Post by angkor on 2006-06-03
[QUOTE=steveneddy]Um, you try transset? [/quote]

Transset is deprecated when you use xgl & compiz.

It's the 'state' plugin I was talking about. With this plugin you can set the transparancy for windows, menus etc.

I'm sorry I can't explain atm how to configure this plugin since I currently don't have an xgl install on my box. I probably will next week though. :) I'm sure there's some useful info at the compiz forum. Or in the ubuntu xgl threads.

---

### Post by BoneyOne on 2006-06-03
Sweet, exactly what I was looking for.  Thanks, i was trying to find it in gconf-editor and having no luck finding the option for it.

Thanks!!

angkor, yeah I was reading how transset isn't great for xgl & compiz (even though it seems to work great for me so far) and that state is much better.  But I had no luck searching the forums there for the plugin so with all the talk about compiz here I figured I'd give it a shot.

I'm going to continue to try to find some better info on state though.

---

### Post by olsonar on 2006-06-03
hold down alt and use the scroll wheel. down increases transparency, up decreases.

---

### Post by BoneyOne on 2006-06-03
[quote=olsonar]hold down alt and use the scroll wheel. down increases transparency, up decreases.[/quote]
Nope, that doesn't work for me, it just seems to ignore the alt keypress and just scroll whatever window is active.

---

### Post by Wr8EYilK8Y on 2006-06-30
Same here. I can't do transparency with XGL.

---

