---
title: "Is there any application that start another allication are finnished"
date: 2013-04-22
forum: Desktop Environments
---

### Post by Azyx on 2013-04-22
For instane a movie player that start a music player when the movie is över? There are for instane vlc who may bllay booth movies and music, but I vant lower volume after the movir.

---

### Post by papibe on 2013-04-22
Hi Azyx.

You can write a little shell script for that. This would be a simple example:
```
#!/bin/bash

vlc --volume 400 movie.mp4

vlc --volume 200 song.mp3
```
Let us know if that helps.
Regards.

---

### Post by Azyx on 2013-04-23
> **papibe said:**
> Hi Azyx.

You can write a little shell script for that. This would be a simple example:
```
#!/bin/bash

vlc --volume 400 movie.mp4

vlc --volume 200 song.mp3
```
Let us know if that helps.
Regards.

vls want to open movie.mp4 and song.mp3

---

