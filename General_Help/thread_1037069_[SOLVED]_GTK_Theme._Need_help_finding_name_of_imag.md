---
title: "[SOLVED] GTK Theme. Need help finding name of image file to customize"
date: 2009-01-11
forum: General Help
---

### Post by chez17 on 2009-01-11
Hello all,

I don't know a better way to describe this, but when you add the "notification area" or "window list" to the panel, there is a little image on the left that sort of lets you know it's there when there are no windows open or no notifications. Is the name of the file the same in every theme? I am using the Blue-Joy theme for the panel and I can't figure out how to change that little image. Any help is most appreciated. Thanks.

---

### Post by mcduck on 2009-01-11
I suppose the image file name can change, and actually I think it might not even always be a image file, but might also be rendered by the theme engine.

Anyway, you don't need to know the original file's name, all you need to know is how to define your own image instead..

The class you want to change in your GTK theme is "PanelAppletFrame".

I've used the following piece of code in my .gtkrc-2.0 file to hide those applet handles:
```
style "handle"
{
engine "pixmap"
  {
    image
    {
      function			= HANDLE
      file              		= ".handle.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= VERTICAL
    }
    image
    {
      function			= HANDLE
      file              		= ".handle.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= HORIZONTAL
    }
  }
}
class "PanelAppletFrame" style "handle"
```
The image this code is pointing at is a (hidden) 1x1 pixel fully transparent PNG image I just  put into my home directory.

So while I have no idea where the original handle graphics are coming from this allows replacing them with my own image. Since I don't feel that I need those handles for anything I chose empty picture. ;)

---

