---
title: "ubuntu calendar wallpaper - how does (did) it work?"
date: 2005-05-02
forum: Desktop Environments
---

### Post by vinthund on 2005-05-02
hello,

1. how can I set previous wallpaper from calendar? I have all months downloaded and installed via synaptic (oct.-apr.) but I can only choose April or ubuntu monthly (which is the same).Hwo about previous months? how can I ttrace them on my disk (I now i can download them form the web, but that is not my questuion

2. does April wallpaper mean we're thru with body-art?

vinthund

---

### Post by spd106 on 2005-05-03
If you downloaded the wallpaper through synaptic the .xml files are located in the /usr/local/gnome-wallpaper-properties folder. To access them through the desktop               background utility the files must be copied into the /usr/local/gnome-background-properties folder. This will need to be done as su.

```
$sudo cp -i /usr/share/gnome-wallpaper-properties/*.xml /usr/share/gnome-background-properties/ 
```

I'm not sure why it is like this. 

But this command works for me, though i'm not sure yet what happens with future calendar months.

---

### Post by americanrockradio on 2005-05-04
I hope not, that blonde chick is hot  \\:D/

---

### Post by mattack on 2005-05-04
speaking of... when does the May wallpaper come out?   :razz:

---

