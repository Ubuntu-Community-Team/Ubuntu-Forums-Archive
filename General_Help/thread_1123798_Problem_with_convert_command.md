---
title: "Problem with convert command"
date: 2009-04-12
forum: General Help
---

### Post by svsig on 2009-04-12
I am trying to create thumbnails from a bunch of images using the convert command. It works fine, but I am unable to determine the orientation of the image, whether it is portrait or landscape. I am using this command:

```
convert -size 120x120 $f -resize 120x120 +profile '*' thumbnails/$f
```

where $f is the file name. All thumbnails are written as landscape even if the original was portrait.

I have found the description here: [http://linux.about.com/od/commands/l/blcmdl1_convert.htm]("http://linux.about.com/od/commands/l/blcmdl1_convert.htm"):

Does anybody know if it is possible to keep the portrait orientation when scaling images this way?

---

