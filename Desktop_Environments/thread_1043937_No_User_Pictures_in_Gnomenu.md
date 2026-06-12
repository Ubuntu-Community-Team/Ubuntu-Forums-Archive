---
title: "No User Pictures in Gnomenu"
date: 2009-01-19
forum: Desktop Environments
---

### Post by 11lettenJ on 2009-01-19
Hi, 
I have recently installed gnomenu and am currently using the vista glass start button, vista menu, and vista icons. When I open it up, however, there are no pictures on the leftside (i.e accessories, games, graphics, internet, sound and video, system tools) with the exception of add/remove. Using the animated program widgets did not help. I've tried downloading new themes. At one time, I randomly did acquire these pictures but on a reboot, they disappeared. I was just wondering if anyone had the same problem and if there were any ways to resolve this. Thanks,
Jim

---

### Post by SonnHalter on 2009-01-31
need help too

---

### Post by phibit on 2009-03-16
Same exact problem here.

---

### Post by phibit on 2009-03-16
Okay after hours of looking through the python code, I solved the problem!!

It seems like when the icon is not found, it displays the ugly "default" icons, just that blue and white window. GnoMenu does something called icon caching, though, so it doesn't have to keep doing icon-lookups, but it DOESN'T CLEAR THE ICON CACHE WHEN YOU CHANGE ICON THEMES.

To solve the problem, just do this:

```
rm ~/.menuiconcache.xml
killall gnome-panel
```

And then gnome-panel and gnomenu will restart and your icons will once again be glorious. I suspect you have to do this every time you change icon themes.

---

### Post by asilaydyingdl on 2009-03-25
Where is the menu icon cache file located?

---

