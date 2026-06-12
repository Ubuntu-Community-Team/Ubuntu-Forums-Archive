---
title: "gnome: get rid of seperators"
date: 2007-01-05
forum: Desktop Environments
---

### Post by matva on 2007-01-05
i'd like to get rid of the ugly seperators on the gnome panel. is this possible? 

i've attached a screenshot to show what i mean.

---

### Post by ComplexNumber on 2007-01-06
i can't see the screenshot.

yes, it is possible. jsut right click on them and select delete.

---

### Post by matva on 2007-01-07
the screenshot is just that small bit. The seperator i'm referring to is to the right of the ubuntu  logo.  There is no "delete" option..

---

### Post by Quillz on 2007-01-07
> **matva said:**
> the screenshot is just that small bit. The seperator i'm referring to is to the right of the ubuntu  logo.  There is no "delete" option..
I would have thought that locking the icons in place would remove the separators, like in Windows, but it seems that this is not the case. I would like a "fix" for this, also, if at all possible.

---

### Post by tweedledee on 2007-01-09
> **Quillz said:**
> I would have thought that locking the icons in place would remove the separators, like in Windows, but it seems that this is not the case. I would like a "fix" for this, also, if at all possible.

Could you clarify exactly what you mean?  That original screenshot is hard to see, I can't tell what the problem is.  In general, though, anything that you can add to a gnome panel (separator, whatever) should have a "remove from panel" option.  If what you actually mean are the bits on the ends of a non "expanded" panel, you're stuck with those - they are the only way to ensure that there is somewhere to click on to move/modify a full panel that isn't expanded.

---

### Post by Quillz on 2007-01-11
> **tweedledee said:**
> Could you clarify exactly what you mean?  That original screenshot is hard to see, I can't tell what the problem is.  In general, though, anything that you can add to a gnome panel (separator, whatever) should have a "remove from panel" option.  If what you actually mean are the bits on the ends of a non "expanded" panel, you're stuck with those - they are the only way to ensure that there is somewhere to click on to move/modify a full panel that isn't expanded.
Is there a way to replace those with transparent images instead?

---

### Post by mcduck on 2007-01-11
Here's how you can hide the handles from window list and notification area applets. This doesn't work for the bars at the ends of panel when it's not expanded.

1. make a 10x10px empty transparent image with Gimp and save it as .handle.png in your home directory
2. create a .gtkrc-2.0 file inside your home dir
3. paste the following code to the file:
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
4. Log out and back again. Enjoy :)

---

### Post by Quillz on 2007-01-11
> **mcduck said:**
> Here's how you can hide the handles from window list and notification area applets. This doesn't work for the bars at the ends of panel when it's not expanded.

1. make a 10x10px empty transparent image with Gimp and save it as .handle.png in your home directory
2. create a .gtkrc-2.0 file inside your home dir
3. paste the following code to the file:
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
4. Log out and back again. Enjoy :)
The handles are still there on my expanded panel. By default, they are those dashed lines, right?

And is there any way to replace the handles of a non-expanded panel with transparent images?

---

### Post by tweedledee on 2007-01-13
> **Quillz said:**
> The handles are still there on my expanded panel. By default, they are those dashed lines, right?

And is there any way to replace the handles of a non-expanded panel with transparent images?

I assume so, as different themes can change the appearance of those handles.  I'd suggest you take a look at some gnome theme information and see if you can track it down, with the warning that the documentation is only so-so.

[http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)
[http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html) (mostly section III on widgets)

Some Google searches will also turn up bits and pieces of other information.  Once you ultimately track down the relevant information, it MAY be as simple as replacing a single .png somewhere - you could also poke around the /usr/share/pixmap & usr/share/themes directories to see if you can locate the image being used for the handle.

---

### Post by mcduck on 2007-01-15
> **Quillz said:**
> The handles are still there on my expanded panel. By default, they are those dashed lines, right?
do you have 'gtk2-engines-pixbuf'-package installed? It's needed for bitmap images in themes to work.

---

### Post by Enverex on 2007-01-15
Doesn't "Right click on the panel > Lock panels" make them disappear?

---

