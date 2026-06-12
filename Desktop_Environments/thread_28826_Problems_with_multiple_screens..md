---
title: "Problems with multiple screens."
date: 2005-04-21
forum: Desktop Environments
---

### Post by TheOwl on 2005-04-21
I have 3 screens in my current config: one off of a pci vga card, and two from agp nvidia card (one monitor, one tv). Everything works like a charm, though I have a couple of problems. As I have set up multiple screens, and not simply extended my desktop to 3 screens, I can't move windows across them. It's not really a problem, I like it more this way, but sometimes it can be a hindrance. Any idea how to do that?

Also, gnome-panels don't save themselves on other screens than the primary one. This one really pisses me off, since actually, I want no panels on the other two screens. Secondary monitor is for fullscreen IRC, and the TV is for movies. Both need no panels, and they magically pop back up after a reboot (or even logoff/on cycle). On the primary screens the panels just stay as I left them when I reboot.

And lastly, how can I set different backgrounds for different screens? This I've been trying to figure out a long time too, with no luck. Gnome doesn't seem to support it, messing with the root window yourself just pisses Gnome off and you can only see your manual results for a second or two, and massively big desktop pictures just don't work, like they do in Windows (stupid workaround, yeah, but at least it worked.)

I've been searching for answers for many weeks now, some times more actively and sometimes have just simply let them be, so I'd really appreciate it if someone with both the knowledge and the time to answer my probably simple but complex questions would do so. Thank you. :grin:

---

### Post by lewiz on 2005-04-23
[QUOTE=TheOwl]I have 3 screens in my current config: one off of a pci vga card, and two from agp nvidia card (one monitor, one tv). Everything works like a charm, though I have a couple of problems. As I have set up multiple screens, and not simply extended my desktop to 3 screens, I can't move windows across them. It's not really a problem, I like it more this way, but sometimes it can be a hindrance. Any idea how to do that?[/quote]
You'll need to use the Xinerama extension.  There's no point in me explaining it all here but check out [http://www.tldp.org/HOWTO/Xinerama-HOWTO/](http://www.tldp.org/HOWTO/Xinerama-HOWTO/) -- it's a little out of date but it should have everything you need.

What's more, once you've got Xinerama working you will be able to move windows across screens and you can define which display the GNOME panels will show up on.

Not too sure about multiple wallpapers though -- a cheap solution would be to join a number of images together and create a new image and use that.

---

### Post by TheOwl on 2005-04-25
Thanks! I'll check it out, I'll post if it helps or not!  :)

---

