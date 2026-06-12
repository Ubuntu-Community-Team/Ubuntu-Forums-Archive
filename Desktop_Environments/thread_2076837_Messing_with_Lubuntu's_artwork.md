---
title: "Messing with Lubuntu's artwork"
date: 2012-10-27
forum: Desktop Environments
---

### Post by vasa1 on 2012-10-27
I'm using the Lubuntu Box icon theme of Lubuntu 12.10. But, because of the color of the panel background, I wanted to change the color of certain icons. To do so, I edited the relevant .svg file with a text editor. In this case, I edited /usr/share/icons/lubuntu/panel/22/nm-device-wired.svg.
```
    <linearGradient
       id="linearGradient3587-6-5-1">
      <stop
         offset="0"
         style="stop-color:#003263;stop-opacity:1"
         id="stop3589-9-2-9" />
      <stop
         offset="1"
         style="stop-color:#a2e5fb;stop-opacity:1"
         id="stop3591-7-4-9" />
    </linearGradient>

```
I changed the "stop-color" values from #000000 and #363636 to #003263 and #a2e5fb, respectively.

Now, the nm applet icon has shades of blue rather than grey.

---

### Post by vasa1 on 2012-10-27
Did a little bit more but found that, for some reason, the battery icon and the shutdown icon were not in /usr/share/icons/lubuntu/panel/22 but in /usr/share/icons/lubuntu/panel/2**4**.

---

