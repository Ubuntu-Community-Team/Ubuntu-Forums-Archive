---
title: "Making a &quot;dock&quot; like this in xfce:"
date: 2007-11-18
forum: Desktop Environments
---

### Post by new2*buntu on 2007-11-18
In two distros, SAM and dreamlinux, I have seen that the xfce application dock zooms in during mouse-over. How could I do this in Xubuntu?
Here is an example of it in SAM: [Here]("http://www.seopher.com/images/samlinux/desktop.jpg")

---

### Post by johndavid400 on 2007-11-18
I'm not sure exactly what programs are compatible with Xubuntu, but in Kubuntu there is one theme that I use (that is easily modified for you chosen apps), that is exactly what you described. But it uses SuperKaramba. Maybe you can run it on Xfce, I don't know. 

Here is a link to the one that I revised for my programs, with pics:

[http://www.kde-look.org/content/show.php/mac+bar-+REVISED+?content=66626](http://www.kde-look.org/content/show.php/mac+bar-+REVISED+?content=66626)


Also, you might be able to run it using Gdesklets?.... I will install Xubuntu-desktop and try it and let you know.

---

### Post by new2*buntu on 2007-11-18
Thanks for the reply. I'll wait until you try it out.

---

### Post by johndavid400 on 2007-11-19
ok, I installed Xfce and ran superkaramba with the theme "macbar" from the link I posted..... it works, but it isn't pretty like it is in KDE. The background of the theme is black instead of transparent like it should be. So you have a functional mac-like launcher that raises on mouse-over, but it creates a black box around the theme. You should try it and see for yourself. 

sudo aptitude install superkaramba
download and extract mac bar from kde-look.org
open superkaramba, select open local theme, navigate to your mac bar folder.

if you dont like it:
sudo aptitude remove superkaramba

If you are completely adverse to using KDE, then I don't know if there is a solution. I couldn't get it to work with Gdesklets (though I know nothing about it).

Maybe someone will come out with a superkaramba equivalent for Xfce. Hope this helps.

---

### Post by vasiliymeshko on 2007-11-19
If I'm not mistaken, the program in SAM Linux is called 'Wbar'

---

### Post by new2*buntu on 2007-11-19
Thanks I will try it now.

---

