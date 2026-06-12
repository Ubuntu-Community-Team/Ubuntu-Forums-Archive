---
title: "Can't add new icon theme"
date: 2010-11-19
forum: Desktop Environments
---

### Post by Chris_cur on 2010-11-19
Finally coming back to Ubuntu this time with XFCE. Here is my hair pulling issue: I can not add downloaded icon theme.  I have dragged and dropped the tar.bz2 file into the window and that does not work. 
So, I tried to extract the contents into /usr/share/icons/ and keep getting told> Extraction not performed  You don't have the right permissions to extract archives in the folder "file:///usr/share/icons" so... wtf? I have administrative rights.

I have also tried extracting the files to my desktop and then copying the file to the /icons/ folder and that also doesn't work.

What am I doing wrong here? I have searched all over the place and I have not found a workable answer.

---

### Post by hhh on 2010-11-19
Download the icon theme. Make sure you have a hidden foder under /home/USER_NAME/ called .icons (with the period in front). Move the icon theme folder to the .icons folder. The theme can now be used locally.

To use them system wide, in the Run dialog (Alt+F2) open Thunar with administrative privelages (gksu thunar). Move the icon folder to /usr/share/icons/ and you're done.

HTH

BTW, which icon theme is it?

---

### Post by Chris_cur on 2010-11-19
Gah! D'OH! 

Thanks. I don't know how I overlooked that!

They are Web0 here is the link [http://gnome-look.org/content/show.php/Web0?content=133506](http://gnome-look.org/content/show.php/Web0?content=133506)

---

### Post by hhh on 2010-11-19
I'm glad it's working. Nice icon set, thanks for the link!

-edit- the OP marked this solved so I assume he figured it out, but for anyone else when you untar this theme there is another tar in the new folder that you also have to extract. Then just move the newly extracted folder to your preferred location.

---

