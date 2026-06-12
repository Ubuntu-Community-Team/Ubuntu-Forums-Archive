---
title: "How do I switch from Compiz to Emerald?"
date: 2009-08-08
forum: Desktop Environments
---

### Post by vizitorq on 2009-08-08
I'm not sure exactly how this works, as the research I have done has led to some really complex stories. First there was beryl, then compiz, then they merged, then from somewhere emerald comes into play, but it's still part of compiz??? what the heck?

What I want is very simple... It's easy to change Themes in my Window Manager. I want to be able to change from Compiz to Emerald, and be able to switch Emerald and Compiz themes just as easily. How do I do this?

---

### Post by BinaryFeast on 2009-08-08
You don't actually need to switch between them. Compiz is a window manager that can use Emerald as its window decorator. So you'll wan't to have both on at the same time. I'd recommend installing fusion-icon:

```
sudo apt-get install fusion-icon
```Find it in the menu and start it. The icon should show up in the panel. Right click the icon and you'll have some options to switch both window managers and decorators.

---

### Post by mcduck on 2009-08-08
> **vizitorq said:**
> I'm not sure exactly how this works, as the research I have done has led to some really complex stories. First there was beryl, then compiz, then they merged, then from somewhere emerald comes into play, but it's still part of compiz??? what the heck?

What I want is very simple... It's easy to change Themes in my Window Manager. I want to be able to change from Compiz to Emerald, and be able to switch Emerald and Compiz themes just as easily. How do I do this?
You don't switch from Compiz to Emerald. You use Emerald *with* Compiz, not instead of it.

Unlike other window managers, Compiz doesn't handle drawing of window borders itself. Instead it uses plugins it calls "window decorators" to do that. By default Compiz in Ubuntu uses gtk-window-decorator, which allows using Metacity's themes. And Emerald is another window decorator.

To use Emerald instead of gtk-window-decorator open CompizConfig Settings Manager (install it if you haven't done that already), then go to Window Decoration-plugin's settings and set the Command-field to /usr/bin/emerald. Now when Compiz starts it loads Emerald as it's decorator.

---

### Post by Volguuz on 2009-08-15
> **mcduck said:**
> You don't switch from Compiz to Emerald. You use Emerald *with* Compiz, not instead of it.

Unlike other window managers, Compiz doesn't handle drawing of window borders itself. Instead it uses plugins it calls "window decorators" to do that. By default Compiz in Ubuntu uses gtk-window-decorator, which allows using Metacity's themes. And Emerald is another window decorator.

To use Emerald instead of gtk-window-decorator open CompizConfig Settings Manager (install it if you haven't done that already), then go to Window Decoration-plugin's settings and set the Command-field to /usr/bin/emerald. Now when Compiz starts it loads Emerald as it's decorator.

Hi mcduck, i am trying to acomplish the same, i'm running Kubuntu 9.04 got compiz and emerald installed and configured the way you described it. Even got the compiz icon and it is set for the emerald theme.

But it still won't load the Emerald Themes, any ideia on how to fix this?

Thank you.

---

