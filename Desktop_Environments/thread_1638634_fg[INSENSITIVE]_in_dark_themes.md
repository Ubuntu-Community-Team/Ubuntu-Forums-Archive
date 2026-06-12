---
title: "fg[INSENSITIVE] in dark themes"
date: 2010-12-05
forum: Desktop Environments
---

### Post by bvc on 2010-12-05
I'm trying to update my Onux themes. I see that people are able to not have the old ugly bright fg[INSENSITIVE] but can't figure out how they are doing it. If anyone knows, help would be appreciated.

---

### Post by bvc on 2010-12-06
figured it out. Found this in the Poesia Theme. Makes me wonder how long this has been possible.
```
#the following is my desperate try to use the crux engine to draw (disabled) text
#to get rid of that annoying shadow, if you have more fixes or better ones, please 
#let me know

class "*Label*"                    style "cruxtext"
widget_class "*Label*"                style "cruxtext"
widget_class "*Cell*"                style "cruxtext"
widget_class "*.GtkTreeView"            style "cruxtext"
widget_class "*.GtkTreeView.GtkButton"         style "listheader"
```

---

