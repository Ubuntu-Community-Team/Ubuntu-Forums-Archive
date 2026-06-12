---
title: "My big problems with World of warcraft"
date: 2006-09-17
forum: Gaming &amp; Leisure
---

### Post by Toan on 2006-09-17
Well i finaly found out how to get wow onto linux but im haveing some problems with the grafix :frown: file:///home/admin/Desktop/Screenshot.png
look at this its sad right? well please if you know how to fix it please tell me.:D cmon you know u want to.

---

### Post by hopstah on 2006-09-17
a little tip:  preview your posts before you submit them so that you don't have to submit three copies of the exact same thing.  also - you can't link to something that sits resident on your hard drive.  you first need to upload it to a site and then link to that site.

---

### Post by hikaricore on 2006-09-17
i'm just going to go super psychic here and tell you:

```
wine WoW.exe -opengl
```

just based on the limited info you've provided and how many times i've read this same exact question (usually more well worded).  if that doesn't work make sure the correct graphic driver for your video card is installed.

also check to see if you have direct rendering enabled

```
glxinfo
```

it will be at the top of the output, if it says no, WoW will never run correctly until you resolve this, and your making your comp do all the work for the video card and trust me it sucks at this.

last thing you might wanna check

```
glxgears
``` or ```
glxgears --showfps
```

depending on the version of the app you have installed, if your fps is crap on 3 little flat rendered gears, WoW will run like crap until you resolve the issue.

but like hop said: preview, upload, then post.

kthxbi

---

