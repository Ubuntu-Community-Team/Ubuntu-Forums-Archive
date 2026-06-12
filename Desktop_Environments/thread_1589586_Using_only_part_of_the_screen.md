---
title: "Using only part of the screen"
date: 2010-10-06
forum: Desktop Environments
---

### Post by Phyr on 2010-10-06
Hi everyone,
my laptop is kinda broken and the right part of my 1440x900 display doesn't work anymore (all black). I think i have around 1200x900 left on the left side. Is there a way to tell X to only use those for displaying the desktop?
Does this work with other application using "fullscreen" ?
Thanks for the help,
Phyr


schematic of the display:
OOOOOOXX
OOOOOOXX
OOOOOOXX

O: works
X: black
So the desktop should only span the O-part

---

### Post by roggenschrotbrot on 2010-10-06
read into RandR
[http://ubuntuforums.org/showthread.php?t=562202](http://ubuntuforums.org/showthread.php?t=562202)
it should work the other way around as well. your video driver might offer the option to disable stretching the image to full size if the resolution is lower then native, so you can just set a lower horizontal resolution and be done.

edit: attached an image of what to look for if you are using a nvidia gpu

---

### Post by Phyr on 2010-10-13
Sadly my driver doesn't support this option (old radeon x700 mobile) and RandR can handle lager virtual resolutions very well, but not the other way round, as the native size has to fit into the virtual one. I found other threads with the same question with none of them satisfactorily answered. So if there is a way I would be greatly pleased and grateful to hear of it.

Edit: For the nvidia driver thing i would need a resolution not supported by my monitor, which the driver doesn't seem to let me do.

---

