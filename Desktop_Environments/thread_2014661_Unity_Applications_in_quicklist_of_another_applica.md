---
title: "Unity: Applications in quicklist of another application's icon"
date: 2012-07-02
forum: Desktop Environments
---

### Post by Margaret Dumont on 2012-07-02
Dear all,

I've recently installed Ubuntu 12.04 and, although I globally like it, I find that searching and launching applications is not very practical.

The fact that the launch bar compresses icons and that they can be scrolled is nice, but as you get more and more applications it all gets cluttered and it's not so fast to open this or that program. Besides, they are all mixed together.

I miss a way to group and organise the icons in the launch bar at will so I can quickly find what I want to use.

On the other hand, the dash menu is also nice, but the fact that you cannot choose which programs you want it to show and that you have to type the name or select a filter it also makes it very slow. If at least there was a modifiable "Favourites" lens... I checked into creating new lens so I could use them as a sort of "submenu" when right clicking on the dash icon, but it looked quite advanced and more focused to developers than to users.

Right now my approach was to use MyUnity to edit quicklists and try to create a sort of organised structure to launch applications. My idea was that I could keep my most used applications in the launch bar, and that right clicking on them would yield a list of applications related to that subject.

For instance, Firefox launch icon would yield a menu with the other internet applications that I use most (that is, Transmission, Mumble...); Gedit launch icon would yield a quicklist with Libre Office Writer, Kile, Texmaker, Impress, Calc...; or Gnome Control Center could contain MyUnity, the System Monitor, Ubuntu Software Center, and Synaptic Package Manager...

Adding "myunity" and "system monitor" to the Gnome Control Center quicklist, and "gksu synaptic" to the Ubuntu Software Center quicklist  yielded flawless results.

However, I am experiencing many problems with the rest:

[LIST]
[*]Adding "ubuntu-software-center" to the "gnome-control-center" quicklist made the option appear but clicking on it was unresponsive.
[*]Adding "mumble" and "transmission-gtk" to the Firefox quicklist makes the three programs work, but from time to time launching Firefox makes a new Firefox icon appear as if it didn't recognise that it was the same thing. Transmission and Mumble shortcuts are already included in this new icon, but I need to clic on its "Keep in launcher" option and remove the old one to avoid having multiple Firefox icons.
[*]Besides, sometimes Firefox doesn't show the "Close, minimize, restore" icons on the upper left, nor can be selected trough the "Alt+Tab" option to shift between running applications (it just doesn't appear there anymore). However, if the other windows are minimized, it is still there in the background and can be used normally. And if additional Firefox windows are opened, they work normally. Removing the "mumble" and "transmission-gtk" links from its quicklist makes the "lost" Firefox windows appear at once.
[*]I tried to add the commands "libreoffice", "libreoffice --writer %U" and "libreoffice --writer" to the text editor icon but with any of them the quicklist just shows the "Open new document/window" gedit options and ignores any reference to libreoffice.
[/LIST]
I'm not sure whether this has to do with the fact that I do not know the exact commands that should be used in the terminal to call each program (althought I've tried Libre Office's aforementioned commands in a terminal and they work fine), whether there is a deeper conflict with the launch bar because quicklists are not designed to call different programs than the one from the main icon (just different options of the same program), or whether is just a limitation of the MyUnity editor.

On the other hand, I've also had problems when removing application icons from the launcher, which made them permanently out of the launcher (for instance, the text editor). I was expecting them to appear in the launcher temporarily when I was running the application again, but this was not the case. Now I don't know how to get those icons back to the launcher when I open them. I'm not sure whether this is just my ignorance on the proper way to do this or some kind of bug.

Any help/ideas will be greatly apreciated.   :)

---

### Post by Margaret Dumont on 2012-07-02
Hello,

Luckily, the issue with the icon permanently not appearing on  the launcher (even when the program was running) has been solved after  rebooting. At least for the moment. 

