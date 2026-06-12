---
title: "Help removing panel &quot;handles&quot;"
date: 2007-04-26
forum: Desktop Environments
---

### Post by ld50 on 2007-04-26
I need a little help removing the handles on each side of the bottom panel in gnome.  I have added the following to .gtkrc-2.0 in my home directory as well as the needed 10x10 transparent "pixel.png".  This has successfully removed the handles from within the panel but not the ones on each end.  What am I missing here?

```
style "handle"
{
engine "pixmap"
  {
    image
    {
      function			= HANDLE
      file              		= ".pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= VERTICAL
    }
    image
    {
      function			= HANDLE
      file              		= ".pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= HORIZONTAL
    }
  }
}
class "PanelAppletFrame" style "handle"
```

Secondly, is there a way to make the panel a set width?  I have set the background set as an image and would like it to stay that size.  (expand is off)

---

