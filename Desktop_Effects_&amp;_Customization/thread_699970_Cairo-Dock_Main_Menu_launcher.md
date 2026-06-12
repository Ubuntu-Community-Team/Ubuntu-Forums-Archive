---
title: "Cairo-Dock Main Menu launcher"
date: 2008-02-17
forum: Desktop Effects &amp; Customization
---

### Post by zephyrus17 on 2008-02-17
Is there a main menu launcher in Cairo-dock? Like the one in Kiba-dock? Is so, could you teach me how to get it set up?

Oh, how do you create your own sub dock? I'm trying to make an Open Office sub dock.

---

### Post by zephyrus17 on 2008-02-19
Bump.

---

### Post by chavanak on 2008-02-19
Drag the  icons onto cairo-dock and then right click on it. Click modify this launcher, go to extra parameters and select which sub-dock you want.

If you want to create a sub-dock for a dock, right click on the dock and select new sub-dock.

If you want to add gnome main menu, then right click on dock, select add launcher and then gnome-main-menu

---

### Post by zephyrus17 on 2008-02-19
Where do I find gnome-main-menu? I believe it has to end in .desktop, right?

---

### Post by bmwman on 2008-06-07
I'm interested as well :)

---

### Post by nochka85 on 2008-06-08
First of all -> Sorry for my english (I'm french ;-) )

It's now possible to launch the gnome main menu with cairo-dock ! 
To be able to do that, you just need to remove it from the gnome-panel ... then you create a new launcher and in the command line , you type : **<Alt>F1**  ;-)

Don't hesitate to go on the official forum (In french but also in English ;-) ) -> [http://www.cairo-dock.org/bg_forumlist.php]("http://www.cairo-dock.org/bg_forumlist.php")

---

### Post by bmwman on 2008-06-10
> **nochka85 said:**
> First of all -> Sorry for my english (I'm french ;-) )

It's now possible to launch the gnome main menu with cairo-dock ! 
To be able to do that, you just need to remove it from the gnome-panel ... then you create a new launcher and in the command line , you type : **<Alt>F1**  ;-)

Don't hesitate to go on the official forum (In french but also in English ;-) ) -> [http://www.cairo-dock.org/bg_forumlist.php]("http://www.cairo-dock.org/bg_forumlist.php")

I tried that, but nothing hapens when I I click on it.

---

### Post by bmwman on 2008-06-10
Actually I got it to work :) I didn't remove the main menu from the gnome panel at first. Great!

Thank you.

---

### Post by carrara47 on 2008-06-17
Hi all,
before all sorry for my English :)
This solution doesn't work for me, because when the gnome-panel isn't running, the shortcut doesn't work.

Then I have created a script (in python) that adds any entry of the menu as a desktop file in the cairo-dock configuration directory (~/.cairo-dock/current_theme/launchers).

This is the result
[[IMG]http://img379.imageshack.us/img379/483/screenshotwf1.th.png[/img]](http://img379.imageshack.us/my.php?image=screenshotwf1.png)

The script is in the attachment.
This is only a workaround, but work well.
The usage is simple:

cairo-menu add|remove  applications|system|all

I have tested the script only on my pc with gnome (Hardy).
To get information about the 'applications' menu I have used the python-xdg package, which should be work also in the other desktop environments.
Instead, for the 'system' menu, I have used python-gmenu, that requires gnome.

However, I think that some problems could happened because of different language and encodings.
I use the English language on my pc, but I have seen that any desktop file of cairo-dock starts with a '#!en' line. It's possible that this line should be changed accordingly to own language. It's enough to open the script and in the first line there are two variables that I have used to create the desktop files.
For the encodings surely I have to use the unicode module, but I don't know it very well :)

Sometimes, if two menu entries have the same name I have added a suffix to distinguish them. This for me is happened with Wine, because a container and one of its launcher had the same name (I don't know why, but two different dock was appeared!! )

If you have some problems with the script let me know.
Bye

Edit: Now the icons are ordered

---

### Post by sinnerFA on 2008-06-24
carrara47,

Let me be the first to say that your script works excellent!
I had no issues running or problems once I restarted.

The dock is now complete.
I am running:

Ubuntu Kernel: Linux <workstation_name> 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

Python: version 2.5.2 (r252:60911, May  7 2008, 15:19:09)

***Also a hint for anyone using this (kinda obvious, but): any gui additions to your box would require you to re-run this script (or add the launcher manual, but why manual?)

Thanks again carrara47!

---

### Post by carrara47 on 2008-06-24
Hi,
I'm happy that all works fine :)

> 
***Also a hint for anyone using this (kinda obvious, but): any gui additions to your box would require you to re-run this script (or add the launcher manual, but why manual?)

Yes, It's true. This script is only a workaround (see the ~/.cairo-dock/current_theme/launchers directory)  and the best solution is if someone creates a plugin for this. (It must be written in C)

For the requirement, I think there's no problem with older kernel.
Except possible encoding problems, my only doubt is what happens in a DE different from gnome. I think that all should work fine.

If someone needs some improvements for the script, for example to control the way the launchers are displayed, let me know.

Bye

---

### Post by lucasbruke on 2008-06-29
Hello, could you explain me how to use/install that script?
Thanks!

---

### Post by carrara47 on 2008-06-29
Yes, of course.

Download the archive and extract it.
It contains only the script, named cairo-menu
Then open a terminal, go in the directory in which you have open the archive and run
```

chmod +x cairo-menu

```
to make it excutable.
The script allows two actions, add and remove, on three possible targets, i.e. applications, system and all.
For example running
```

./cairo-menu add applications # add the applications menu
./cairo-menu add all # add both system and applications menu
./cairo-menu remove system # remove only the system menu

```
and so on.
Use the -h option to quickly remember those options.

Bye

---

### Post by lucasbruke on 2008-06-29
well, the system menu seems to be working fine. But I'm having trouble with the applications menu. When I enter ./cairo-menu add applications in the terminal I get this:

  File "./cairo-menu", line 293, in <module>
    main()
  File "./cairo-menu", line 290, in main
    CreateMenu(xdg.Menu.parse())
  File "./cairo-menu", line 246, in CreateMenu
    CreateMenu(entry, Name, prefix, order)
  File "./cairo-menu", line 241, in CreateMenu
    CreateContainer('%s.desktop' % new_container,Name,Icon,container_name,order)
  File "./cairo-menu", line 216, in CreateContainer
    CreateEntry(new_path,data)	
  File "./cairo-menu", line 174, in CreateEntry
    N.write(data)
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe1' in position 51: ordinal not in range(128)

After that something seems to be installed because when trying to open Cairo-Dock again it opens the the settings window in maintenance mode and I can't do anything there. So if I remove the applications menu only, the rest still works.
Do you know if I am missing something?
Thanks again!

---

### Post by carrara47 on 2008-06-29
No, the script has a problem.
> 
However, I think that some problems could happened because of different language and encodings.

My conjecture was right! :)

Probably one of your .desktop file contains some special characters.
The new script should work. It isn't a real solution, simply it don't create the entry for the bad items.
Anyway it print those items in the terminal, so you can check inside the .desktop file in order to know what happen.
If you want you can send me the bad .desktop file so I can see if I'm able to found a better workaround. Run ./cairo-menu -h to see my email.

Bye

---

