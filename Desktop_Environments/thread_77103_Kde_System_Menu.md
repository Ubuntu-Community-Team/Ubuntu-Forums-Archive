---
title: "Kde System Menu"
date: 2005-10-16
forum: Desktop Environments
---

### Post by compmodder26 on 2005-10-16
I've searched all over for this and I can't seem to find anything on it.  Is there a way to edit the System Menu that is on the taskbar?

---

### Post by aysiu on 2005-10-16
Right-click on the panel.
Configure panel.
Menu.
Edit K Menu.

---

### Post by Takis on 2005-10-16
I think he/she means the System Menu like you get if you type in 'system:/' in Konqueror, and no, I don't think you can change it too easily.

---

### Post by compmodder26 on 2005-10-19
Yes the system menu is what I was referring to.  Any ideas if there is a config file somewhere for it?  I've looked through all the KDE config files I could find but I haven't been able to turn up anything.

---

### Post by fp-www.tonepad.com on 2005-12-23
I am interested in this also.

With a fresh Kubuntu Breezy install I get the following links under the System Menu:

url in konqueror window__________ (name shown in menu)
/home/user ____________________(home folder)
media:/ ______________________(storage media)
remote:/ ___________________(remote places)
settings:/ _________________(settings)
trash:/ ____________________(trash)

AND after upgrading (kde, I think) I get:

url in konqueror window__________ (name shown in menu)
system:/home ____________________(home folder)
system:/media ______________________(storage media)
system:/remote ___________________(remote places)
system:/trash ____________________(trash)
system:/users ___________________ (users folders)

(please notice the differences between the two)

I don't want this change, I want to go back to the previous menu, I find it's much more useful, gives me more information on the media and allows me to do more things on my home folder.

I can always manually put the urls from the first (original, desired) menu in konqueror, but I want it done automatically when i click on the menu items.

Any help on how to change the second menu to be like the first I would greatly appreciate it.

Fp

---

### Post by entangled on 2005-12-23
There is a serious side effect too. 
If I open System Menu: Home folder and browse, the URL shows as system:/home. However, it shows the contents of *my* home folder, otherwise known as /home/peter, so I assume that system:home is an alias. I can browse the files but when I try to open an odt document with OpenOffice writer it fails to load and OO aborts. 
If I then type the proper directory name of /home/peter into the URL box, continue browsing and try to open the same odt document, OO loads it properly.
I suspect that OO does not know how to deal with the aliased file paths. 
I consider OO to be broken by the change to system menu until this is fixed.

BTW. gvim and Kate can load the file, OO and gedit cannot.

Please let me know if others have the same problem. If you can verify then I will submit a bug report.

---

### Post by fp-www.tonepad.com on 2005-12-23
I have submitted a bug report. 

[http://bugs.kde.org/show_bug.cgi?id=118935](http://bugs.kde.org/show_bug.cgi?id=118935)

more details in that link.

---

### Post by jeremy on 2005-12-24
I have posted a fix to the openoffice problem at:
[http://ubuntuforums.org/showthread.php?p=546408#post546408](http://ubuntuforums.org/showthread.php?p=546408#post546408)

---

### Post by entangled on 2005-12-24
Thanks very much Jeremy. The %f tip works nicely. 
Unfortunately I had just reported the bug (again, it seems, despite searching the buglist and forums first).
It seems this is a little integration problem that would not have happened if file associations of the more common applications were tested. So I think the bug belongs with the KDE release rather than the applications.

---

