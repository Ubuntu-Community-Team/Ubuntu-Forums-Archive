---
title: "Where does Nautilus keep its configurations?"
date: 2008-08-21
forum: Desktop Environments
---

### Post by syn4k on 2008-08-21
Where does Nautilus keep its configurations? I'm talking about the configuration file which contains icon sizes and whether or not folders open in list view or not.

I did locate nautilus but I got back like 600 files...

---

### Post by perlluver on 2008-08-21
> **griffin.ray@gmail.com said:**
> Where does Nautilus keep its configurations? I'm talking about the configuration file which contains icon sizes and whether or not folders open in list view or not.

I did locate nautilus but I got back like 600 files...

Press alt+f2, type in gconf-editor, and go to the nautilus tab.

---

### Post by syn4k on 2008-08-22
Great response :) Now, what I really need though is to be able to run this command: gconf-editor /apps/nautilus/preferences/default_folder_viewer "list_view" and it actually set the value to list_view...

So far, all that running this command does is bring up the window so I can manually type it in. I would like to set this automatically from my bash settings script that I'm building.

Thanks!:)

---

### Post by syn4k on 2008-08-22
I also tried: ```
perl -pi -e 's/icon_view/list_view/g' ~/.gconf/apps/nautilus/preferences/%gconf.xml
```
However, that does nothing even though it seems it would since it effectively replaced the setting.

---

### Post by syn4k on 2008-08-27
Well...keep them coming, please

---

### Post by VMC on 2008-08-27
Open Nautilus, go to "Edit > Preferences > Views > Default View", then to the right of  "View new folders using:" click "List View"

---

### Post by mcduck on 2008-08-28
> **griffin.ray@gmail.com said:**
> Great response :) Now, what I really need though is to be able to run this command: gconf-editor /apps/nautilus/preferences/default_folder_viewer "list_view" and it actually set the value to list_view...

So far, all that running this command does is bring up the window so I can manually type it in. I would like to set this automatically from my bash settings script that I'm building.

Thanks!:)

The tool used to set/configure gconf keys from CLI is "gconftool-2", "gconf-editor" will simply launch the graphical editor.

```
gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_view "list_view"
```

[http://library.gnome.org/admin/system-admin-guide/2.22/gconf-6.html.en]("http://library.gnome.org/admin/system-admin-guide/2.22/gconf-6.html.en")
[http://linux.die.net/man/1/gconftool-2]("http://linux.die.net/man/1/gconftool-2")

---

### Post by VMC on 2008-08-28
This is the first time I have ever come across this tool. Very powerful. I did some research and read some docs online. I'm sure this has been discussed on some programming forums.
Reading the man page I found this:
 gconftool-2 --get /desktop/gnome/background/picture_filename
I needed that info just yesterday! I had to dig around to find it through find command.

I will have to remember this tool for future reference. Thanks for the introduction.

---

