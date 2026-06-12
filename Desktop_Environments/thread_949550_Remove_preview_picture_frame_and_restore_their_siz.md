---
title: "Remove preview picture frame and restore their size"
date: 2008-10-16
forum: Desktop Environments
---

### Post by derma on 2008-10-16
If you upgrading from Gutsy to Hardy dislike the frame around the picture preview... well you can do this workaround... in this way the previews should be as were in Gutsy.


So...


go here (typing "sudo"... or using the nautilus scripts)...


```
/usr/share/pixmaps/nautilus/
```



make a copy of this file...


```
thumbnail_frame.png
```


...and rename that "**thumbnail_frame.png**.*backup*" (or whatever you want... it's the same!!)


next open **gconf**, that means "System **>** Editor Config...." (I don't know that item name 'cos using the italian version... pardon!!)


and go into this path...


```
/apps/nautilus/icon_view
```


set the key **thumbnail_size** to *96*


(unless it has being set at this value!!!... but I think most of you did that to avoid giant previews with a awful and absurd frame around them!!!)


restart Nautilus typing in a Terminal...


```
killall nautilus
```



That's all!!!



Frame off and preview as in Gutsy!!!











Ce la...

---

