---
title: "xubuntu6.06 menu gone"
date: 2006-06-03
forum: Desktop Environments
---

### Post by qinhengsi on 2006-06-03
hi friends,
I installed xubuntu6.06 yesterday. It is fine except one thing.
I ran the menu-editor. It came out nothing. Then I found my menu was gone.
I also found that ~/.config/xfce4/desktop/menu.xml was overwritten.

I tried google, but I cannot find much helpful. 
anyone can help me rebuild my menu?

OR

anyone can post his/her menu.xml ?

thinks a lot

---

### Post by earthvisitor on 2006-06-03
look at
/etc/xdg/xfce4/menu.xml
It's the exactly same menu.
Alternatively, just delete the empty file menu.xml you mentioned. It should come back.

---

### Post by earthvisitor on 2006-06-03
Sorry, it should be
/etc/xdg/xfce4/desktop/menu.xml

---

### Post by psychicdragon on 2006-06-03
Just delete the menu file (~/.config/xfce4/desktop/menu.xml) and the menu will revert to the default.

If you want to customize the menu, you'll have to use a text editor because the menu-editor seems to be bugged. I'm going to try building the menu-editor from the Xfce svn when I have some time. I was running Fxce from svn just a couple of days ago and had no problems with the menu-editor.

---

### Post by Nordoelum on 2006-06-04
LOL. I deleted the one located: etc/xdg/xfce4/desktop/menu.xml
not: /.config/xfce4/desktop/menu.xml

Damn, could someone upload the latest build of the menu.xml?

---

### Post by Nordoelum on 2006-06-04
I really need this now :P Since now all my menus have gone. Can I get it from the official package?

---

### Post by dotnick on 2006-06-04
You could always try 

$update-menus

at the command line.... i had the same problem

---

### Post by kaamos on 2006-06-04
Happened to me as well, fixed with ```
sudo apt-get install xfdesktop4 --reinstall
```

---

### Post by Nordoelum on 2006-06-04
Didn't do the trick :( Since I removed the file from the /etc/xdg/xfcg4/desktop folder.

Do I need to reboot?

---

