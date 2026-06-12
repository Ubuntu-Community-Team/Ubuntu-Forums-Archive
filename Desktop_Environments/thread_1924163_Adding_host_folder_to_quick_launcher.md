---
title: "Adding host folder to quick launcher"
date: 2012-02-12
forum: Desktop Environments
---

### Post by propo on 2012-02-12
I would like to add a icon on the quicklist in Ubuntu 11 to go the my host folder and folders in there as all my files are on the host. How do I go about this?

---

### Post by Frogs Hair on 2012-02-12
Hello and Welcome 

Is this 11.04 or 11.10 ? Since you have host access I am guessing you are using Wubi ? You could first try copying the files to Ubuntu home if you have the space .

I think the path  would be something like this: Home - File System - Host - Users - User Name and finally to the pictures , music , and other folders  . 

A launcher and a quick list are not the same thing . A launcher can be created with the main menu granted the command is correct .

---

### Post by propo on 2012-02-12
It's 11.10, just got it installed and miss the days I could just drag drop anything to the top bar, now being the leftside quick launch bar, and have my quick launch to something. But the new launch bar doesn't go with drag drop. 
You're correct it's /file system/host/~docs... folder where I would like to have a quick launch icon for. The folder is quite big, and I think its a waste of space to have things double. I do have a link in the home folder but I like clicking and going in one go :)

---

### Post by Frogs Hair on 2012-02-12
Take a look at the link . If you try to drag the host folder to the Ubuntu desktop it will likely copy the entire contents of the host folder , which will be bigger than Wubi allows .  

[http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html](http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html)

---

### Post by propo on 2012-02-13
I tried it but dragging it to the launch bar only works when its an application. It doesn't work with a Location, it instantly springs back to the desktop :sad:.

---

### Post by Frogs Hair on 2012-02-13
I have not tried this and don't know if it is possible to add the host file and its directories .[http://everythingexpress.wordpress.com/2011/11/22/how-to-add-places-as-quicklists-in-unity/](http://everythingexpress.wordpress.com/2011/11/22/how-to-add-places-as-quicklists-in-unity/)

A dual boot with Ubuntu on its own partition would allow for the creation of a data partition accessible from both operating systems . This would require some home work and help from someone who has done it .

If I were to do the above I would wait until 12.04 is released in a April because it will have 5 year support . Remember that Wubi installations are suggested for temporary use as a means to try Ubuntu .

---

### Post by Krytarik on 2012-02-13
> **propo said:**
> I tried it but dragging it to the launch bar only works when its an application. It doesn't work with a Location, it instantly springs back to the desktop :sad:.
Don't set it up as "Location", but as a usual "Application", with the command "nautilus /host". And also, notice that if you drag it from your desktop into the Launcher, the original file must stay on the desktop; if you don't plan to keep it there, move/copy it instead into your "~/.local/share/applications" directory, and drag it from there into your Launcher.

Regards.

---

### Post by propo on 2012-02-14
Yes! it worked, both are good solutions but I didn't quite understood the nautilus thing from the howto, needs to be: Exec=nautilus /host/...; . Took a while (i.e. taskbar) but Ubuntu 11 is finally configured to my liking. Thanks guys.

---

