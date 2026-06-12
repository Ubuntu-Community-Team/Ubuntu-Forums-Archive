---
title: "Banshee Not Playing Audio Files...Help"
date: 2009-01-17
forum: General Help
---

### Post by Kristopher on 2009-01-17
Just upgraded to 8.10, thought I would use Banshee for my audio and see how it is...but when i click a mp3 track or m4a i see a small orange square with a cross through.

How do i fix this?

Thanks

---

### Post by abdusamed on 2009-11-15
> **Kristopher said:**
> Just upgraded to 8.10, thought I would use Banshee for my audio and see how it is...but when i click a mp3 track or m4a i see a small orange square with a cross through.

How do i fix this?

Thanks


yea same prob with karmic.. i click on play.. a white cross shows up on the left of the track :(

---

### Post by cnelbuendia on 2009-11-25
Try restoring the GStreamer configuration to default. 
To do that try the following: 

```

rm -rf ~/.gconf/system/gstreamer
rm -rf ~/.gstreamer-0.10
```That worked for me.  ;)

---

