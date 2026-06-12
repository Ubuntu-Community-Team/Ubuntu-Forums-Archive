---
title: "Using Nautilus as file manager"
date: 2013-06-03
forum: Desktop Environments
---

### Post by zanox on 2013-06-03
I succeeded in it, but I can't manage the files from the desktop, it gives me 
[CENTER]
[IMG]https://dl.dropboxusercontent.com/u/14269970/errore.jpg[/IMG]
[/CENTER]

The first sentence in Italian means "I can't open the folder"
I'm using Xubuntu 12.04

Thank you in advance

---

### Post by sid0972 on 2013-06-04
use sudo nautilus, your privileges are not elevated

[http://askubuntu.com/questions/98489/how-can-i-elevate-nautilus-privileges-to-move-or-copy-a-folder-as-root](http://askubuntu.com/questions/98489/how-can-i-elevate-nautilus-privileges-to-move-or-copy-a-folder-as-root)

---

### Post by sudodus on 2013-06-04
I think Thunar is still managing (or supposed to manage) the desktop according to the picture. Maybe you want Nautilus to manage your desktop too. Yes or no?

---

### Post by ajgreeny on 2013-06-04
Just out of interest, what happens if you start nautilus with command ```
nautilus --no-desktop
```so that it is not trying to manage your desktop?  I do not see why it would make a difference, but it must be worth trying.

---

### Post by thesoundman20 on 2013-06-04
are you wanting to use nautilus as just a file manager to view/edit your files and not handle your desktop? or are you wanting it to manage both your desktop and your use it to view/edit your files? because if the former is true you can create a launcher to open nautilus and do it that way. you can even setup a keyboard shortcut to open nautilus that way your only a keystroke away from your file manager.

---

### Post by zanox on 2013-06-04
> **sudodus said:**
> I think Thunar is still managing (or supposed to manage) the desktop according to the picture. Maybe you want Nautilus to manage your desktop too. Yes or no?

Exactly :)

both, Thunar out, Nautilus in ;)

---

### Post by thesoundman20 on 2013-06-04
i found this post on helpubunutuDOTcom to be helpful [https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager) as well as this one [http://askubuntu.com/questions/74534/set-nautilus-as-default-file-manager-in-xubuntu](http://askubuntu.com/questions/74534/set-nautilus-as-default-file-manager-in-xubuntu)

---

### Post by thesoundman20 on 2013-06-04
actually this post is perfect. i think if you remove the "--no-desktop" part it should work beautifully! good luck! [http://ubuntuforums.org/showthread.php?t=720449&p=4490813#post4490813](http://ubuntuforums.org/showthread.php?t=720449&p=4490813#post4490813)

---

### Post by zanox on 2013-06-04
> **thesoundman20 said:**
> i found this post on helpubunutuDOTcom to be helpful [https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager) as well as this one [http://askubuntu.com/questions/74534/set-nautilus-as-default-file-manager-in-xubuntu](http://askubuntu.com/questions/74534/set-nautilus-as-default-file-manager-in-xubuntu)

I already did that things, they work but they don't set nautilus as desktop manager

> **thesoundman20 said:**
> actually this post is perfect. i think if you remove the "--no-desktop" part it should work beautifully! good luck! [http://ubuntuforums.org/showthread.php?t=720449&p=4490813#post4490813](http://ubuntuforums.org/showthread.php?t=720449&p=4490813#post4490813)

I removed the "--no-desktop" part
That works for folders! but if I try to open the trash bin or a non-folder file I get this:

[CENTER][IMG]https://dl.dropboxusercontent.com/u/14269970/Istantanea%20-%2004062013%20-%2020%3A56%3A47.png[/IMG]
[/CENTER]

---

### Post by zanox on 2013-06-05
Ok after a reboot it works perfectly! but I can't set the background, I saw there's a package for nautilus to manage the wallpaper, any other pack to install?

---

### Post by Buntu Bunny on 2013-06-05
Settings > Preferred Applications > Utilities

Is your preferred file manager set as Nautilus or Thunar? 

I have to admit the that whole Xubuntu/Nautilus/Thunar arrangement seems quirky. I have Nautilus set as my preferred file manager, but when I open my home folder on my desktop, it's still Thunar.

---

### Post by ajgreeny on 2013-06-05
I have removed the **/home**,  **/filesystem** and **/trash** icons using desktop settings (right click on desktop) and replaced them with my own launchers which could have been for nautilus, if I'd wanted, as the /home, /filesystem and /trash icons kept moving around almost every time I booted, which was very annoying.

I have not replaced thunar with nautilus as my preferred application, and those new icons are still for thunar, but I simply thought you might find this a good way to get your /home desktop icon to use nautilus instead of thunar.

---

### Post by zanox on 2013-06-05
nautilus.. see the page before, there's an interesting link how to fix it

and what about the wallpaper? I can't see it anymore on the background and I can't change it! :roll:

---

