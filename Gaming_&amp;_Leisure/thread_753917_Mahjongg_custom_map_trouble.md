---
title: "Mahjongg custom map trouble"
date: 2008-04-13
forum: Gaming &amp; Leisure
---

### Post by natirips on 2008-04-13
So fine, I made a custom Mahjongg map:```
<mahjongg>
  <map name="VidZmay" scorename="vidzmay">
    <layer z="0">
      <block left="0" top="0" right="15" bottom="15"/>
    </layer>
    <layer z="1">
      <block left="0.5" top="0.5" right="14.5" bottom="14.5"/>
    </layer>
    <layer z="2">
      <block left="1" top="1" right="14" bottom="14"/>
    </layer>
    <layer z="3">
      <tile x="10" y="10"/>
    </layer>
  </map>
</mahjongg>
```and saved it as vid.map in /usr/share/gnome-games/mahjongg/maps directory. I've also tried putting the <map>...</map> part into the mahjongg.map file at the end of the file, just above that </mahjongg> part, but now Mahjongg won't start, it seems to be trying to load-up but it can't. I've also tryed adding one more tile (because I'm not sure if I have even number of tiles) but nothing changes. If I remove my map it starts normally. Can anyone tell me what I did wrong?

---

### Post by natirips on 2008-04-16
bump

---

