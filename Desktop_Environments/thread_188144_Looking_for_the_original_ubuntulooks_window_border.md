---
title: "Looking for the original ubuntulooks window border..."
date: 2006-06-03
forum: Desktop Environments
---

### Post by shame on 2006-06-03
If anyone can remember that far back, the first time we saw ubuntulooks in dapper, the human metacity theme to go with it was bright orange and there were lots of complaints and arguments but I liked it.
Well I've been longing to have that metacity theme back so does anyone know how I can get it?
I don't want the whole ubuntu artwork package from that time, just the metacity theme.

---

### Post by bvc on 2006-06-05
The old had a harder gradient so I can't help you there. I don't know the exact color but this is close
#B85A33

Put that in the Human gtkrc about line 187 where it says
```
style "metacity-frame" = "clearlooks-default"
{
	bg[SELECTED] = "#CC863E"
}
```

make it
```
style "metacity-frame" = "clearlooks-default"
{
	bg[SELECTED] = "#B85A33"
}
```

reset the theme

---

