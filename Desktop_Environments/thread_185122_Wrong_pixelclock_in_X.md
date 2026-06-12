---
title: "Wrong pixelclock in X"
date: 2006-05-31
forum: Desktop Environments
---

### Post by brsseb on 2006-05-31
Im told to use the following modeline for my monitor, a Dell 24" (2405):

```

Modeline"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235 +HSync -Vsync
```

For the monitor to work in perfect 1920x1200@60hz, the pixel clock MUST be 154 dead on. But using the above modeline, which explicitly s](*,) ay i want 154MHz, results in the monitors clock being 193-194Mhz instead! Thats why i get the distorted picture! 

But i asked for 154MHz. Its not ignoring my modeline, since if i change any setting in it, it results in either a "cannot display this mode"-error, x crash, or just a more distorted image. 

Does anyone know why im not getting my desired pixelclock?

---

