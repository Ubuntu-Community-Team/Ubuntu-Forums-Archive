---
title: "Problem applying X11 mouse-themes"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by mrazster on 2007-04-23
Lo folks....have a stupid little problem with mouse-themes in xfce4.

When I try setting anything else then "default" mouse-theme in "mouse-settings" it won't take it.."kind of".....doesn't appear on desktop and in thunar e.t.c... but when I open Firefox I can se the "new" cursor when I move the cursor over to firefox window. But as soon as I move back to desktop the "default" cursor comes back. 

I have tried unpacking the mouse-theme both in:

```
/usr/share/icons
```

and

```
~/.icons
```

But it doen't matter...stil the same.

Any suggestions..?

---

### Post by mrazster on 2007-04-24
Anyone..?

---

### Post by mrazster on 2007-04-30
Ok guys I'm giving this one a last bump.

I re installed my system today..for other reasons....and I did a server/CLI install...then manually added xfce4 and all other packages.
I still get that wierd behavior with mouse themes.
Only one I've been able to use (other tha deafault) is human cursor theme...when installing it from the repos.

Any other X11 theme I add...behaves strange..like explained above.

When I was runing *"Xubuntu"* installed with the xubuntu metapackage and all stuff..it worked. But when installing it like this it won't....what packages did I miss/leave out...??

Any ideas..?

---

### Post by dj_juno on 2007-10-10
I had this same issue and found that editing /usr/share/icons/default/index.theme solved things.  The file only had a couple lines that I changed from:
[Icon Theme]
Inherits=core
to:
[Icon Theme]
Inherits=ComixCursors-Blue-Regular
(which was the folder name of theme i was trying to get working)

then i restarted X and the cursor theme applied to everything.
yay!

---

### Post by angryforumreader on 2008-04-21
Thanks a lot I was having the same exact problem 
cursor changed to the normal one when it scroll out of firefox

made a folder and put the cursor theme in /usr/share/icons/<folder name>
then edit /usr/share/icons/default/index.theme

and change to inherits=<folder name>

---

