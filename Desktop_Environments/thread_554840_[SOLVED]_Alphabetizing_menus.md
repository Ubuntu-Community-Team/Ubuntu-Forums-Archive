---
title: "[SOLVED] Alphabetizing menus?"
date: 2007-09-19
forum: Desktop Environments
---

### Post by citizenofnowhere on 2007-09-19
Hi all,

How do you alphabetize the applications listed in my gnome menu? I'm not sure why, but I honestly couldn't find a lead on this on the forums. 

I know it's supposed to be already arranged like that by default, and I know I can right click and use "Edit Menus", but that requires me to drag and drop them one by one (and eats my CPU like candy).

Does any one know any other way to make these behave? The command line is my friend, not afraid to pop the hood and get messy, as long as it gets done.

I'm on the Feisty version of Gnome by the way, 2.18

Thanks in advance for any thoughts!

---

### Post by Wolki on 2007-09-19
> **citizenofnowhere said:**
> I know it's supposed to be already arranged like that by default, and I know I can right click and use "Edit Menus", but that requires me to drag and drop them one by one (and eats my CPU like candy).

Does any one know any other way to make these behave? The command line is my friend, not afraid to pop the hood and get messy, as long as it gets done.

As far as I know the menus will auto-sort alphabetically as long as you did not change the layout manually. So what we'll have to do is tell the system you don't want the order you specified anymore.

Open the file "~/.config/menus/applications.menu". It's an xml file and you should be able to find one or more sections called <layout>. If you do,. backup the file, then remove these sections (ie delete everything between the opening <layout> and the next closing </layout> tag. Then restart the panel and see if it works now.

---

### Post by citizenofnowhere on 2007-09-19
Worked like a charm! Thanks mate!

PS. Didn't need to restart the panel (some of my status area applets don't play nice if I kill the panel), just removed the menu applet from the panel and added it back in.

---

