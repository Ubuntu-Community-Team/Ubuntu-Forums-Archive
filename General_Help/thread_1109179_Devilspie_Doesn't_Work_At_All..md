---
title: "Devilspie Doesn't Work At All."
date: 2009-03-28
forum: General Help
---

### Post by Penguin Guy on 2009-03-28
Devil's Pie doesn't work, it has no effect at all.

*/home/josh/.devilspie/Thunderbird.ds*
```
(if (is (application_name) "Thunderbird") (set_workspace 2))
```

Debug output:
```
~$ devilspie
Window Title: 'me@comp: ~'; Application Name: 'Terminal'; Class: 'Gnome-terminal'; Geometry: 587x412+0+25
Window Title: '[gnome] Devilspie Doesn't Work At All. - Ubuntu Forums - Mozilla Firefox'; Application Name: 'Firefox'; Class: 'Firefox'; Geometry: 1280x974+0+25
Window Title: 'x-nautilus-desktop'; Application Name: 'File Manager'; Class: 'Nautilus'; Geometry: 1280x1024+0+0
Window Title: 'Top Expanded Edge Panel'; Application Name: 'Top Expanded Edge Panel'; Class: 'Gnome-panel'; Geometry: 1280x25+0+0
Window Title: 'Bottom Expanded Edge Panel'; Application Name: 'Bottom Expanded Edge Panel'; Class: 'Gnome-panel'; Geometry: 1280x25+0+999

```


I fiddled around with the code, debugged and reinstalled devilspie a few times and eventually got it to work. If you're looking for a solution to your devilspie issues, I'm afraid I can't remember what I did. I do know, however, that it's important that you use plain quotes [COLOR="Green"]**"**[/COLOR] rather than the fancy HTML quotes [COLOR="Green"]**“**[/COLOR]/[COLOR="Green"]**”**[/COLOR] that you see on a few of the devilspie guides. Good luck.

---

