---
title: "I want to be able to &quot;clip&quot; pieces from webpages. Can I?"
date: 2009-01-25
forum: General Help
---

### Post by y0diggity on 2009-01-25
Here's what I want to do. 
I want to be able to go to a web page and drag a highlight box of some sort around a specific piece of that page and then be able to save that as a .jpg or whatever. Like you can do if you're editing a picture in Photoshop or Gimp. I've seen it done in a Windows Tablet OS, but is there an app or plugin I can get to do that with what I have? I have the "clipmarks" plugin for Firefox, but it selects its own sections and doesn't let me select them exactly how I want to. Also, it doesn't work so well on flash headers, etc.
Any suggestions? I don't know if I explained what I want very well, but it makes sense to me. :)

---

### Post by kaibob on 2009-01-25
A lot of utilities will do what you want. I use the Imagemagick import command-line utility. To try it, enter the following in a terminal window and then draw a rectangle with the cursor:

```
import -frame filename.png
```

If this works for you, assign it to a launcher.

BTW, I tried this on youtube, and it works fine with Flash. Also, I don't believe that Imagemagick is installed by default, but it's in the repo's and doesn't take up much space.

---

