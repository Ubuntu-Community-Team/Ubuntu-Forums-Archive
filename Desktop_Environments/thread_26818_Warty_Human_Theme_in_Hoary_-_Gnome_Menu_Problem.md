---
title: "Warty Human Theme in Hoary - Gnome Menu Problem"
date: 2005-04-14
forum: Desktop Environments
---

### Post by Schrollini on 2005-04-14
Hello all,

I recently upgraded to Hoary.  Overall, the process was perhaps the smoothest software upgrade I've every gone through.[1]  Congrats, developers.

However, I didn't like the new Human theme as much as the old one from Warty.  Luckily, [this post](http://www.ubuntuforums.org/showpost.php?p=121813&postcount=43) showed me where to find the old themes (thanks, bvc).  I downloaded to oldest tar file, extracted the gtkrc and metacity-theme-1.xml files, put them in the right places, and everything worked.

Well, almost.  The only flaw I've found is that when I click on the 'Places' or 'System' menus, the text stays black:
[IMG]http://home.uchicago.edu/~rschroll/menu-places.png[/IMG]
instead of turning white:
[IMG]http://home.uchicago.edu/~rschroll/menu-apps.png[/IMG]
(I know this is a rather minor thing, but I'm silly like this.)  I've looked over the gtkrc file, but I don't see anything specific to the gnome menu to change.  I note that the old theme used to the 'Industrial' engine, while the new theme uses the 'Clearlooks' engine, but I have no idea what that means, let alone if it's relevant.

I did find that the Gnome Journal's [preview of Gnome 2.10](http://www.gnomejournal.org/article/17/gnome-210-desktop-and-development-platform) displays the same problem I'm having, but that hasn't gotten me any closer to a solution.

Thanks in advance! (And apologies for wasting your time on something so little!)

[1]: Nitpick: Next time, could you note in the Release Notes if we're switching to a different sound daemon?

---

### Post by ubuntu_demon on 2005-04-14
I don't have this problem. What happens when you create a new user ? If he hasn't the problem you can try removing some hidden files related to gnome from your homedir (don't remove hidden files of applications you use)

---

### Post by Spark* on 2005-04-14
Open /usr/share/themes/Human/gtk-2.0/gtkrc, scroll down where the widget_class statements are and add this line: ```
widget_class "*MenuItem.*" style "clearlooks-menu-item"
```
You can then remove all the other widget_class lines with "MenuItem" in them, but it shouldn't be necessary.

**Edit:** Oops, of course not "clearlooks-menu-item" but whatever the old Industrial theme used for menus.

---

### Post by Schrollini on 2005-04-14
[QUOTE=Spark*]Open /usr/share/themes/Human/gtk-2.0/gtkrc, scroll down where the widget_class statements are and add this line: ```
widget_class "*MenuItem.*" style "clearlooks-menu-item"
```
[/QUOTE]

Thanks, Spark*.  That worked perfectly.

In case anyone else wants to know, the line I used was:
```
widget_class "*MenuItem.*" style "human-menu"
```

demon666_nl: I'm afraid I tried Spark*'s method first, so I didn't get to test yours.  Thanks anyway.

---

### Post by ubuntu_demon on 2005-04-14
[QUOTE=Schrollini]Thanks, Spark*.  That worked perfectly.

In case anyone else wants to know, the line I used was:
```
widget_class "*MenuItem.*" style "human-menu"
```

demon666_nl: I'm afraid I tried Spark*'s method first, so I didn't get to test yours.  Thanks anyway.[/QUOTE]
 np
I'm glad it worked :)

---

