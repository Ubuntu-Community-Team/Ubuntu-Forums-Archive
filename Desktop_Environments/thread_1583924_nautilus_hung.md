---
title: "nautilus hung?"
date: 2010-09-28
forum: Desktop Environments
---

### Post by Shpadoinkle on 2010-09-28
upon installing updates for 10.10 this morning, nautilus seems to be hung. i cannot open any folders, nor right click on the desktop. when trying to run nautilus from the terminal, i get this output. 

```
nautilus: symbol lookup error: nautilus: undefined symbol: g_application_get_type
```

any ideas?

---

### Post by Shpadoinkle on 2010-09-28
help,anyone...

---

### Post by MariusLV on 2010-10-06
Try this:
sudo apt-get purge nautilus && apt-get install nautilus

---

### Post by justinlindh on 2010-10-06
For what it's worth, I had this same problem after updating/restarting this morning as well. The symptoms of it include Gnome attempting to load/reload nautilus very, very rapidly (the application panel is overwhelmed with entries).

I took the idiot approach and just 'apt-get remove nautilus', after which Gnome got very angry with me. I winded up having to "apt-get install --reinstall ubuntu-desktop" after making that mistake. MariusLV's suggestion, if it works, is probably preferable.

---

### Post by mister_p_1998 on 2010-10-07
Might be the same problem Ive had for a while...
[http://ubuntuforums.org/showthread.php?t=1587841](http://ubuntuforums.org/showthread.php?t=1587841)

---

### Post by MariusLV on 2010-10-07
The reason why I suggest to use "purge" rather than,  as justinlindh did, "remove", is that the remove-command only removes the application itself whilst leaving behind the configuration files. Therefore, if there is a problem with a configuration file, the problem will still manifest itself when you reinstall the application, because the fresh install will still use the same configuration files. The purge-command, on the other hand, deletes both the application AND the configuration files, making it the best way to ensure a fresh start when reinstalling. I'd say there's a good chance purging and reinstalling will fix your problem - at least it worked for me when I recently experienced similar symptoms.

If you use a lot of third-party software repositories, I suppose there is a chance your problems might be caused by faulty or conflicting packages. Now, this is pure speculation, of course, but if for some reason purging and reinstalling doesn't work, it might be worth trying it again after disabling all but Canonical's official Ubuntu repositories. Hope you manage to solve your problem.

---

