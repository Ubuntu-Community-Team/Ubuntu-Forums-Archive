---
title: "Problem with resolution when I used a projector!"
date: 2006-01-29
forum: Desktop Environments
---

### Post by rozojc on 2006-01-29
I have a question; When I connect an LCD projector to the back of my laptop I can't send the video through it (meaning I press the Function button I use in Windows and it doesn't work). However, if I boot with the thing plugged to my laptop then it does work, but KDE comes up at 640x480 and I it doesn't let me change the resolution (however in Windoze it does work at higher resolutions). Any ideas?

---

### Post by DrBair on 2006-02-01
First off, what kind of laptop is it that we are dealing with? Many laptops need software to enable things like this.

For the resolution, you could try disabling DDC in xorg.conf and then forcing it to a resolution.

---

### Post by rozojc on 2006-02-01
It's an Acer 3003LCi. I'll try what you said and report my results, although I do think these kind of things should work out of the box.

---

### Post by localzuk on 2006-02-01
These sort of things do not work out of the box on Windows. It requires software that is created by the graphic's card manufacturers. Linux doesn't get this sort of support from manufacturers as it is not worth it to them yet.

What you require is screen cloning, here is a thread which discusses multiple screens. [http://www.ubuntuforums.org/showthread.php?t=122646](http://www.ubuntuforums.org/showthread.php?t=122646)

---

