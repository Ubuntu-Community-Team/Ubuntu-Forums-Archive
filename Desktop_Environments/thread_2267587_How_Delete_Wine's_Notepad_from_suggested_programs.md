---
title: "How: Delete Wine's Notepad from suggested programs"
date: 2015-03-02
forum: Desktop Environments
---

### Post by LanceHaverkamp on 2015-03-02
How do I **completely** delete Wine's Notepad from xubuntu's suggested programs?

I never, ever want Linux to try to open any file-type with Notepad.  Why is it even installed this way?  Would anyone ever want to open a non-wine file with a Windows editor?


Thanks!
Lance

---

### Post by grahammechanical on 2015-03-02
Someone who installed wine and a Windows application through wine might want to use it. Wine uses a file structure that imitates the Windows file structure. When Windows applications are installed through wine the components of the application go into the same kind of folders just as they would do if actually installed in Windows. These applications have ini files and other stuff that one would expect a Windows application to have.

I guess the wine developers thought they were being helpful by providing a text editor to edit those files that would be more convenient for a Windows user to use than an unfamiliar Linux text editor. 

But hey, it seems you can't please everyone. I do not use Xubuntu but I am sure that there is a method for removing application names from the Xubuntu menu system. Perhaps selecting the name and right clicking might bring up an option to remove. I have no idea.

I am pretty certain that Notepad will run through wine as a Windows application and I am fairly confident that any Windows application running through wine will have great difficulty in accessing the Linux file structure. Those Windows applications are generally not designed to even know that Linux exists.

---

### Post by raptir on 2015-03-03
To remove it from the options to open a text file you would need to change the mime association for the application.

Go to /usr/share/applications and edit notepad.desktop (or whatever WINE creates it as). You'll need to edit it as root. Find the line that says MimeType= and remove the types you no longer want it associated with. Save the file and then run:

```
sudo update-desktop-database
```

to make the changes effective.

---

### Post by Toz on 2015-03-03
Follow [these instructions]("http://askubuntu.com/questions/323437/how-to-prevent-wine-from-adding-file-associations/400430#400430") if you want to prevent wine from ever creating these associations in the first place.

---

