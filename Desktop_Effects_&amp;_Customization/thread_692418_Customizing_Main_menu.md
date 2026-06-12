---
title: "Customizing Main menu"
date: 2008-02-09
forum: Desktop Effects &amp; Customization
---

### Post by Spikius on 2008-02-09
Ok, so everyone knows te Applications / Places / System ...
I would like to rename them, is there anyway to do that couse i googled like 2 hours and didint find any answer to my Q.

So if there is anyone who knows...

---

### Post by adamc83 on 2008-02-10
Names as they appear in menus are stored in .desktop files, which are found in /usr/share/applications

You should see something like "Name=Application Name", which you could change, though do so at your own risk. I've never done it, so I cant say it wouldnt break something, though I dont see why it would.

Unless you are talking about editing the names of the menus themselves, that I'm not sure about...

---

### Post by adamc83 on 2008-02-10
Think I might have found the answer to changing the names of Applications/Places/System, if thats what you meant... look at the files in /etc/xdg/menus. Again, something really might break if you tinker with them.

Look [here]("http://library.gnome.org/admin/system-admin-guide/stable/menustructure-0.html.en") for more info.

---

