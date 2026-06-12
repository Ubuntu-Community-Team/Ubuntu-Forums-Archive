---
title: "Evolution treeview gtkrc options"
date: 2009-12-31
forum: Desktop Environments
---

### Post by muffie82 on 2009-12-31
Hello, this is my first post on the forum :)

I have a problem with costomizing the treeview background of my themes. I want to get rid of the odd and even row colors. So I added: 

```
    GtkTreeView    ::odd_row_color        = "#FFFFFF"
    GtkTreeView    ::even_row_color       = "#FFFFFF"
```to my gtkrc file. 

This works for allmost all applications but not for Evolution mail client. Can anyone please help me get rid of them? 

As I understand it Evolution must use a different widget for the displaying the odd and even colors in the mail view. But I can be wrong.

---

### Post by VCoolio on 2010-01-01
Try: widget_class "*.ETree.*"

Also [from here]("http://ubuntuforums.org/showpost.php?p=8443484&postcount=118"):
```
style "evolution-hack" = "murrine-default" # Hacks for Evolution Mail.
{
bg[NORMAL] = shade (1.14, @bg_color) # Color for evo treeview headers.
bg[PRELIGHT] = shade (1.18, @bg_color) # Color for evo treeview header prelight.
bg[ACTIVE] = shade (0.75, @bg_color) # Color for unfocused evo selected items.
bg[SELECTED] = @selected_bg_color # Color for evo selected items.
fg[ACTIVE] = @selected_fg_color # Color for evo active text.
fg[SELECTED] = @selected_fg_color # Color for evo selected text.
}

style "murrine-treeview-header" = "murrine-button"
{
xthickness = 2
ythickness = 1
bg[NORMAL] = shade (1.14, @bg_color) # Color for treeview headers.
bg[PRELIGHT] = shade (1.18, @bg_color) # Color for treeview header prelight.
bg[ACTIVE] = shade (0.85, @bg_color) # Color for pressed-treeview.
engine "murrine"
{
roundness = 0 # This makes treeview progressbars square.
}
}

# Workarounds for Evolution
widget_class "*.ETable.ECanvas" style "murrine-treeview-header"
widget_class "*.ETree.ECanvas" style "murrine-treeview-header"
widget_class "*GtkCTree*" style "evolution-hack"
widget_class "*GtkList*" style "evolution-hack"
widget_class "*GtkCList*" style "evolution-hack"
widget_class "*.ETree.*" style "evolution-hack"
widget_class "*EInfoLabel*" style "evolution-hack"
```

---

