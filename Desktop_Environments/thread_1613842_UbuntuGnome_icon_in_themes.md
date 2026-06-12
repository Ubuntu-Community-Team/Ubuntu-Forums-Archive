---
title: "Ubuntu/Gnome icon in themes"
date: 2010-11-04
forum: Desktop Environments
---

### Post by Chazz44able on 2010-11-04
I'm sure there's a really easy way to do this in the Configuration Wizard, but what I want to do is change the icon that is usually the Ubuntu icon that is now the Gnome icon (after having installed the "Slick Red" theme back to being the Ubuntu symbol. On the very top Left of the screenshot: [http://gnome-look.org/content/preview.php?preview=1&id=113991&file1=113991-1.png&file2=113991-2.png&file3=&name=Slick+Red](http://gnome-look.org/content/preview.php?preview=1&id=113991&file1=113991-1.png&file2=113991-2.png&file3=&name=Slick+Red)[IMG]http://file:///home/charles/Desktop/DesktopSC.png[/IMG][IMG]http://file:///home/charles/Desktop/DesktopSC.png[/IMG]

---

### Post by Chazz44able on 2010-12-22
Anybody?

---

### Post by Lone_Joker on 2010-12-22
The icon by the part where it says Applications?

Anyway. I think filename for the icon is gnome-main-menu.png, it might be some other type of file though (not sure). That file should be in
[LIST]
[*]/opt/gnome/share/pixmaps (or icons)
[*]/usr/share/pixmaps (or icons)
[*]~/.icons/
[/LIST]

I found something about this here too: [http://ubuntuforums.org/showthread.php?t=498890](http://ubuntuforums.org/showthread.php?t=498890)

EDIT: I think the name for the icon depends on what icon theme you're using. I'd just open up my file manager and search for it.

---

### Post by 101011010010 on 2010-12-23
Hello.
You have to edit the icon "start-here.png" in the Black-Red icon set.
(Black-Red/black-red/scalable/places). This should be in ~/.icons or /usr/share/icons.
I hope this helps.

---

### Post by Frogs Hair on 2010-12-23
The icon folder may also be in home/hidden folders/.icons . This is where I find my icon sets that I have downloaded . Press Ctrl + H when in your home folder to show hidden folders.

---

### Post by Chazz44able on 2010-12-23
Thank you all for replying, neither the black&red icon theme or the Last amazing grays (the set I'm now using) icon set are in my icons folder. So where can |I find them? Or is there another way to change it?

---

### Post by 101011010010 on 2010-12-23
Hello again.
If the icons are not in /usr/share/icons, then they should be in,
 /Home/"username"/.icons (not ~/.themes as I said earlier :oops:). 
Have you got Nautilus set to show hidden folders?
If not navigate to  your home folder in Nautilus & press Ctrl+h.
A.

---

### Post by Frogs Hair on 2010-12-23
The icon folder should in one of two places . File browser > File system > User > Share > icons or File browser > Home > Hidden folders > .icons .

---

### Post by hhh on 2010-12-23
You can also change that icon via gconf-editor, see steps 1 and 2 in this post (ignore the rest)...
[http://ubuntuforums.org/showpost.php?p=2841579&postcount=2](http://ubuntuforums.org/showpost.php?p=2841579&postcount=2)

---

### Post by Chazz44able on 2010-12-23
> **hhh said:**
> You can also change that icon via gconf-editor, see steps 1 and 2 in this post (ignore the rest)...
[http://ubuntuforums.org/showpost.php?p=2841579&postcount=2](http://ubuntuforums.org/showpost.php?p=2841579&postcount=2)

Yeh, that's fine but that only works for the Gnome menu - one icon only -  whereas I want to change it on the custom menu - were it shows the  Applications, Places and System menus on the panel.

---

