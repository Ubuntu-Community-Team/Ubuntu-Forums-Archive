---
title: "SImple Image Reducer does not launch (after reinstalls of 18.04)"
date: 2018-11-27
forum: Desktop Environments
---

### Post by pjstock on 2018-11-27
I expect this has been asked many times before but I don't see the answer right away here.

I recently reinstalled 18.04 on two systems. 
Some applications (correction. so far it actually seems that only one, Simple Image Reducer, which I use a lot as I am always needing to make photos smaller, is not launching on either my newly 18.04-ed desktop or my laptop) are not launching from the desktop. double click and... nothing. (though some, which I also reinstalled manually post OS install launch fine.)
Simple Image Reducer for example, which I use a lot. does not launch.

Not having confidence that I would be able to successfully execute the elegant command driven migration of my old /home contents to the new machines, I might have just done a brute force Cut and Paste of files and folders, duplication be damned.)

when I try to laumch it with what I think is the Terminal command (errh would that be just $ simple-image-reducer %U or would it be $sudo simple-image-reducer %U?  or /simple-image-reducer %U..... I never know) but in any event, it doesn't launch from terminal either.

is SIR possibly just obsolete?

---

### Post by again? on 2018-11-28
/usr/bin/simple-image-reducer is a python script.
Appears some python syntax has changed.

I installed on 18.04. Produced error when trying to run.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] simple-image-reducer**
Traceback (most recent call last):
  File "/usr/bin/simple-image-reducer", line 28, in <module>
    import Image
ImportError: No module named Image
```

Searched google for "simple-image-reducer ImportError: No module named Image"
Result [https://stackoverflow.com/a/38713366](https://stackoverflow.com/a/38713366)
> It is changed to : **from PIL.Image import core as image** for new versions.

Edited /usr/bin/simple-image-reducer as root...
```
sudoedit /usr/bin/simple-image-reducer
```
replacing
```
import Image
```
with
```
from PIL.Image import core as image
```

It then started without error.

---

