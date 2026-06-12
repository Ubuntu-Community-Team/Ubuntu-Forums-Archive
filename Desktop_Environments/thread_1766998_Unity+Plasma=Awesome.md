---
title: "Unity+Plasma=Awesome"
date: 2011-05-25
forum: Desktop Environments
---

### Post by ALF102 on 2011-05-25
For those who haven't heard of this you can go to the following link to try it out. 
[http://www.omgubuntu.co.uk/2011/05/how-to-run-kde-plasma-widgets-in-ubuntu-unity/](http://www.omgubuntu.co.uk/2011/05/how-to-run-kde-plasma-widgets-in-ubuntu-unity/)

[IMG]http://img841.imageshack.us/img841/5353/screenshot1up.png[/IMG]


Now then, if any of you are having difficulties involving:

1.  You want to have the plasma desktop run on startup by default.[INDENT]Step 1:  You create a file and named it plasmadesktop.sh or any other names you can    think of. Open the file and type this:
[/INDENT][INDENT]```
#!/bin/bash
sleep 3 && plasma-desktop
```and save.
[/INDENT][INDENT]*As you can notice I put the sleep time to 3, which means the plasma desktop start 3 seconds after the the login. I've tried to put 1 but somehow the resolution seems to break. You can try to experiment it on your own at your own rick of course.

Step 2: Open Startup Applications and add a new entry. Name should be anything you want to but I put mine as "Plasma Desktop". In the command area, just browse the previous file from step 1. After that done and save. Now you'll be able to automatically run plasma desktop on startup
[/INDENT]2. You can't find the Folder View widget or some of the default widget and you can't find it at the 'Get New Widget' Menu either.[INDENT]Step 1: You install them from the Ubuntu Software Center. Just search for "plasma widget".

[/INDENT]3.After you got Folder View widget, when you click on a folder it ask you to use which type of program to open the folder. By default, you won't have Dolphin installed with the plasma desktop and since installing Dolphin together with nautilus could cause some confusion (thats what happen to me).[INDENT]Step 1: Go the KDE system setting, you can access it from the KDE menu at the KDE panel of course.

Step 2: Go to Default Applications then click the File Manager

Step 3: Since you don't have dolphin install, there's only one option left that is to add one by choosing "Other"

Step 4:Open the "Other" dialouge and click "ADD" and type the following command:
```
nautilus --no-desktop
```Step 5: Click "Apply" and then "Ok"

*Now Folder View will open Nautilus as the default file browser.


[/INDENT][IMG]http://flic.kr/p/9LL9ec[/IMG]

---

