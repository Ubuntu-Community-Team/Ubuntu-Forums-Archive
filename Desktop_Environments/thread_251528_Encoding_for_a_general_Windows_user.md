---
title: "Encoding for a general Windows user"
date: 2006-09-05
forum: Desktop Environments
---

### Post by duff on 2006-09-05
At work I need to encode a series of JPEGs to a movie file and send them to various people at other universities.  A majority of these people are Windows users and I'd like to be able to send movies without having them install additional codecs.  So, what mencoder command can I give to encode JPEGs, of arbitrary size (so MPEG1 is out), that'll work on any basic Windows XP machine?  Currently, I use

```
# mencoder  "mf://*.jpg" -mf fps=24 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4
```

But the mpeg4 codec is not in Windows Media Player by default.

Any help on this would be greatly appreciated.

---

