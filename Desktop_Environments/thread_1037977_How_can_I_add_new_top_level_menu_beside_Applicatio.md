---
title: "How can I add new top level menu beside Applications/Places/System?"
date: 2009-01-12
forum: Desktop Environments
---

### Post by pmiklos on 2009-01-12
hi,

Does anybody know how to add a new top level menu beside Applications/Places/System in gnome?

I would like to add a new menu called Projects. I can add it as a submenu to Applications but I want it to place at the top level. I found no solution how to achieve it.

Thanks for your answers,
-peter

---

### Post by ajgreeny on 2009-01-12
Not tried this, but what happens if you right click on the present menu and use the Edit Menu option and then New Menu, instead of new item, which I have used several times.

---

### Post by pmiklos on 2009-01-12
> **ajgreeny said:**
> Not tried this, but what happens if you right click on the present menu and use the Edit Menu option and then New Menu, instead of new item, which I have used several times.

I have tried that. "New Menu" adds menu under the existing top level menus. If nothing is selected, nor Applications neither System, it automatically selects Applications and creates the menu under that.

---

### Post by binbash on 2009-01-12
as far as i know you can't add it

---

### Post by pmiklos on 2009-01-12
> **binbash said:**
> as far as i know you can't add it

you may right. Regarding to the GNOME 2.14 Desktop System Administration Guide it is the application.menu that is searched for when rendering the menu bar. I have tried to modify it by hand, without any success.

---

### Post by nemilar on 2009-01-12
This is actually a very interesting question.  If you find that there is no answer (it isn't possible), you should think about putting in a feature request (wishlist) at Launchpad. 

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by kunwon1 on 2009-02-25
Hi, I don't use ubuntu anymore but I am using gnome. I found the solution to this problem on my system, it might work on ubuntu. ymmv.

```
nano $HOME/.config/menus/applications.menu
```

```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
        <Name>Applications</Name>
        <MergeFile>/home/kunwon1/.config/menus/launch.menu</MergeFile>
        <MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
        <Menu>
```

See the first MergeFile tag? that's my custom menu. It's important that you don't use type="parent" for your include. That does not do what you want in new versions of gnome, so even if it works today it might break with a gnome upgrade.
edit: the file above is not shown in its entirety


Here is launch.menu:

```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
        <Name>Quicklaunch</Name>
                <Include>
                        <Filename>firefox.desktop</Filename>
                </Include>
                <Include>
                        <Filename>xchat.desktop</Filename>
                </Include>
</Menu>
```

that's the whole file. Mine is just to include launchers on the top level menu, and i'm not even sure there isn't an easier way to do this. But this works for me. You'd have to do it differently to include an actual menu, see [this link]("http://library.gnome.org/admin/system-admin-guide/stable/menustructure-13.html.en") for details on the makeup of the .menu file.
edit: to see your changes you may have to `killall gnome-panel`

Results:

[[IMG]http://img9.imageshack.us/img9/3734/screenshot1q.th.png[/IMG]](http://img9.imageshack.us/my.php?image=screenshot1q.png)

Hope this helps someone :D

---

### Post by luceerose on 2010-08-06
Sorry, this didn't work for me at all.
Even after killall, pkill & logout.
Using Debian Sid with Gnome 2.30.2
No sign of the new menu anywhere.

---

