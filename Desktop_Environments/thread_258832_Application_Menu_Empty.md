---
title: "Application Menu Empty"
date: 2006-09-16
forum: Desktop Environments
---

### Post by jonwatson on 2006-09-16
I'm not sure what happened, but my applications menu is now empty. When I click on it, I get a little white square with nothing in it.

When I create a new user, that user's menu is fine. 

I've tried to copy the .gnome* directories from a working user over to my directory and while that does reset my panels, it doesn't fill in the Applications menu.

I think what I need to know is where the menus are stored so I can grab them from another user.

Ideas?

---

### Post by lukew on 2006-09-16
Hi jonwatson,

Try copying over the the contents of the directory: 

~/.config/menus/

Luke

---

### Post by crossedout on 2006-09-16
Hi jonwatson,
I don't normally like to post links, but in this particular case they are rather lengthy but hopefully one of them can address and solve your problem.

[http://www.ubuntuforums.org/archive/index.php/t-184984.html+xfce4+menu+editor+open+menu&hl=en&gl=uk&ct=clnk&cd=3]("http://www.ubuntuforums.org/archive/index.php/t-184984.html+xfce4+menu+editor+open+menu&hl=en&gl=uk&ct=clnk&cd=3")

[http://www.ubuntuforums.org/showthread.php?t=225390&highlight=application+menu+empty](http://www.ubuntuforums.org/showthread.php?t=225390&highlight=application+menu+empty)

-Xout

---

### Post by jonwatson on 2006-09-16
Thanks for the ideas crossedout and lukew. So far, neither of those suggestions have worked for me.

I've found the default menus in /usr/share/applications, but copying them over to my ~/.config/menus doesn't work. I'm not sure where to copy them too...

---

### Post by IMELucky on 2006-10-10
I've also had the exact same problem after installing software with synaptic...:-(

---

### Post by GoreNuru on 2008-01-14
Try to delete your applications.menu and replace it with some of applications.menu.undo-* files. I think, this will word, if you have this files ) For me it's worked

---

### Post by hangar_18 on 2008-07-13
"~/.config/menus/applications.menu" file must include this:
> 
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
</Menu>

mine was empty after some problem during editing applications menu..this solved the problem :wink:

---

