---
title: "Cedega &amp; Anarchy Online problems"
date: 2005-10-15
forum: Gaming &amp; Leisure
---

### Post by Minne on 2005-10-15
Hello, I have successfully installed Anarchy Online but I get 1 fps or less when I try to run it. 
Is there anyone who has an idea what could be done?

It doesn't help to lower the graphics to minimum either.

Thanks for any ideas what I could do about it.

---

### Post by seethru on 2005-10-16
Sounds like you haven't installed your video cards drivers

Whats the output of this?
```
$ glxinfo | grep render
```

---

### Post by Minne on 2005-10-16
This was the output.
"direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20050225 x86/MMX/SSE2"

---

### Post by seethru on 2005-10-16
is that an onboard video card? I'm not too sure whether you can get 3d acceleration working on one of those, and unfortunately MESA isn't gonna give you great performance in games.

---

### Post by Vidar on 2005-10-17
[QUOTE=seethru]is that an onboard video card? I'm not too sure whether you can get 3d acceleration working on one of those, and unfortunately MESA isn't gonna give you great performance in games.[/QUOTE]

It's an onboard Intel GPU, but it's not horribly slow. It can play Enemy Territory with no problems at all in my experience.

---

