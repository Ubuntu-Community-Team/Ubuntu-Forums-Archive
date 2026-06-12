---
title: "human-icon-theme: missing &quot;mimetypes&quot; directory"
date: 2014-08-06
forum: Desktop Environments
---

### Post by Kirkx on 2014-08-06
I have Human icon theme and I was trying to get the text file icons to look as follows:

[http://i.imgur.com/INoZJkE.png](http://i.imgur.com/INoZJkE.png)

Normally, when changing just one or a few icons in an icon theme I would simply copy the desired icon(s) to an icon theme selected in Appearance settings. As my favourite text file icon originally belongs to Oxygen icon theme:

[http://i.imgur.com/F0fjk80.png](http://i.imgur.com/F0fjk80.png)

I would copy file "text-plain.png" from here:
```
/usr/share/icons/oxygen/22x22/mimetypes
```
to here:
```
/usr/share/icons/Human/22x22/mimetypes
```

However, apparently there is no "mimetypes" folder anywhere in </usr/share/icons/Human/> except for "48x48" subfolder. Obviously, 48x48 icons are not suitable for the file/folder tree in Thunar set to "view as detailed list":

[http://i.imgur.com/xvk11yZ.png](http://i.imgur.com/xvk11yZ.png)

I have found the workaround, but it's not very elegant:

- install "oxygen-icon-theme"
- install "tangerine-icon-theme"
- select "human-icon-theme" (in Appearance)

Now the text file icons look as the ones on the first screenshot.

---

### Post by Kirkx on 2014-08-07
After some googling around I have a partial answer to my original post. You need to look at the "Inherits" line in the file "index.theme". As it turns out:

- Human icon theme inhertis: Tangerine,gnome
- Tangerine inherits: gnome,oxygen

[http://i.imgur.com/vEU3wyt.png](http://i.imgur.com/vEU3wyt.png)

[http://i.imgur.com/bmfJdNW.png](http://i.imgur.com/bmfJdNW.png)

And Oxygen has the icon I need.

There are still a few questions, though.

1) While neither Human nor Tangerine have any text file icons, Gnome actually has one, named "txt.png", but it is never called despite Gnome being present in both "Inherits" lines mentioned above.

[http://i.imgur.com/qTq5m6Y.png](http://i.imgur.com/qTq5m6Y.png)

2) From what I have read, the directory list in "index.theme" should match the actual directories present on the hard drive. Human icon theme, however, has mimetypes listed in "index.theme", but they are nowhere to be found on the hard drive.

[http://i.imgur.com/KVNDixw.png](http://i.imgur.com/KVNDixw.png)

[http://i.imgur.com/tvWD3VZ.png](http://i.imgur.com/tvWD3VZ.png)

[http://i.imgur.com/BTSgvkk.png](http://i.imgur.com/BTSgvkk.png)

I'm not sure if it's a bug, or is it actually allowed and taken care of by "Inherits" function.

---

