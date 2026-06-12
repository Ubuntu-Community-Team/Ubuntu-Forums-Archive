---
title: "No terminal"
date: 2005-05-21
forum: Desktop Environments
---

### Post by Tomppa on 2005-05-21
Ubuntu boots ok and I get to Gnome. But when I press Ctrl-Alt-F1, (or F2-F6) there is no 
command prompt at all. Just blinking cursor. I Can write, and Enter works. But there is no login prompt at all, neither error message of anykind. I can go back to Gnome by pressing Ctrl-alt-F7.
  Have I misconfigured something?

---

### Post by mherring on 2005-05-21
[QUOTE=Tomppa]Ubuntu boots ok and I get to Gnome. But when I press Ctrl-Alt-F1, (or F2-F6) there is no 
command prompt at all. Just blinking cursor. I Can write, and Enter works. But there is no login prompt at all, neither error message of anykind. I can go back to Gnome by pressing Ctrl-alt-F7.
  Have I misconfigured something?[/QUOTE]

I've never seen this trick, but It works on my machine.  Can you get a terminal from the gnome menu?

---

### Post by Tomppa on 2005-05-21
[QUOTE=mherring]I've never seen this trick, but It works on my machine.  Can you get a terminal from the gnome menu?[/QUOTE]

You mean Gnome terminal? It works fine.

---

### Post by mherring on 2005-05-21
[QUOTE=Tomppa]You mean Gnome terminal? It works fine.[/QUOTE]

OK--I'm flying blind here.  There is a way to start with different run levels when you boot.  I dont have it at my fingertips.

The question is if you boot into a terminal mode, then does everything work normally?

---

### Post by Tomppa on 2005-05-22
Now I feel really stupid  ](*,) 

I had made init script for setiathome while a go. It worked fine, at least setiathome launched at startup. But I missed  & from one line, so it got stuck there. Apparently it didn't affect gdm, because it was ran after that, but getty(?) never got started.

---

