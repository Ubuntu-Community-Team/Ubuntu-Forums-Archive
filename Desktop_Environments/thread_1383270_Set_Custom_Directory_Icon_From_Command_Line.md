---
title: "Set Custom Directory Icon From Command Line"
date: 2010-01-17
forum: Desktop Environments
---

### Post by fisherm on 2010-01-17
Hello. I am looking for a way to (via bash script) set a custom directory icon for a number of directories. All of these directories contain a "cover.jpg" image. I can accomplish this manually by right clicking the directory > select "Properties > click the directory icon button > select the "cover.jpg" image. I am just looking for the way to do this in the terminal to save time, as the music collection is quite large. Thanks in advance.

---

### Post by mutex023 on 2010-02-02
found this solution from - [http://old.nabble.com/How-do-I-change-a-folder-icon-from-a-script--td25832597.html](http://old.nabble.com/How-do-I-change-a-folder-icon-from-a-script--td25832597.html)

In gvfs 2.28 you can use gvfs-info and gvfs-set-attribute to get and set 
any metadata. 
To get the custom icon value; 
# gvfs-info -a metadata::custom-icon myfolder 

To set a custom icon 
# gvfs-set-attribute myfolder metadata::custom-icon 
file:///usr/share/pixmaps/gnome-spider.png 

Hope this helps, I too was looking for this.

---

### Post by Dart00 on 2010-06-09
Sorry for bring up a old thread....

But now that you set the custom icon from the terminal...how do you "un"set it back to the standard/default icon?

---

### Post by Dart00 on 2010-07-11
BUMP

Still cant figure this out... :(

---

### Post by maclofreak on 2010-07-14
> But now that you set the custom icon from the terminal...how do you "un"set it back to the standard/default icon?
One way is to just go Right Click>Properties>Click on icon>Revert.
But i don't know how to do it in the terminal.

---

### Post by redRumSirIsMurder on 2010-07-31
This should have the same effect as selecting 'revert' from the icon properties window:

```
gvfs-set-attribute -t stringv [COLOR="Red"]myfolder[/COLOR] metadata::custom-icon ""
```

This declares the attribute type to be 'stringv' before setting it blank ( "" ). Might seg fault if you don't include the empty quotes.

Use at own risk &c.

---

### Post by kyleabaker on 2010-11-19
This doesn't seem to work for me. I'm testing it on my Dropbox folder, but the icon never changes. Is there something more that I need to do?

EDIT:
Nevermind, I got it working.

---

### Post by marksch on 2011-04-12
kyleabaker,

What did you do to get it working?

Mark

---

### Post by a.sarkar on 2011-06-20
Hi all,

I know, this is an old thread, but this is really for the benefit of others who might stumble upon this. 

The command to reset the icon for a folder is
```
gvfs-set-attribute myfolder -t unset metadata::custom-icon
```

---

