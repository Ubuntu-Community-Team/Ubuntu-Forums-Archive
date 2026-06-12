---
title: "Type in unfocused window"
date: 2012-02-24
forum: Desktop Environments
---

### Post by jere.the.miah on 2012-02-24
Say I have two terminal windows open, one full screen and one windowed. When the windowed terminal is focused I'd like to type in the unfocused fullscreen window and still be able to see the windowed terminal to reference it's output. Currently to type in the  fullscreen window i have to click it and it covers up the windowed terminal. I tried messing with gconf-editor "focus_mode" but it still covers up the windowed terminal. do i need compiz for something like this?

---

### Post by Krytarik on 2012-02-24
> **jere.the.miah said:**
> I tried messing with gconf-editor "focus_mode" but it still covers up the windowed terminal. do i need compiz for something like this?
Well, it works for me with that setting set to "sloppy", with Metacity. And equally well with Compiz. What version of Ubuntu, what DE/session, and what window manager are you using?

Regards.

---

### Post by jere.the.miah on 2012-02-27
ubuntu maverick 10.10 kernel 2.6.35-32

I found it, I needed to _uncheck _"auto_raise" and set "focus_mode" to "sloppy". Thanks for the help with the sloppy option.

---

