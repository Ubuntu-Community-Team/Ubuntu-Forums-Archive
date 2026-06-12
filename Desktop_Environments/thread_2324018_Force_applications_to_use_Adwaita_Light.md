---
title: "Force applications to use Adwaita Light"
date: 2016-05-10
forum: Desktop Environments
---

### Post by Imerion on 2016-05-10
I am looking for a way to force all apps to use the light version of the Adwaita theme. As it is now, apps like Totem, Eye of Gnome and Photos use a black theme which sticks out in a very ugly way compared to my other apps.

I managed to use "GTK_THEME=Adwaita:Light totem" to do this when launching apps, so I know it's possible. But adding this to the .desktop files doesn't seem to work. I would like to have a permanent solution that makes this work even if I just open an image from my file manager or such. Is there any way to do this? Perhaps I could automatically add "GTK_THEME=Adwaita:Light" to all app launches in some way?

---

### Post by vasa1 on 2016-05-10
> **Imerion said:**
> ...

I managed to use "GTK_THEME=Adwaita:Light totem" to do this when launching apps, so I know it's possible. But **adding this to the .desktop files** doesn't seem to work. ...
Can you try```
Exec=bash -c 'GTK_THEME=Adwaita:Light totem'
```instead? 

You may try adding "%U" or "%u" to the end of the code if you want to open files by double-clicking on them in your file manager.

I suggest you copy over the .desktop files you want to modify to *~/.local/share/applications* and modify them there. 

I've also tried```
Exec=env GTK_THEME=Adwaita:dark gnumeric %U
```as suggested in the link I've given below. I think the latter is preferable.

Edit: also look at [http://worldofgnome.org/running-gtk-applications-different-themes-per-app/](http://worldofgnome.org/running-gtk-applications-different-themes-per-app/) posted on May 13, 2014 which has this:> While GTK_THEME flag should work for all GNOME applications, it actually doesn&#8217;t (not a clue why). So you should experimental a bit what works, what doesn&#8217;t.

Furthermore, this flag is been here mainly for debugging purposes and not for regular use.



---

### Post by Imerion on 2016-05-11
Thanks for your answer! Those lines both worked fine, though only for Eye of Gnome and Gnome Photos. Totem still gives me the dark version, even though it does give me the light version if I double-click the .desktop file. (But not from my main menu or when opening movie files.

Very odd. I did modify both totem.desktop and org.gnome.Totem.desktop. The problem seem to be with the latter, which launches the dark version whatever I do.

---

### Post by vasa1 on 2016-05-11
> **Imerion said:**
> Thanks for your answer! Those lines both worked fine, though only for Eye of Gnome and Gnome Photos. Totem still gives me the dark version, even though it does give me the light version if I double-click the .desktop file. (But not from my main menu or when opening movie files.

Very odd. I did modify both totem.desktop and org.gnome.Totem.desktop. The problem seem to be with the latter, which launches the dark version whatever I do.
There maybe at least three Totem .desktop files:
```
09:14 PM .../app-install/desktop $ ls | grep -i totem
totem:org.gnome.Totem.desktop
totem-plugin-arte.desktop
totem:totem.desktop
```
And each may have more than one **Exec=** line. Did you fix them all?

---

### Post by Imerion on 2016-05-14
That worked! I had missed those extra execs. Should have done a search. Anyway, thanks a lot for all help! It looks great now!

---

### Post by vasa1 on 2016-05-14
Glad I could help!

---

