---
title: "Move automatically new windows to another destop"
date: 2010-03-12
forum: Desktop Environments
---

### Post by pedazovago on 2010-03-12
Hi:

First sorry for my English, second in thanking everyone for the great community mounted, very helpful for newbies like me

Finally my question. I've been looking for a window manager that allows me two things, send new windows to another desktop automatically, and when a window receives a desk run a program automatically.

I tested with fvwm but I have not been able to.

thanks for the help[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by Barriehie on 2010-03-13
Devilspie can do some of what you ask:
[http://ubuntuforums.org/showthread.php?t=98071](http://ubuntuforums.org/showthread.php?t=98071)

---

### Post by pedazovago on 2010-03-13
> **Barriehie said:**
> Devilspie can do some of what you ask:
[http://ubuntuforums.org/showthread.php?t=98071](http://ubuntuforums.org/showthread.php?t=98071)

Thanks. This program are perfect for that , and link are very interesting 
[COLOR=#010122][FONT=sans-serif][/FONT][/COLOR]

---

### Post by Barriehie on 2010-03-14
> **pedazovago said:**
> Thanks. This program are perfect for that , and link are very interesting 

Glad to help!

---

### Post by jpkotta on 2010-03-14
In Fvwm, ```
Style <window matcher> StartsOnDesk <number>
```

Also in Fvwm, you can run a function whenever a window is mapped with the InitalMapCommand style.  One of the things you can do with commands is run applications.  Here's an example of such a command:
```

DestroyFunc StartMyApp
AddToFunc StartMyApp
+ I Exec exec myapp

Style some_window_name StartsOnDesk 0
Style some_window_name InitialMapCommand StartMyApp

```

---

### Post by ThomasAdam on 2010-03-31
> **jpkotta said:**
> 
```

DestroyFunc StartMyApp
AddToFunc StartMyApp
+ I Exec exec myapp

Style some_window_name StartsOnDesk 0
Style some_window_name InitialMapCommand StartMyApp

```

**Don't do this** -- it's going to spawn a lot of windows that way -- when I wrote support for this, it was never intended to find a use like this.  That's completely *disasterous* if myapp and some_window_name match.

-- Thomas Adam

---

### Post by jpkotta on 2010-04-02
> **ThomasAdam said:**
> **Don't do this** -- it's going to spawn a lot of windows that way -- when I wrote support for this, it was never intended to find a use like this.  That's completely *disasterous* if myapp and some_window_name match.

-- Thomas Adam

Of course, but it's fine if myapp doesn't even make windows.

---

