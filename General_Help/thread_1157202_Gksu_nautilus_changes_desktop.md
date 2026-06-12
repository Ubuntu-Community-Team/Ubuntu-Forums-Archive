---
title: "Gksu nautilus changes desktop"
date: 2009-05-12
forum: General Help
---

### Post by Mordaneous on 2009-05-12
Hi there,

When I run ```
gksu nautilus
```, my wallpaper and icon settings go back to default, i.e. what the super user must be set to. I don't want this to happen when I run nautilus as su. Is there anyway I can stop the command from altering my wallpaper and desktop settings? At the moment I have to logout to go back to my personal wallpaper and desktop icon settings!

Thanks

---

### Post by exutable on 2009-05-12
Isn't gksu the same thing and su?

---

### Post by Mordaneous on 2009-05-12
Hmmm not sure but after some poking around ```
sudo nautilus --no-desktop
``` seems to do the trick. However I thought running apps as sudo is bad and gksu or gksudo is better, since nautilus uses the gnome front end?

---

### Post by exutable on 2009-05-12
Honestly,

I didn't even know about gksu or gksudo, I thought you were always supposed to use sudo.  I never use su, although I did when I used to have debian.

Did sudo work though?

---

### Post by FIONEX on 2009-05-12
that's really odd because I don't have that problem.  gksu is just a gtk front end to sudo, which allows you to run a command with "sudo" but not through a terminal.

---

### Post by Mordaneous on 2009-05-12
yeah thats what I thought. However when i try gksu it wipes out my wallpaper and desktop icons. sudo nautilus with the --no-desktop flag works fine though, but yes, this does mean I need to run it in a terminal each time.

---

### Post by fooman on 2009-05-12
what about:

```
gksudo nautilus --no-desktop
```

?

---

### Post by fooman on 2009-05-12
btw...you could also install the extension to nautilus called "nautilus-gksu" which will give the ability to *right click* on any folder/directory/file and choose "open as administrator" from the drop-down context menu...thus opening nautilus as root.

i prefer that over having to open a terminal to do the "gksudo nautilus" command.

to install,  search in synaptic for "nautilus-gksu"...or open a terminal and type or copy/paste:

```
sudo apt-get install nautilus-gksu
```after it installs, log out and back in again to see the change.  then open your home folder and right click on a folder....you should see "open as administrator" as an option now.

---

### Post by Penguin Guy on 2009-05-12
Do not use [COLOR="Red"]sudo[/COLOR] for graphical applications.
Always use [COLOR="Green"]gksu[/COLOR] or [COLOR="Green"]gksudo[/COLOR] for graphical applications.

[COLOR="Red"]sudo[/COLOR] uses your configuration files.
[COLOR="Green"]gksudo[/COLOR] uses root's configuration files.

Some applications can cause errors, destruction, or simply not run if you use [COLOR="Red"]sudo[/COLOR]; although these are in the minority it is still safer to use [COLOR="Green"]gksudo[/COLOR].

For more information see the [[COLOR="Blue"]psychocat guide[/COLOR]]("http://www.psychocats.net/ubuntu/graphicalsudo").

Your problem can be easily solved by copying your themes and icons into /usr/share or /root.

---

### Post by Mordaneous on 2009-05-13
> **fooman said:**
> btw...you could also install the extension to nautilus called "nautilus-gksu" which will give the ability to *right click* on any folder/directory/file and choose "open as administrator" from the drop-down context menu...thus opening nautilus as root.

I too prefer that way, but as it uses gksu it wipes out my wallpaper and icons on the desktop. And yes I have also set up symlinks so sudo apps use my themes etc. Thats not the problem, only the desktop is affected! Using sudo in the terminal is the only way this doesn't happen, but as mentioned I'm not keen on using sudo all the time :sad:

---

### Post by measekite on 2009-07-14
> **fooman said:**
> btw...you could also install the extension to nautilus called &quot;nautilus-gksu&quot; which will give the ability to *right click* on any folder/directory/file and choose &quot;open as administrator&quot; from the drop-down context menu...thus opening nautilus as root.

i prefer that over having to open a terminal to do the &quot;gksudo nautilus&quot; command.

to install,  search in synaptic for &quot;nautilus-gksu&quot;...or open a terminal and type or copy/paste:

```
sudo apt-get install nautilus-gksu
```after it installs, log out and back in again to see the change.  then open your home folder and right click on a folder....you should see &quot;open as administrator&quot; as an option now.

 I ried this and it works but with a problem.  It works find when you rt click on a file like fstab but does not work when you rt click on a folder.    When you right click on a folder the same thing happens.  You get the root desktop and colors.  Does anybody have any idea why this happens?

---

