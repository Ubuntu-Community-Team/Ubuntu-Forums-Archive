---
title: "how to set permissions?"
date: 2006-10-01
forum: Desktop Environments
---

### Post by tdog on 2006-10-01
HI.
im not sure if im in right place , feel free to move this to right place. 
I installed apache, php, mysql. but i have no permission to do anything.
I read about setting permission using sudo and stuff, but im new to linux and i can not undrestand. 
Im the only one going to use this Computer ,so is there anyway i can set permission on this PC so when ever i login , i have access to modify, read, write, execute , without having to resort to some shell comands. ???


Thanks

---

### Post by orb9220 on 2006-10-01
Drag a home or computer icon to panel. Then right click icon on panel and select properties. In the command field change it to: gksudo -g nautilus.
Then just click on when you want sudo abilities for copying,moving,renaming,delete,ect...

And when you run a command just add word sudo or gksudo for graphic based apps.

The whole point of linux is security. If I want access to everything all the time then so can others and will. That is what windows problem is sloppy security.

---

### Post by rbprogrammer on 2006-10-01
i'm the same way, but what i do to still maintain a level of security (especially from myself screwing up the system), i put myself into the group [admin] or [adm] or both and everytime i need to do something with a protected file that is used for root, i change the file's group to [admin] or [adm].

to change a group:
sudo chgrp admin /path/to/file/or/folder

to change permissions on that file/folder:
sudo chmod --- /path/to/file/or/folder

now the [---], the first dash is the owner, the second dash is the group and the last dash is everyone else.  each dash can have a 1,2,3,4,5,6, or 7.

4 = read
2 = write
1 = execute

the most common code that i use is 775, which for the:
owner - read, write, and execute access
group - read, write, and execute access
others - read and execute access

then the command would be:
sudo chmod 775 /path/to/file/or/folder

hope that helps........

---

### Post by rbprogrammer on 2006-10-01
oh, well if you dont like the commands, then orb9220's suggestion if much better

---

### Post by gdoermann on 2007-09-03
Ok,
So I have mounted a new partition and have successfully added it to the fstab.  So I have mounted it to /storage and I am wondering how do I get the permissions right?  I tried editing it in nautalis (under properties) I tried 
```
sudo chmod 755 /storage
```

I also tried
```
sudo chown -R doermann:doermann /storage 
```

When I go to /storage I can see and access the files.  I think the permissions are correct but when I right click the folder it doesn't show new folder or new file as an option (in nautalis)

---

### Post by dm3nt0r on 2008-06-28
I dont understand what u mean by pulling home into panel.. what panel? where is this panel?

---

### Post by Milkium on 2008-06-29
> **dm3nt0r said:**
> I dont understand what u mean by pulling home into panel.. what panel? where is this panel?It's the bar at the very top where the drop down menus "Applications" "places" and "System"
 are located.

---

