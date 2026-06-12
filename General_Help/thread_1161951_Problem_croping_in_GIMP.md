---
title: "Problem croping in GIMP"
date: 2009-05-17
forum: General Help
---

### Post by Bernie Power on 2009-05-17
I am finding that I can only crop an image with GIMP if GIMP is started as root. Some actions like rotating, skewing, flipping, brightness and applying filters work fine as user. Croping and text seem not to work. The image file permissions are all rw.
I have resently upgraded to 9.04 with some other minor issues. 
GIMP 2.6.6

Has anyone any idea how to resolve this one?
Thanks B.P.

---

### Post by Legace on 2009-05-17
Try this in Terminal:

```
rm -rf ~/.gimp-2.6
```
Then see if GIMP works under user.

---

### Post by Bernie Power on 2009-05-18
Thankyou Legace for the input.
That has sorted out my problem.
Cheers
Bernie

---

