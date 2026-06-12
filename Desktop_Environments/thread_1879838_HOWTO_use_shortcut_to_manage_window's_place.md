---
title: "HOWTO use shortcut to manage window's place"
date: 2011-11-12
forum: Desktop Environments
---

### Post by chao787 on 2011-11-12
I am using xubuntu 11.10 in my laptop.
And I want to set window at top-left corner or take left hlf space of screen, or some similar behaviors (using instructions in terminal or just shortcut keys in global area).
In gnome 2.x, I can using ccsm to set these shortcut in a convenient way. But I don't know how to set it in xfce.

I have searched through google and our forum up and down, and only  (G)devilspie or wmctrl may help me. Yet, I do't think I can manage these in a mature way.

Xfce is a mature X, and I think someone must have a tricky method to do this common task.

Sorry about my poor English.

---

### Post by Toz on 2011-11-12
Hello and welcome to the forums.

Devilspie will probably do what you're looking for. See: [http://burtonini.com/blog/computers/devilspie/]("http://burtonini.com/blog/computers/devilspie/") and [https://help.ubuntu.com/community/Devilspie]("https://help.ubuntu.com/community/Devilspie").

---

### Post by chao787 on 2011-11-13
> **Toz said:**
> Hello and welcome to the forums.

Devilspie will probably do what you're looking for. See: [http://burtonini.com/blog/computers/devilspie/]("http://burtonini.com/blog/computers/devilspie/") and [https://help.ubuntu.com/community/Devilspie]("https://help.ubuntu.com/community/Devilspie").

Hi Toz!
Thank u, but devilspie only adjust and control window at its starting time. But I wanna find a way to control these window using shortcuts. 

How do you manage your window if using keyboard only? Just using alt-F10 to max it?

---

### Post by Toz on 2011-11-13
How about wmctrl? Looks like it can adjust windows on the fly. The following resizes and moves the xchat window to the top-left corner for me:
```
wmctrl -r xchat -e 0,0,0,500,500
```
You can easily add that command to a keyboard shortcut.

---

### Post by chao787 on 2011-11-13
Opps, Great.
And I also found an alternative software to manage window.(may be more suitable about this task.)
[http://manpages.ubuntu.com/manpages/lucid/man1/xdotool.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/xdotool.1.html)

I think write some script inside can manage it better, no matter using which which tool, and just like code emacs.. 
hej-hej........
Any code suggestions?

---

