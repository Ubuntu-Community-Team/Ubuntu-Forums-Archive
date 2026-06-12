---
title: "Add Year to mate-panel"
date: 2020-12-10
forum: Desktop Environments
---

### Post by #&amp;thj^% on 2020-12-10
I favor CLI over GUI's, and I've been racking what little brains I had left, to add the year to Mate Panel.

Clock indicator in Ubuntu MATE 18.04 & 20.04 LTS is controlled by indicator-datetime service, so to set it the way i wanted, I had to use the commands below:
```

gsettings set com.canonical.indicator.datetime time-format custom
&&
gsettings set com.canonical.indicator.datetime custom-time-format '%l:%M %p %A %B %d'
```

it probably was doable in dconf-editor, and you would have had to set the time-format to "custom" in order for your changes to set.
Hope this helps others to add the year to the time.
```
**"man date"**
``` shows other custom sets also. Enjoy

---

