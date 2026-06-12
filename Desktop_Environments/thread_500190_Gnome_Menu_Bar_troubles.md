---
title: "Gnome Menu Bar troubles"
date: 2007-07-13
forum: Desktop Environments
---

### Post by Sikarian on 2007-07-13
In the gnome menu bar, under Applications, where you've got Accessories, Education, etc... I was under Edit Menu trying to edit an item and I accidently dragged the Education menu.  I dont know where I dropped it, but its been deleted and removed from the menu list.  If I try to recreate a new menu and call it Education,  no programs I add that go in the Education menu go there.  It's like, gone.

Is there anyway to rebuild the menu and get it back?  I had a bunch of programs under there I used and now they are not listed any more.

---

### Post by mbradlcu on 2007-07-14
I'm not totally sure on this one but 2 thing you may want to try,, 
playing with the gnome-menu editor it seem there's a "revert" button,, I didn't mess with mine but if you''re stuck you may want to as a last resort,,
another way is to find were you dropped your "Education" folder, you can find this by using the following:
```
find .gnome2 -type f -exec grep -ln 'Education' {} \;
```
I found it in:
> .gnome2/yelp.d/sk-content-list.last
editing that file looks a little squirrely but I'd make a copy of it and dig in.
please let me know if you have any questions with this

thanks!

---

