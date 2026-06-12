---
title: "Firefox userchrome fonts"
date: 2007-09-12
forum: Desktop Environments
---

### Post by lenniboy on 2007-09-12
Hi, I would like my Firefox menu fonts (File, Edit, View...) be the same than my XFCE fonts. I have edited the userchrome file and could change the font size but Firefox does not use the font family I have specified, which would be Sans. (That's the font I have selected in the XFCE User Interface settings). However, if I tell it to use MS fonts like Times New Roman it works!


```

menubar, menubutton, menulist, menu, menuitem, textbox, toolbar, tab,
tree, tooltip
{
    font-family: Sans !important; 
    font-size: 9 px !important;
    
}
```

Is there any way to sync Firefox with the rest of the menu fonts?

---

### Post by Happy_Man on 2007-09-12
Perhaps try Sans Serif?

---

