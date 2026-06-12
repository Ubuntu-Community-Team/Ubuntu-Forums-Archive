---
title: "How do i get an app to start on boot?"
date: 2006-08-15
forum: Desktop Environments
---

### Post by trojanlinux on 2006-08-15
I want KOrganizer to start every time I turn on my computer. I know in windows you would just drag it into the "startup folder". But windows sucks, so how do i do it in ubuntu?

---

### Post by mority on 2006-08-15
Well, in Ubuntu, there is a tab "Startup Programs" at System -> Preferences -> Sessions. There you can add the programs you want to be started after Gnome login.

But if you use KOrganizer, you are possibly using Kubuntu (which has the KDE Desktop as default), and I don't know how to do it in KDE.

---

### Post by trojanlinux on 2006-08-15
I am using ubuntu, i like Korganizer. I added the koraganizer shortcut that is on the desktop to the startup programs. However when i restart it does not start the program.

---

### Post by mority on 2006-08-15
> **trojanlinux said:**
> I am using ubuntu, i like Korganizer. I added the koraganizer shortcut that is on the desktop to the startup programs. However when i restart it does not start the program.

Hmm, to be honest I am not an expert of the Gnome sessions feature.

Try to add the actual executable to the Startup Programs like '/usr/bin/korganizer'. You can determine the right command with 'which' like this:
```
which korganizer
```

---

### Post by Thulemanden on 2006-08-15
Try writing the start command in a file and place it in  the folder  /home/[user]/Desktop/Home/.kde/Autostart

---

### Post by mority on 2006-08-16
> **Thulemanden said:**
> Try writing the start command in a file and place it in  the folder  /home/[user]/Desktop/Home/.kde/Autostart

He's using Gnome, not KDE...

---

### Post by Afkpuz on 2007-08-11
I'm running ubuntu with kontact as well and I've been toying around with the reminder dameon.  The best that I can do (I'm still working on it)  is to set Korganizer to run on startup.  That means that the icon in sys tray AND the Korganizer window itself will open on every startup.  If you can live with that, heres how you do it.


System->Preferences->Sessions


Click "New"


For Name, fill in "KOrganizer"
For Command, fill in "korganizer"

Click "ok"


Thats it.  The sessions work similar to a launcher.  The "name" is just anything that helps you remember what the program is called.  You could name it anything.  The command is the same line that you would use when creating a custom launcher.  So if you wanted to start up say, the calculator at every start up, you could goto 

Applications->Accessories   

and right click on calculator.  Click "add this launcher to panel".
Then, right-click on the newly added panel icon and select "properties".  This will tell you the command used to run the calculator.  In this case, it's "gcalctool".

So, if you wanted to run the calculator each startup, you would follow the same steps you did for korganizer, but you would paste "gcalctool" into the command box, instead of korganzier.  You'd also probably use a more appropriate name, like "Calculator".

Does that help?

---

