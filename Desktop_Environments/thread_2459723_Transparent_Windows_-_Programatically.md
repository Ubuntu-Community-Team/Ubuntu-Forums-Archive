---
title: "Transparent Windows - Programatically"
date: 2021-03-24
forum: Desktop Environments
---

### Post by bobtedbob on 2021-03-24
Hi

I understand how to make windows transparent using x11 commands but I want to programatically create a transparent window. I am using GLFW and it has functionality to support this if the OS supports it.

[https://www.glfw.org/docs/3.3/window_guide.html#window_transparency](https://www.glfw.org/docs/3.3/window_guide.html#window_transparency)

I am running Ubuntu 20.04 but when running GLFW it gives the impression that the OS is not supporting it. Is there anything I need to do to enable GLFW to display transparent windows?

Thanks

---

### Post by norobro on 2021-03-24
> **bobtedbob said:**
> I am running Ubuntu 20.04 but when running GLFW it gives the impression that the OS is not supporting it.
What gives you that impression? Care to show some code?

Works fine on my box:
[ATTACH=CONFIG]288179[/ATTACH]

---

### Post by bobtedbob on 2021-03-25
When I run 

[glfwWindowHint]("https://www.glfw.org/docs/3.3/group__window.html#ga7d9c8c62384b1e2821c4dc48952d2033")[COLOR=#4D4D4D][FONT=monospace]([/FONT][/COLOR][GLFW_TRANSPARENT_FRAMEBUFFER]("https://www.glfw.org/docs/3.3/group__window.html#ga60a0578c3b9449027d683a9c6abb9f14")[COLOR=#4D4D4D][FONT=monospace], [/FONT][/COLOR][GLFW_TRUE]("https://www.glfw.org/docs/3.3/group__init.html#ga2744fbb29b5631bb28802dbe0cf36eba")[COLOR=#4D4D4D][FONT=monospace]);

and then create the window I get 0 returned from this query

[/FONT][/COLOR][glfwGetWindowAttrib]("https://www.glfw.org/docs/3.3/group__window.html#gacccb29947ea4b16860ebef42c2cb9337")[COLOR=#4D4D4D][FONT=monospace](window, [/FONT][/COLOR][GLFW_TRANSPARENT_FRAMEBUFFER]("https://www.glfw.org/docs/3.3/group__window.html#ga60a0578c3b9449027d683a9c6abb9f14")[COLOR=#4D4D4D][FONT=monospace])

I can make the whole window transparent using 

[/FONT][/COLOR][glfwSetWindowOpacity]("https://www.glfw.org/docs/3.3/group__window.html#gac31caeb3d1088831b13d2c8a156802e9")[COLOR=#4D4D4D][FONT=monospace](window, 0.5f);

but I specifically just want the frame buffer ( so I can determine whats transparent and whats not)

[/FONT][/COLOR]

---

### Post by norobro on 2021-03-25
Do you have compositing enabled? 

From here: [https://www.glfw.org/docs/3.3/window_guide.html#window_transparency](https://www.glfw.org/docs/3.3/window_guide.html#window_transparency)> [COLOR=#4D4D4D][FONT=Roboto]If supported by the system, the window content area will be composited with the background using the framebuffer per-pixel alpha channel. This requires desktop compositing to be enabled on the system. It does not affect window decorations.[/FONT][/COLOR]

---

### Post by bobtedbob on 2021-03-26
How do [FONT=arial]I enabl[COLOR=#000000]e *desktop compositing ?*[/COLOR][/FONT]

---

