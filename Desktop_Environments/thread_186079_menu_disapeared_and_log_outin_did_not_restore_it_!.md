---
title: "menu disapeared and log out/in did not restore it !"
date: 2006-06-01
forum: Desktop Environments
---

### Post by IdoMcFly on 2006-06-01
EDIT : 
```

cp /etc/xfd/xfce4/desktop/menul.xml.<your locale> ~/.config/xfce4/desktop

```

Old problem was :

[I]I have a problem : my menu was eaten by the menu editor :(

I've followed the indication in the release note : rm the ~/.config/xfce4/desktop/menu.xml

log out and log in

it worked once, but since the second crash, it did not restore the menu, the application button is also empty :?

please help[/I]

---

### Post by oyvindaa on 2006-06-01
Have you tried adding a new menu?

Rightclick --> Add New Item --> Xfce Menu

Not sure whether it'll work in your case, but give it a go.

---

### Post by IdoMcFly on 2006-06-01
thenk you for the answer I've manage to reslve it by the code above

---

### Post by oyvindaa on 2006-06-01
Alright, all is good then! :)

---

### Post by Peepsalot on 2006-06-02
My menu is gone now too.  The button is there, but clicking it does nothing.  I installed Ubuntu Dapper 6.06, and then installed xubunu-desktop later.  The menu worked at one time.

Problem is I don't have any of these directories mentioned above.
There is no /etc/xfd directory on my computer, nor is there ~/.config.

---

### Post by psychicdragon on 2006-06-02
[QUOTE=Peepsalot]My menu is gone now too.  The button is there, but clicking it does nothing.  I installed Ubuntu Dapper 6.06, and then installed xubunu-desktop later.  The menu worked at one time.

Problem is I don't have any of these directories mentioned above.
There is no /etc/xfd directory on my computer, nor is there ~/.config.[/QUOTE]
There's some typos in that command in the top post, do this instead:
```
cp /etc/**xdg**/xfce4/desktop/menu.xml.<your locale> ~/.config/xfce4/desktop/menu.xml
```Ignore the .<your locale> part if you're using US english.

You can also copy the file using the filemanager if you're more comfortable with that.

---

### Post by Peepsalot on 2006-06-03
OK thank you, it is working now.  I was also a little confused because ls does not show files that begin with "." apparently.  I just realized this.  so my .config directory really does exist :D

---

### Post by puelly on 2006-06-05
I accidentally removed the file /etc/xdg/xfce4/desktop/menu.xml.  I have restored the menu.xml.uk but there are some non english characters.  Can someone please send me a copy of their menu.xml or tell me how to extract that file from the downloaded debs.

My email address is:
maclan at yahoo dot com

---

