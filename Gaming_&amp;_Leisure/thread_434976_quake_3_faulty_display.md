---
title: "quake 3 faulty display"
date: 2007-05-06
forum: Gaming &amp; Leisure
---

### Post by eosinophil on 2007-05-06
i got ubuntu edgy 6.10 with gnome 
i got quake 3 running after a while..
btw ..simple question : commands executed :
$>quake3 (worked)
$>su-
$>su me
$>quake3 (IT DIDN'T WORK)

i get it...u gotta launch q3 with the same user u logged in to X but..really...is this normal..?
anyways..this is not the main problem..
the problem is that i got it runnin as i said but its really faulty..the screen is all an artefact :) i mean u can vaguely see stuff like weapons or something..not even close to being able to read the menus..

maybe someone can point me in some direction..
thank you.

sorry for any spelling mistakes, english is not my native language.

---

### Post by buttons on 2007-05-06
> **eosinophil said:**
> i got ubuntu edgy 6.10 with gnome 
i got quake 3 running after a while..
btw ..simple question : commands executed :
$>quake3 (worked)
$>su-
$>su me
$>quake3 (IT DIDN'T WORK)

i get it...u gotta launch q3 with the same user u logged in to X but..really...is this normal..?


Sure.  From the su man page:

>        su is used to become another user during a login session. Invoked
       without a username, su defaults to becoming the super user. The
       optional argument - may be used to provide an environment similar to
       what the user would expect had the user logged in directly.

So...you used su - which became superuser with the superuser's environment variables, and then su user which became you, but with the superuser's environment variables still.  It's confusing and silly, which is one of the many reasons why ubuntu disables superuser by default.  So don't use it!

> **eosinophil said:**
> anyways..this is not the main problem..
the problem is that i got it runnin as i said but its really faulty..the screen is all an artefact i mean u can vaguely see stuff like weapons or something..not even close to being able to read the menus..

maybe someone can point me in some direction..
thank you.

Be sure you have direct rendering enabled for your video card.  Try this command:

```
glxinfo |head -n 3
```

Which should give something along the lines of
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
```

If direct rendering is No, then you need to install the restricted drivers for your card if it is an ATi or NVidia card.

---

