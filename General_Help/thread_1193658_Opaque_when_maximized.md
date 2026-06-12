---
title: "Opaque when maximized"
date: 2009-06-21
forum: General Help
---

### Post by warrenis1234 on 2009-06-21
I've searched but came up empty, and i saw the post in these forums of a guy trying to see if the window could b transparent while the video like youtube remains opaque... well i believe there is a way to at least in compiz to cancel out the window transparency setting when the window is maximized

am i right?  and if i am, how do i do it, what do i type in?

thanks

---

### Post by warrenis1234 on 2009-06-21
anyone?  if you know the answer is elsewhere, that would be helpful too

---

### Post by kapcom01 on 2009-11-15
i know it may be too late for the solution but i have it anywhay:p

go to CompizConfig Settings Manager > Opacity, Brightness and Saturation
click New under the Window specific settings
add this command:```
(state=maxvert | maxhorz)
```and click Up to bring it on the top.

---

### Post by warrenis1234 on 2009-11-16
> **kapcom01 said:**
> i know it may be too late for the solution but i have it anywhay:p

go to CompizConfig Settings Manager > Opacity, Brightness and Saturation
click New under the Window specific settings
add this command:```
(state=maxvert | maxhorz)
```and click Up to bring it on the top.

definitely wasnt too late, thanks a lot for this.   strangely enough, a maximized video is still transparent...   know how to stop that?

---

### Post by kapcom01 on 2009-11-21
> **warrenis1234 said:**
> definitely wasnt too late, thanks a lot for this.   strangely enough, a maximized video is still transparent...   know how to stop that?


Try this instead:
```
(state=maxvert) | (state=maxhorz) | (state=Fullscreen)
```
and again move this command on top of all others and set it to 100

---

### Post by warrenis1234 on 2009-11-21
> **kapcom01 said:**
> Try this instead:
```
(state=maxvert) | (state=maxhorz) | (state=Fullscreen)
```
and again move this command on top of all others and set it to 100

perfect, thanks a lot, you saved the beauty of my desktop

---

