---
title: "Black Gnome panel - nearly there"
date: 2009-02-25
forum: Desktop Environments
---

### Post by JimmiG on 2009-02-25
So I'm running Ubuntu 8.10 on my netbook, and I've been trying to make it looks as close to UNR 1.0.1 (which I was running before) as possible. This involved making the gnome panel black and changing the text to white, which I've managed to do.

Now I've only got two "separators" that stick out. As you can see, there's one just to the right of the Ubuntu logo in the top left, and another between the close button and the notification area:
[[IMG]http://img22.imageshack.us/img22/2779/netbook.gif[/IMG]](http://imageshack.us)

They are not the default gnome panel separators, instead they are part of the notification area and go home applet. If I remove those, the lines disappear. The one between the clock and the shutdown/switch user buttons is a normal divider that can easily be removed if unwanted.

I know it's possible to remove them or at least make them invisible/black, because in Ubuntu Netbook Remix 1.0.1, they're not there as seen [here]("http://arstechnica.com/hardware/news/2008/06/hands-on-with-the-ubuntu-netbook-remix.ars")

Any ideas?

---

### Post by dbbolton on 2009-02-25
Make a file called "handle.png" (like a black or transparent square) and then add this to your theme's gtkrc file:

```

style "handle"
{
engine "pixmap"
  {
    image
    {
      function			= HANDLE
      file              		= "handle.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= VERTICAL
    }
    image
    {
      function			= HANDLE
      file              		= "handle.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= HORIZONTAL
    }
  }
}
class "PanelAppletFrame" style "handle"

```

Hope this helps

---

### Post by hit on 2009-12-28
Any ideas why this isn't working? (anymore?)

---

