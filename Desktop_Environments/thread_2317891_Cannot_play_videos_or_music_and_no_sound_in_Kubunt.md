---
title: "Cannot play videos or music and no sound in Kubuntu with KDE 5.5.4"
date: 2016-03-21
forum: Desktop Environments
---

### Post by tk83 on 2016-03-21
Started computer and found that music couldn't be played - tried both Spotify and Clementine, both showed the play progress bar not moving and no music coming out. Tried sound test on Youtube, but no Youtube videos could play. Tried as a different user and found the problem didn't exist. 

This was on Kubuntu 15.10 with KDE 5.5.4 (from their KDE backports repo). 

Found that the following run as my user fixed the problem:
```
rm ~/.cache/event-sound-cache.tdb.7b1c138151f60cc9b86d033a56786c2b.x86_64-pc-linux-gnu
```

Hope that helps anyone who encounters the same problem!

---

