---
title: "changing window manager in lubuntu"
date: 2012-08-08
forum: Desktop Environments
---

### Post by abhishektrivedi on 2012-08-08
can I change the window manager of my lubuntu 11.04 from openbox to metacity or any other? If yes then how? Plz help me.

---

### Post by SantaFe on 2012-08-08
> **abhishektrivedi said:**
> can I change the window manager of my lubuntu 11.04 from openbox to metacity or any other? If yes then how? Plz help me.I THINK you can open a term window & type this: metacity --replace &

That should replace openbox with metacity, assuming you HAVE metacity already.  to go back just repeat with openbox in place of metacity.

But I'd wait till someone with more experience than I chimes in. ;)

---

### Post by Austin Texas on 2012-08-08
I am no expert either, but I believe that you can switch to metacity (2d) at the login screen by clicking on the ubuntu logo

---

### Post by MG&amp;TL on 2012-08-08
> **SantaFe said:**
> I THINK you can open a term window & type this: metacity --replace &

That should replace openbox with metacity, assuming you HAVE metacity already.  to go back just repeat with openbox in place of metacity.

But I'd wait till someone with more experience than I chimes in. ;)

That will work, but as soon as you log out, it will die. :)

> **Austin Texas said:**
> I am no expert either, but I believe that you can switch to metacity (2d) at the login screen by clicking on the ubuntu logo

Ubuntu-specific, this is Lubuntu. Nice try, though. Keep at it!

See this post: [http://ubuntuforums.org/showpost.php?p=9875054&postcount=6]("http://ubuntuforums.org/showpost.php?p=9875054&postcount=6") - for compiz, but same principle. I'm sure you get the idea.

---

### Post by abhishektrivedi on 2012-08-09
I tried the procedure given by you and it works but as soon as i close the terminal window , all the window decorations disappear and all the windows come without border. any solution to this problem.

---

### Post by MG&amp;TL on 2012-08-09
> **abhishektrivedi said:**
> I tried the procedure given by you and it works but as soon as i close the terminal window , all the window decorations disappear and all the windows come without border. any solution to this problem.

Given by whom? This sounds like you've run metacity --replace and then killed the process (by closing the terminal).

---

### Post by abhishektrivedi on 2012-08-09
Given by SantaFe. But i found the solution by editing the etc/xdg/lxsession/Lubuntu/autostart
and adding "@matacity --replace" and now metacity is working correctly but I cannot find any tool to configure metacity  themes. Also the right click pop-up menu is not working on desktop .Any Idea?

---

### Post by MG&amp;TL on 2012-08-09
> **abhishektrivedi said:**
> Given by SantaFe. But i found the solution by editing the etc/xdg/lxsession/Lubuntu/autostart
and adding "@matacity --replace" and now metacity is working correctly but I cannot find any tool to configure metacity  themes. Also the right click pop-up menu is not working on desktop .Any Idea?

The menu on the desktop is provided by openbox...

Can't help about the metacity themes, there must be one somewhere.

---