And I've seen that the problem with "ubuntu-software-center" was that  the label appearing in the launcher is misleading. The command "software-center"  gives the desired result, although the first time yielded a MyUnity  error ("This application has  yielded an unexpected error and must abort. [29] Invalid object.  FMain.?.0"), but it seems to work fine.

Some more information:

[LIST]
[*]I've tried to add various programs ("libreoffice --write",  "gedit") to the quicklist of a random simple game ("loopy") because I've  thought it probably won't be so integrated as the Text Editor, Firefox  or Libre Office. This has worked perfectly fine.
[*]I could add "gedit" to the quicklist of the Libre Office Writer  icon and it seems to work well, although the first time yielded the same  MyUnity error ("This application has yielded an unexpected error and  must abort. [29] Invalid object. FMain.?.0").
[*]I couldn't add anything to the gedit/text editor quicklist (I've tried with different programs).
[/LIST]
 So, apart from erratic behaviour, I think I've basically reduced all my problems to one:
**I cannot add anything to the gedit/Text Editor quicklist.** 

Does anyone know why or how to solve it?

---

### Post by Margaret Dumont on 2012-07-02
Hello again,

Since simple editing using MyUnity was not working, I tried to learn how to edit the launch files directly. [Here]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles") you have some instructions on how to do that.

However, I still couldn't make it work. Finally I have found out it is an issue of the quicklists editor of MyUnity. I post it here just in case it is of use to someone else.

It seems that the syntax for the quicklist shortcuts has just changed from Ubuntu 12.04 version onward (check mc4man comment on [this thread]("http://ubuntuforums.org/showthread.php?t=1962862")) and I've realised that MyUnity is using the old syntax. In principle the old syntax should still be working but when both old and new are mixed, it doesn't. This is what caused items in my launcher without a previous quicklist to work flawlessly and  items which already had a quicklist to have mixed syntax and yield that strange behaviour.

MyUnity editor does two things to the file "Nameofitem.desktop", which in my case it was located in "~/.local/share/applications":

[LIST=1]
[*] It adds the quicklist items to the "X-Ayatana-Desktop-Shortcuts" list adding a semicolon before and after each item name (I think only one is needed but I guess having two won't be a problem): 
```
X-Ayatana-Desktop-Shortcuts=Name of item 1;;Name of item 2;;Name of item 3;
```
[*]It adds an instruction block for every item at the end of the file with this syntax:
```
[Name of item 1 Shortcut Group]
Name=Name of item 1
Exec=Command in terminal
TargetEnvironment=Unity
```
[/LIST]

With the new syntax it should do instead:

[LIST=1]
[*] Add the quicklist items to the "Actions" list adding a semicolon after each application name:
```
Actions=Name of item 1;Name of item 2;Name of item 3;
```
[*]Adds an instruction block for every item at the end of the file with this syntax:```
[Desktop Action Name of item 1]
Name=Name of item 1
Exec=Command in terminal
OnlyShowIn=Unity
```
[/LIST]
I had to remove by hand the old syntax that MyUnity had added (it doesn't completely remove it when you do it from the editor) and add the items I wanted in the quicklist by hand with the new syntax. 

However, the small arrows that indicate whether the program is running do not appear near the icon in the launcher... But I can live with that.   :)

---

### Post by Merrattic on 2012-07-21
Thanks for the tips on what MyUnity is not doing! Although the MyUnity syntax seems to work for some launchers, it has no effect with others

---

### Post by funicorn on 2012-07-21
thanks for your efforts. I tried to edit the unity quicklist and found out the old way either to write the desktop file or to use my unity failed. Funny thing is  a gui tool called unity launcher editor, of a new version for 12.04,  failed too.

---

### Post by mc4man on 2012-07-21
> **funicorn said:**
> thanks for your efforts. I tried to edit the unity quicklist and found out the old way either to write the desktop file or to use my unity failed. Funny thing is  a gui tool called unity launcher editor, of a new version for 12.04,  failed too.

If you'd like, - find the .desktop you were trying to edit the quicl;ist in, open in a text editor & post the contents in a code box.
Plus describe what you were trying to add

---

