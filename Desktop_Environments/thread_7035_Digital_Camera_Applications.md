---
title: "Digital Camera Applications"
date: 2004-12-03
forum: Desktop Environments
---

### Post by mattyh on 2004-12-03
I am looking for a good linux program to do some common tasks like removing redeye and maybe some color balancing.  Any that people would recommend?  Thanks.

---

### Post by JonAtkinson on 2004-12-06
gThumb will do simple colour balancing. I don't think it'll do red-eye reduction, though.

When I insert my digicam (A Fuji FinePix), the fact it's a camera is automatically detected, and gThumb is started. If you camera isn't detected like this, use Applications/Graphics/gThumb or /usr/bin/gthumb

--Jon

---

### Post by randy on 2004-12-07
There's a tutorial for the Gimp that's at the gimp website on redeye reduction.

---

### Post by rubycon on 2004-12-26
[QUOTE=JonAtkinson]gThumb will do simple colour balancing. I don't think it'll do red-eye reduction, though.

When I insert my digicam (A Fuji FinePix), the fact it's a camera is automatically detected, and gThumb is started. If you camera isn't detected like this, use Applications/Graphics/gThumb or /usr/bin/gthumb

--Jon[/QUOTE]


I own a Fuji FinePix myself. I can mount it manually but no automated process, such as gthumb, is run when I connect it. So I started gthumb manually but it can't find my camera. A few Fuji cameras appears in the list of models. However the FinePix is not present. Did you have to set anything up to get it to work?

EDIT: 
Problem solved! The reason it didn't work was because I hadn't added my user to the 'plugdev' group. Now it works like a charm.

---

