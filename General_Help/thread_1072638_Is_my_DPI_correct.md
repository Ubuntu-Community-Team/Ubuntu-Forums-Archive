---
title: "Is my DPI correct?"
date: 2009-02-17
forum: General Help
---

### Post by Jengu on 2009-02-17
So I read that in Jaunty font DPI is going to be set to the DPI suggested by the monitor. So I ran the command documented [here]("https://wiki.ubuntu.com/X/Troubleshooting/HugeFonts") to see what my intended DPI is:

```

>> xpdyinfo | grep dots
resolution:    108x106 dots per inch

```

Of course I've been running at 96 DPI like everybody. So I tried switching to 108... and sure enough my fonts are bigger. I prefer them smaller, but I don't know if they're intended to look this way or not. If it is intended to look this way, for best quality I believe I should be setting my DPI to 108 and then reducing my font size. If it's not intended to look this way, I should be filing a bug and just switching back to 96. But I don't know how to tell. Anyone?

For reference, this is on a 14" LCD laptop (Dell Vostro 1400).

Screenshot 96 DPI:
[[IMG]http://img15.imageshack.us/img15/7994/screenshot96dpiti1.png[/IMG]](http://imageshack.us)
[[IMG]http://img15.imageshack.us/img15/screenshot96dpiti1.png/1/w1280.png[/IMG]](http://g.imageshack.us/img15/screenshot96dpiti1.png/1/)
Screenshot 108 DPI:
[[IMG]http://img15.imageshack.us/img15/3664/screenshot106dpigq5.png[/IMG]](http://imageshack.us)
[[IMG]http://img15.imageshack.us/img15/screenshot106dpigq5.png/1/w1280.png[/IMG]](http://g.imageshack.us/img15/screenshot106dpigq5.png/1/)

---

