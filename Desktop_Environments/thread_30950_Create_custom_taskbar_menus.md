---
title: "Create custom taskbar menus?"
date: 2005-05-01
forum: Desktop Environments
---

### Post by dlanor78 on 2005-05-01
I was wondering if it's possible to create customized menu items like the k button or the system button.  For example, one button that I can click on and a menu that pops up with all my internet apps inside it.  This would be great for people like me that like tu use lots of quick launch icons  ;-)

---

### Post by Nob on 2005-05-01
yes, i believe so.. i havent used kde for a long time, but i think u can add folder just as usual application, and when you click on it, you get its contents..

so u can make application menu by creating sim-links in that folder ;)

---

### Post by gunnyman on 2005-05-01
Easily add items from Kmenu to task bar like this:
Right click taskbar
Choose add to panel
Choose application
Apps from Kmenu appear,
choose (for example) internet
choose Add this menu.

---

### Post by exile on 2005-05-01
Nob is correct.

Create a folder. Put links to your apps or files into the directory then drag it onto your  KDE panel.

Select add as Quick Browser.

You can change the appearance of the icon in the panel by right clicking and going to properties..

---

### Post by dlanor78 on 2005-05-01
Thanks for the responses guys.  I did know about the method gunnyman described, but some of the things I want in the task bar aren't listed in the k menu (mostly things installed from source).  I tried out the other method but I must be doing something wrong.

If I drag and drop the app I want to run (like azureus) into a folder and choose "link here", nothing happens when I click on it.  I also tried "ln -s /path/to/file /path/for/link" and same thing.  Also, I can't seem to change the icon for the link once it's made.  I know this has to be possible or else the system button (with links to home, storage media, remote places...etc) wouldn't be possible.  Any ideas what's wrong here?

[update]
Okay, I found something that seems to work okay.  I just edited the k menu and created my own folder in the Internet section called Quicklaunch Internet Appz.  Then I put the links I wanted in that folder and told it to "Add Menu To Main Panel".  The only downer is now everytime I go to the k menu and the Internet section, I'll see that folder, but I can live with that :)

[update2]
I just tried something on a whim.  I remembered that in konqueror folders that have a . (period) before them are hidden.  So I went back to the menu editor and put a .befor my new folder.  Now it's hidden in the k menu and I can still access the folder in the panel.  Sweet  :grin:

Now if only I could figure out how to unhide that folder in the k menu editor so I can edit it again later.  Anyone know where these folders are so I can browse there in konqueror or something?

---

### Post by dlanor78 on 2005-05-01
Okay, that last post was starting to get a little long  ;-) I got my kmenu item back by editing the /home/user/.config/menus/applications-kmenuedit.menu file and restarting X.  And to create a folder with lauchable links, just make the folder, go into it (in konqueror, not sure how to do next step in shell) and right click>Create New>Link To Application.  Then drag this folder to the taskbar.  If you can stand the "Open In File Manager" and "Open In Terminal buttons, this works fine.

I prefer the other method I used.  Creating an entry in the k menu and putting the links there.  Then to the taskbar.  It just looks better in my opinion :)

---

