---
title: "remove exif data from jpegs"
date: 2007-04-25
forum: Desktop Environments
---

### Post by adza on 2007-04-25
hi there, i was wondering if anyone konws how i might be able to remove the exif data from jpeg files (i have 200+ to do!!)... i need to do this because of a memory leak in the plogger program that crashes when uploading from olympus cameras... wierd, but there you have it! i tried to open one of these jpegs in gimp... it (sort of) crashed my box... not pretty, this exif stuff from olympus must be pretty freaky....

---

### Post by mcduck on 2007-04-25
You could use command-line tool Imagemagick to do that. Just run 'sudo apt-get install imagemagick' if you don't already have it. (or get it from Synaptic).

'mogrify -strip image.jpg' will remove EXIF data from a single jpg image.

..or you could use 'mogrify -strip *.jpg' to process all jpg images in the current directory.

---

### Post by adza on 2007-04-25
Sweet, thanks for that... i've just installed and successfully used jhead to achieve that... sudo apt-get install jhead.... then jhed -de * to strip exif data.... same result!! sorry for the post!

---

