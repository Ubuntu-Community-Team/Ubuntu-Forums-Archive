---
title: "XFCE 4.8 - No Applications Found"
date: 2011-05-15
forum: Desktop Environments
---

### Post by Albertint on 2011-05-15
I've run into this bug that I don't know how it happened, quite. I ran my installed 4.8 on Ubuntu 11.04 a few days ago, and it the Applications Menu worked fine. Then, I wanted to add an application to it (The Ubuntu Software Center) so I opened up its settings and edited it with what I think to be alacarte. Then when I click the menu to check it, a simple tab appears over it and says "no applications found". This was rather confusing, so I looked in the ~/.config/menus/ folder and opened up the xfce-applications.menu file. This is what it says:

```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
    <Name>Xfce</Name>
    <MergeFile type="parent">/etc/xdg/menus/xfce-applications.menu</MergeFile>
</Menu>
```This leads me to believe that the standard menu editor may not work correctly, but now I need to know how to get it working again. I've tried simply replacing the menu, but that doesn't work. 

Thanks,
 Albertint

---

### Post by Albertint on 2011-05-15
Wow, nevermind on that.

Turns out when I edit the file, it is saved in the folder I described above, which is the one accessed. But there's an exact same file saved under ~/etc/xdg/menus/xfce-applications.menu 

Strange, but it works just to copy that over to the other folder I defined.

Good thing I got that. Now how do I change the thread badge as SOLVED. :confused:

---

### Post by mvario on 2011-05-17
I just had the same thing happen... what did you copy where?

Thanks

[edit]

got it, I chose custom instead of default and pointed it at ~/etc/xdg/menus/xfce-applications.menu and I'm good.

---

### Post by fooey on 2011-07-26
in the same EXACT situation as O.P.er

How'd you fix again?

---

### Post by lucia_engel on 2011-08-14
> **fooey said:**
> in the same EXACT situation as O.P.er

How'd you fix again?

I just had the same problem and this is what I did. Right click on the Applications Menu and go to Properties. Select "Use custom menu file" and browse to ~/etc/xdg/menus/xfce-applications.menu

Edit: Disregard the above, "Application Finder" and Launcher "add" would still not work. Keep the default menu and run the following commands.

```

cp ~/.config/menus/xfce-applications.menu ~/.config/menus/xfce-applications.menu_backup
cp /etc/xdg/menus/xfce-applications.menu ~/.config/menus/

```

---

### Post by XubuRoxMySox on 2011-08-14
> **Albertint said:**
> Now how do I change the thread badge as SOLVED. :confused:

Thanks for this thread, it's actually quite helpful!

To mark this as SOLVED, go to your first pot in the thread and click "Edit." Then choose "Advanced" options to open up the Subject line, then just add "[SOLVED]" to the subject.

-Robin

---

### Post by Elfy on 2011-08-14
Actually you should be able to do so from the Thread Tools at the top. As it is I did it.

---

### Post by art_peru on 2011-08-29
Thanks a lot, same problem here :)

---

### Post by mikodo on 2011-08-31
> **lucia_engel said:**
> 

```

cp ~/.config/menus/xfce-applications.menu ~/.config/menus/xfce-applications.menu_backup
cp /etc/xdg/menus/xfce-applications.menu ~/.config/menus/

```
Same problem. This fixed it.

Thanks.

---

### Post by ericklan on 2011-09-01
> **lucia_engel said:**
> I just had the same problem and this is what I did. Right click on the Applications Menu and go to Properties. Select "Use custom menu file" and browse to ~/etc/xdg/menus/xfce-applications.menu

Edit: Disregard the above, "Application Finder" and Launcher "add" would still not work. Keep the default menu and run the following commands.

```

cp ~/.config/menus/xfce-applications.menu ~/.config/menus/xfce-applications.menu_backup
cp /etc/xdg/menus/xfce-applications.menu ~/.config/menus/

```


restart session and ok =)

---

