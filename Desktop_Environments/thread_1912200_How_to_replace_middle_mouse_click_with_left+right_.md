---
title: "How to replace middle mouse click with left+right click?"
date: 2012-01-20
forum: Desktop Environments
---

### Post by polomora on 2012-01-20
Hello,

I have a MS optical scrolling mouse, where the scroll wheel doubles up  as the middle mouse button. I find that when scrolling, I sometimes  press too hard and accidentally activate the middle mouse button  feature, resulting in unexpected text inserts.

Does anyone know how to replace the middle mouse button with simultaneously holding down the left and right mouse buttons?

I tried using xinput:
```
# xinput get-button-map 10
1 2 3 4 5 6 7
# xinput set-button-map 10 1 0 3
```But this removes both the middle key and the left+right push key functionality.

I also tried installing gpointing-device-settings, but this didn't do  anything. It gave the following error, don't know if this is  significant:
```
# gpointing-device-settings
An X error occurred. The error was BadAtom (invalid Atom parameter).
```Can anyone help?

Many thanks,
Paul

---

