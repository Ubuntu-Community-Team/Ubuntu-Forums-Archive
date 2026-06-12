---
title: "Just compiled and installed xfce, is there a way..."
date: 2004-10-17
forum: General Help
---

### Post by Flawed on 2004-10-17
to select it from the login screen, like Gnome and KDE? What config files do I have to edit? I'm considering installing ubuntu on my old laptop, but as it has only 64 megs of RAM I thought I'd go for a lighter window manager, so I'd like to try out xfce on my desktop. Thanks in advance.

---

### Post by chz on 2004-10-19
if u updated through synaptic...XFCE should already be available on ur sessions when u login. at least thats what happened when i did it. if you compiled it yourself or through apt-get...i dont think it will update ur login sessions screen.

---

### Post by triad169 on 2004-10-19
here you go this should work.

```

sudo mkdir /etc/X11/sessions
cd /etc/X11/sessions
sudo gedit xfce.desktop
```

geditor opens now add this:

> 
[Desktop Entry]
Encoding=UTF-8
Name=XFCE4
Comment=This logs you into XFCE4.
Exec=/usr/bin/startxfce
TryExec=/usr/bin/startxfce
Icon=
Type=Application

Save the file.  leave *icon=* blank.  had some issues with this on another distro.  I think that should do it.  Havent tried on Ubuntu but did work for me before on another distro.

Triad

---

### Post by GOwin on 2004-10-20
I can also use XFCE on my ubuntu system. I like it over gnome as i find it more responsive on the destop.

Now, how do i get the gnome applications menu into XFCE?

---

### Post by Flawed on 2004-10-21
Thanks, guys. What repositories do I have to add to synaptic to be able to grab xfce? Universe doesn't seem to have it -- or is it down right now?

---

### Post by im_ka on 2004-10-21
[quote=GOwin]I can also use XFCE on my ubuntu system. I like it over gnome as i find it more responsive on the destop.

Now, how do i get the gnome applications menu into XFCE?[/quote]

not  sure if it will generate the exact gnome menu, but i'd try this:

[http://menumaker.sourceforge.net/](http://menumaker.sourceforge.net/)

(found by your friend [http://www.google.com/linux](http://www.google.com/linux)  :wink:)

---

### Post by im_ka on 2004-10-21
[quote=Flawed]Thanks, guys. What repositories do I have to add to synaptic to be able to grab xfce? Universe doesn't seem to have it -- or is it down right now?[/quote]

[http://www.os-cillation.com/article.php?sid=37](http://www.os-cillation.com/article.php?sid=37)

---

### Post by GOwin on 2004-10-21
I can't seem to add those URI into synaptic repositories.

I'm doing it as follows:
Binary (deb)
URI: [http://www.os-cillation.de/debian](http://www.os-cillation.de/debian)
Distribution: source &lt;-- is this correct
Section: &lt;-- what do i place in here?

---

### Post by shufla on 2004-10-22
Hello,

[quote=Flawed]Thanks, guys. What repositories do I have to add to synaptic to be able to grab xfce? Universe doesn't seem to have it -- or is it down right now?[/quote]

Huh? It's very strange. Yesterday I've installed Ubuntu, added universe to repositories and synapticed xfce4. Well, did you push REFRESH button in synaptic after activating universe repository?

[another thing - menu]

Try install menu package from universe. sudo apt-get install menu, then sudo update-menus.

Best regards,
Lukasz

---

### Post by GOwin on 2004-10-24
[QUOTE=GOwin]I can't seem to add those URI into synaptic repositories.

I'm doing it as follows:
Binary (deb)
URI: [http://www.os-cillation.de/debian](http://www.os-cillation.de/debian)
Distribution: source -- is this correct
Section: ;-- what do i place in here?[/QUOTE]

*bump*

---

### Post by easymacaddict on 2004-10-25
[QUOTE=GOwin]I can also use XFCE on my ubuntu system. I like it over gnome as i find it more responsive on the destop.

Now, how do i get the gnome applications menu into XFCE?[/QUOTE]

I just installed the new xfce 4.2beta1 on my slackware setup by running the [handy installer](ftp://os-cillation.com/installers/xfce4-4.2beta1-installer.bin), and it automatically imported both my gnome and kde menus (into one giant menu, but that's a different story).  there is also a [debian (sarge) package](http://www.os-cillation.com/article.php?sid=37)  available.

---

### Post by GOwin on 2004-10-25
[QUOTE=easymacaddict]I just installed the new xfce 4.2beta1 on my slackware setup by running the [handy installer](ftp://os-cillation.com/installers/xfce4-4.2beta1-installer.bin), and it automatically imported both my gnome and kde menus (into one giant menu, but that's a different story).  there is also a [debian (sarge) package](http://www.os-cillation.com/article.php?sid=37)  available.[/QUOTE]


I've tried the instructions from that os-cillation.com page. I can't get to access the repository indicated there. I'm using synaptics, but I think I'm doing it all wrong

---

