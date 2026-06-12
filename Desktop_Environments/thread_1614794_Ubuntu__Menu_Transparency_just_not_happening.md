---
title: "Ubuntu / Menu Transparency just not happening?"
date: 2010-11-06
forum: Desktop Environments
---

### Post by smirnoff76 on 2010-11-06
Hi All wonder if someone can point me in the right direction, I have configured my system (ubuntu 10.10) to use Emerald themes and to use Compiz as my window manager. All of my compiz settings are working bar one which is Transparent menus, i.e. click on the Gnome / applications menu and it should be transparent. 
I have enabled opacity and set "Tooltip | Menu | PopupMenu | DropdownMenu | Normal  |" and set opacity to 80, but regardless how much I shift the opacity setting it still isn't giving ma a transparent menu? 
Can any one help? I have attached a screenie showing the compiz opacity settings screen. 

Thanks!!

---

### Post by sikander3786 on 2010-11-06
Just a thought, if you are using Emerald, shouldn't the transparency be configured in Emerald rather than Compiz? You can check emerald-theme-manager for that.

[http://ubuntuforums.org/showthread.php?t=645958](http://ubuntuforums.org/showthread.php?t=645958)

---

### Post by dakukuu on 2010-11-06
How comes you have 4 window icons? What's the new one lol

---

### Post by cracker89 on 2010-11-06
BUMP. Ok. I think the opacity tool in compiz as such becomes active only  when u want to see underlying windows or unactive windows.
 
Notice the cursor positions in both. Further than that, I really do not know how to achieve any envisaged goals you have with it. Not a dire fan of varying opacities myself.
[ATTACH]174747[/ATTACH]
[ATTACH]174748[/ATTACH]


See if that kind of transparency is working.. Or we'll fetch someone else. If you'd already figured that out, well... ahem.. Link us to the wallpaper on ur screenshot tho?

---

### Post by cracker89 on 2010-11-06
> **sikander3786 said:**
> Just a thought, if you are using Emerald, shouldn't the transparency be configured in Emerald rather than Compiz? You can check emerald-theme-manager for that.

[http://ubuntuforums.org/showthread.php?t=645958](http://ubuntuforums.org/showthread.php?t=645958)
  And this makes sense. Try that.. the config manager for Emerald is there in the repository..

---

### Post by mcduck on 2010-11-06
Instead of trying to use the "Opacify"-plugin, try using the "Opacity, Brightness and Saturation"-plugin.

Also, you are missing part of the window matching rule, try something like this instead:

```
(class=Menu|PopupMenu|DropdownMenu)
```

..and no, Emerald has nothing to do with this. It's just a window decorator plugin for Compiz, and thus only controls how the window borders look like. Not anything happening inside the window itself.

---

### Post by smirnoff76 on 2010-11-06
Thanks mcduck Opacity, Brightness and Saturation was the answer

---

### Post by mkarl on 2010-11-06
wow cool, just stopped by and wanted to say thanks for this thread, I'd given up hope a while ago doing this cos I couldn't get it to work, but nice one! :KS

Karl :)

---

