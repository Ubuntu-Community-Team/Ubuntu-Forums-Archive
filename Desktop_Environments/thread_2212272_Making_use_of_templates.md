---
title: "Making use of templates"
date: 2014-03-20
forum: Desktop Environments
---

### Post by Langstracht on 2014-03-20
I would like to create a spreadsheet file of multiple sheets each containing/using the same template.

It seems the only way to access the template menu is through File>New which of course opens a new file.

Is there a way that I am missing to just "insert" a template into a sheet?

If not, then is there a way of "opening" the template directly (i,e. not opening a spreadsheet first and importing the template) from the command line?  I don't like it too much but at least it saves some keystrokes.

---

### Post by ajgreeny on 2014-03-20
Just open the generic starter application for libreoffice (command **libreoffice**) instead of a spreadsheet and from that you can get to the template manager, and choose the template you want to use.

If you want to make a new template just set up the document or spreadsheet layout etc etc as you want then go to [B]File ->Templates ->Save as template

[/B]PS: My pic is of LO 4.2.2.1 from the ppa I use in Xubuntu 12.04.

---

### Post by Langstracht on 2014-03-20
Thank you.  I hadn't realized that.  

However, what I want to do is "open" the chosen template from the command line (well actually in a crontab file but that's another story).

Anything I've tried doesn't work.

Is this something that CAN be done?

---

### Post by ajgreeny on 2014-03-20
Yes it can.  You need to know the filename of your template and use command ```
libreoffice /home/username/.config/libreoffice/4/user/template/filename.ots
```changing the pathway I show here to your own system.

You will need to use the full pathway in a cron job, as I show here, as I don't think just using a shortcut eg ~/ for your home will work.

---

### Post by Langstracht on 2014-03-21
Brilliant.  Works like a charm.

Thanks VERY much.

---

