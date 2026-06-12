---
title: "gtk-2.0 customization help?"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by Impulse666 on 2007-07-07
recently switched to ubuntu and i love it, just a couple things i'm not too sure about...

when you hover your mouse over "system" you get
> Change desktop appearance and behavior, get help, or log out
by default this is black text on yellow background. i have customized a theme using the theme manager, and it has white text. is there any way to edit the gtk file to change the background color on that popup object? 

and then how would i go about that? i can only open the file as read only because of permissions, and because i am not the owner i cannot change the permissions. do i have to log in as a different user to be able to edit the system files?

---

### Post by hyperair on 2007-07-08
Open your run dialog (Alt+F2) and type "gksu gedit" without quotes. Then type in your password when prompted. It'll open a text editor. From there open whatever file you want to open. You can even drag the text files in. What that command does is it opens the gnome-text-editor as the root user which is pretty much the super user in all Linux distributions. The super user doesn't have any limitations from access to any part of the system, so use it with care, as you could also destroy your entire system accidentally if you delete the wrong files as a super user.

---

