---
title: "Blank Gnome desktop on login"
date: 2009-05-08
forum: Desktop Environments
---

### Post by cb372 on 2009-05-08
When I boot and login, I am faced with an almost blank Gnome desktop. 

What I have:

[LIST]
[*]Top panel (menus, but no applets)
[*]Bottom panel
[*]Ability to run programs from terminal with no problems
[/LIST]
What I don't have:

[LIST]
[*]Icons on desktop
[*]Files on desktop
[/LIST]
If I switch console (e.g. Ctrl+Alt+F3) and then switch back to X (Ctrl+Alt+F7) then everything is magically fixed! All of my applets and desktop contents have appeared.

I've been trying to remember when this first started happening. It's definitely after I upgraded to Jaunty, but I can't say for sure that it's directly related to the upgrade. Other than that, I can't think of any package installs/uninstalls that may have caused this.

I had a quick look through /var/log/messages etc and couldn't see anything out of the ordinary.

Has anybody else had this problem? Any hints on where to start looking for clues?

Thanks in advance.

---

### Post by gettinoriginal on 2009-05-09
Try Alt F2, type in gconf-editor, Run, select apps, nautilus, preferences, and be sure that "show desktop" is checked.

---

### Post by CyyberSpaceCowboy on 2009-05-09
Exact same problem here, definitely happened as a result of Jaunty upgrade (otherwise I like Jaunty, boots wicked fast even on this old single core non multi-threaded CPU).  "show desktop" is checked (thanks for the tip on gconfig editor, learn some new Linux every day :).  My links and files are still there in home/username/desktop, I just can't see them.

---

### Post by CyyberSpaceCowboy on 2009-05-09
I re-read cb372's post, I do have apps in my menus and they work.  Switching to terminal and back again doesn't change anything for me.

---

