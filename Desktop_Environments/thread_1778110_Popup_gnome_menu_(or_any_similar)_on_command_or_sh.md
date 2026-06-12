---
title: "Popup gnome menu (or any similar) on command or shortcut."
date: 2011-06-08
forum: Desktop Environments
---

### Post by Elline on 2011-06-08
Hello.
Didn't knew where to ask about it, through maybe it is related to desktop environments.

Just wondering is there any existing way to show any gnome(2)-like menu on shortcut or command.

What I want really is make a menu appear by touching screen border by associating one of the screen corners with a command in compiz.

I saw some kind of menu myGtkMenu, but it is an additional entity. It would be perfect if I can associate menu popup with a command like I can do in "Keyboard Shortcuts", but there is only key shortcuts awailable, though I need a corner touch.

Thanks in advance and sorry for my freaky English.

---

### Post by Elline on 2011-06-16
No chances for me?

---

### Post by jerrrys on 2011-06-16
don't use it, but sounds like "brightside" it's in the software center

---

### Post by Elline on 2011-06-16
Should look for that, thank you for reply!

Wow, it looks like you found answer for my another [topic]("http://ubuntuforums.org/showthread.php?p=10946492#post10946492")!

But I can associate actions (i.e. commands) with screen corners from just compiz. But I can't figure out is there a command to show a gnome menu.

---

### Post by Elline on 2011-06-16
Oh, well. I installed that brightside, but it looks like it is actually not switching the desktops, maybe conflicting with compiz. But it is out of topic really.
Also, this software looks really outdated, even is's website is down.

---

### Post by jerrrys on 2011-06-16
as long as its in the software center, it has a maintainer.  i have gone as far as i can.  good luck

---

### Post by Elline on 2011-06-17
Yes, thank you very much! It is just conflicting with compiz that's the problem.

Any other suggestions? Just a menu that pops out by a command?

---

### Post by jerrrys on 2011-06-18
perhaps a compiz user will stop on in...

---

### Post by stinkeye on 2011-06-18
Do you want a menu like 10.10?
There is an indicator [**_[COLOR="DarkRed"]here[/COLOR]_**]("http://www.florian-diesch.de/software/classicmenu-indicator/")
Which will display a menu like in maverick.

Download and install the **classicmenu-indicator_0.03_all.deb** file
and to run hit alt+F2 and enter
```
classicmenu-indicator

```

---

### Post by Elline on 2011-06-19
> **stinkeye said:**
> Do you want a menu like 10.10?
There is an indicator [**_[COLOR="DarkRed"]here[/COLOR]_**]("http://www.florian-diesch.de/software/classicmenu-indicator/")
Which will display a menu like in maverick.

Download and install the **classicmenu-indicator_0.03_all.deb** file
and to run hit alt+F2 and enter
```
classicmenu-indicator

```

Sorry, it is not what I want.

I need a menu that appears on command. So I can associate that command, for example, "super-menu-show" with a screen corner and make appear that way.

---

### Post by stinkeye on 2011-06-19
Don't undestand.
A menu for what?

You can use xdotool to run keyboard shortcuts.
eg
```
xdotool key Super+a
```

and use in ccsm > commands.

---

### Post by Elline on 2011-06-21
> **stinkeye said:**
> Don't undestand.
A menu for what?
A menu with applications. Like in gnome2, or that you suggested.

---

### Post by Elline on 2011-06-21
Oh, thank you very much!

I have found a solution with xdotools.

---

### Post by komealy on 2012-03-12
I was actually looking for a very similar situation as this and I was wondering what the solution actually was. I'll look into it and see if I can figure it out anyway. Thanks in advance.

---

### Post by komealy on 2012-03-12
> **Elline said:**
> Oh, thank you very much!

I have found a solution with xdotools.


I was actually looking for a very similar situation as this and I was wondering what the solution actually was. I'll look into it and see if I can figure it out anyway. Thanks in advance.

---

