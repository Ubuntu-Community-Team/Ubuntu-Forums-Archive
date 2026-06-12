---
title: "Remove menu items in gnome"
date: 2005-06-28
forum: Desktop Environments
---

### Post by RikoW on 2005-06-28
Dear all,

I used the gnome menu editor to add some entries to the Application -> Internet menu.

Is there a way to remove those items again, since one appears twice now. The menu editor does not let you do that, however I assume there is somewhere a config file, which defines the menu entries and which could be edited by hand. However, so far I haven't found it yet. 

I'm sure someone here can whip this info just out of his/her pocket :)

Thanks,
                Riko

---

### Post by codejunkie on 2005-06-28
click on Places then search for files and then on Look in Folder and choose the  /usr directory. for example: you added gaim search for gaim.desktop this will show the directory the file or files are located in to remove or edit it you need root access to that file so open a terminal and start nautilus with root privileges with the command 
```
sudo nautilus --browser
``` hope this helps.

---

### Post by dissident on 2005-06-28
Look in  ~/.local/share/applications/ and /usr/share/applications/

---

### Post by RikoW on 2005-06-28
Thanks! everybody!

/usr/share/applications gave the entry that was screwed up.
I thought, I had created that entry, but all others I created with menu editor are in ~/.local/share/applications

Anyway, things are now the way I want them :)

Cheers,

       Riko

---

