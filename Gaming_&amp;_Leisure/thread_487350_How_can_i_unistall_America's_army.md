---
title: "How can i unistall America's army?"
date: 2007-06-29
forum: Gaming &amp; Leisure
---

### Post by Jordan777 on 2007-06-29
i have tried sh uninstall (after changing directories of course). I have tried sudo sh uninstall (again cd).  I have tried using the unintsaller that came with it.  When i try it I get this message 

****Screenshot******
<username>:~$ armyops
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History: 

Exiting due to error
***********************

What I think happened was I tried to start it up and it worked but then it froze.  I didn't know how to exit it out so I tried something like ctrl+esc and it eventually closed out but since then it doesn't work any longer.  It jsut shows the AA logo and immediately cuts back to the desktop.  when i try to uninstall I get this message. 

*********Screenshot**************
<username>:~$ cd /usr/local/games/armyops
j<username>:/usr/local/games/armyops$ uninstall
bash: uninstall: command not found 

:(:(

Any ideas of what I can do?  I really want to play it.

---

### Post by SirPerigrin on 2007-06-29
Well, i am not too familiar with the program but i had similar issues with a botched install of VMware (It disagreed with my wifi card) and i was able to uninstall the old fashioned way with no future problems. I found all the files that the uninstall script would remove itself and manualy deleted them (I did this from root logged into Gnome with internet adapter powered off for security). Theoreticaly unless the program integrates itself into anything else or modifies system files (AOL anyone?) then you shouldn't have any issues with this slash and burn method. So, if somone more experienced comes along and says i'm not a total moron, then just use the search functions and find the AA files in the various directorys and trash them. Of course i do not claim to know what i'm doing, but it worked for me. Get the aproval of somone else BEFORE you try this method as, if i'm wrong, yeah, i'll probly **** somthing up :)

---

### Post by Jordan777 on 2007-06-29
Well being so used to windows that was one of my first methods when the command line failed me (I'm a newb don't hurt me).  BUT it unfortunately (or should I say fortunately?) will not manually delete.  It absolutely refuses to go to the trash bin.

---

### Post by avik on 2007-06-29
Where's the included uninstaller located?

Now, if you can't find any other option, yes, manually deleting the files will work.  You'll have to be root to delete those files.  You can use:

```
gksudo nautilus
```

(but be **extremely** careful what you delete), or you can use:

```

sudo rm *<filename>* # files
sudo rm -r *<dir_name>* # directories

```

Once again, be very careful.

---

### Post by Jordan777 on 2007-06-29
Thank you!! thank you thank you thank you!!! I just deleted the armyops folder and began to reinstall it.  thanks soo much man you helped me out big time.  :KS

---

