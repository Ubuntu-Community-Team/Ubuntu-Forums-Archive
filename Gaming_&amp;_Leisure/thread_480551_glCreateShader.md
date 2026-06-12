---
title: "glCreateShader"
date: 2007-06-21
forum: Gaming &amp; Leisure
---

### Post by koma77 on 2007-06-21
When I try to run a game (Danger from the Deep) I get the following OpenGL-related error message:


```

undefined symbol: glCreateShader
```

Anyone know which lib I might be missing?

---

### Post by sommotommo on 2007-12-09
Hi

have the same problem!

Did you solve it in the time between?

Thanks for attention

---

### Post by revanthedarth on 2007-12-21
did you use -lGL -lGLEW -lGLU? Apps using glCreateShader works for me.

I think it's not about GLEW or GLU, but trying is no harm.

---

