---
title: "Compiz update took away my cube pictures"
date: 2006-09-07
forum: Desktop Environments
---

### Post by PathSpace on 2006-09-07
I just updated Compiz, and the picture I set for the top and bottom of the cube are no longer there (just blank white screens), even though the images are set in csm.  :confused:

---

### Post by turbojugend_gr on 2006-09-07
Notice I am not using Csm, since I have not upgraded to it, I am a little bit of a chicken on this one....;) 

Anyway I think you should try to set another picture for top and bottom of the cube, see if it works with them, and if it does try re-seeting your favourites, if the problem still occurs, try renaming the pictures or moving them to another catalogue, it worked fine for me with Gset when I had the same issue...

On the other hand I am not sure, as I hadn't used csm still, but I can't see any harm in trying it. Oh by the way can you plz post your view on this post? 
[http://www.ubuntuforums.org/showthread.php?p=1473318&posted=1#post1473318](http://www.ubuntuforums.org/showthread.php?p=1473318&posted=1#post1473318)
I am desperate on collecting some info...;) . 

Anyhow, let me now how it works for you, I hope this will do the trick!

---

### Post by PathSpace on 2006-09-07
I tried deleting, then re-setting the picture, but to no avail.  And regarding whether or not you should upgrade...I'm no expert but I don't think it would mess you up terribly.

---

### Post by turbojugend_gr on 2006-09-07
Did you set another picture to check that case out?

---

### Post by ayoli on 2006-09-07
strange, but nice that i havent got this problem.
i had to reset my images after first release of csm and they have never gone.

---

### Post by Dinerty on 2006-09-07
> **PathSpace said:**
> I just updated Compiz, and the picture I set for the top and bottom of the cube are no longer there (just blank white screens), even though the images are set in csm.  :confused:

Did you change the permission to directory?

```
chmod 755 ~/.compiz -R
```

if not, you will be able to change the images but they will not be saved and it will use the default novel ones

---

### Post by PathSpace on 2006-09-07
Yes, I changed directory permissions, and my changes get saved, but my desktop bottom/top is just blank.  :|

---

