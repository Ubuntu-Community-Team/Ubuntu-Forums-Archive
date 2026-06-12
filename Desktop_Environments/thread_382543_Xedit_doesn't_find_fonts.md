---
title: "Xedit doesn't find fonts"
date: 2007-03-12
forum: Desktop Environments
---

### Post by xurios on 2007-03-12
Has anyone gotten xedit to work with ubuntu? It is not in the ubuntu xclients-base package (it is in the debian package, but that one don't work for me), so I built xedit, after installing libxaw7-dev. That part worked, but xedit doesn't find the fonts it needs and aborts at startup. 

```

Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Error: Aborting: no fontset found

```

Now, mind you, I don't care much for xedit, but my mom is totally dependent on it. She doesn't like those "new fangled" GUI type text editors like vi or emacs (!). I upgraded her from redhat 6 or something like that last Christmas when I was visiting, so she could have a media capable system, but I didn't realize that there would be problems with the change from xfree86 to xorg. I figure I can get it working then send her some files and some instructions and then she can also get it working. She's using AXE, but misses xedit and complains every time I call her. I thought she could try THE, but it seems that it's xedit compatible mode is only slightly xedit compatible.

 
I think if I spent about 20 to 40 hours educating myself about xorg vs. xfree86 and maybe tracing differences in how the fonts are organized I could get something working, but I am hoping someone here might have a suggestion of a more efficient solution for me :) I guess I could always put her on fedora next Christmas, or maybe someone has an xedit.el file to make emacs work like xedit a bit?

---

