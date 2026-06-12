---
title: "How to find launcher commands for apps"
date: 2006-07-12
forum: Desktop Environments
---

### Post by hedonistic.heathen on 2006-07-12
I've casually been toying with dapper for a few weeks now and I really like it thus far (except for the fact that I've spent 20+ hours trying to get my BCM4311 wireless card to work without success), but one thing that I don't care for is the management of newly installed applications...

I download an application via syanptic or apt-get and I have no idea what folders it is installed in...So, I do a  Places>Search for the app that I just installed and there's no executable file (or an odly labeled file that would indicate it will run the app) so I find myself randomly clicking files until the app opens up.  This isn't exactly fun or efficient.

Is there a reliable way to find the command that will launch the application from terminal so that I can create a launcher?


For instance I just installed gaim-guifications so that I can install a new theme for gaim, but all the forum posts talk about dragging and dropping the theme file into the guifications window...Problem is I don't know how to open guifications so that I can get a window to drop the theme file into...I've googled and searched the forums and I can't seem to find the terminal command that opens guifications and none of the files found by the search function open it either...

I hope someone can share a method that makes installing, running, and organizing applications a bit more efficient.  Windows asks where I want to install an app, gives me the option to pin it to the start menu, and gives me an executable icon which I can click to run the app.  I'm not asking for a windows clone, but I'm guessing expereinced linux users don't have such difficulties locating, organizing, and running apps as I have, so feel free to make suggestions.

---

### Post by scxtt on 2006-07-12
> Is there a reliable way to find the command that will launch the application from terminal so that I can create a launcher?
whereis <name_of_app>
[indent]example:

:> whereis gaim
gaim: /usr/bin/gaim /etc/gaim /usr/lib/gaim /usr/bin/X11/gaim /usr/share/man/man1/gaim.1.gz[/indent]

one word of advice, don't try to impose the windows way of doing things on linux, there's a reason most packages install to default directories in the way they do ... if you want to control where things install, you'll probably like a disto that doesn't rely heavily on repos ["configure", "make", "install"] ...

---

