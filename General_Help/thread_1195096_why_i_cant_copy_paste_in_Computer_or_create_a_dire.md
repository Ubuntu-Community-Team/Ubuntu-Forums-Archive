---
title: "why i cant copy paste in Computer or create a directory..?"
date: 2009-06-23
forum: General Help
---

### Post by hasatmax on 2009-06-23
I am totally new to ubuntu and wonder why I cant create directories and copy paste either.
I had to install a  tomcat plugin for eclipse but the plugin has to be extracted in Plugins folder of Eclipse in "File System". Is there any terminal commands to get it running, would be grateful if someone could guide me through this. And yeah, it is a wonderful community ofcourse.

Thanks,
hasatmax.

---

### Post by VCoolio on 2009-06-23
For everything in your filesystem you need root permissions. For commandline you either do "sudo -s" which will give you a root shell or you do "sudo" in front of your cp or mkdir command.
To do all this with nautilus run "gksudo nautilus".
Of course, do all of this with caution, messing around while having root permissions can do a lot of damage.

Also check if you can put the plugin in the user folders of eclipse, something like ~/.eclipse/plugins or ~/.local/share/eclipse/plugins. That wouldn't require root permissions of course and would be a lot safer. I'm not sure of this, I thought of it yesterday as you can do this with vlc skins that normally go somewhere in the system section. (don't be offended if you know this already, but ~/ stands for /home/username and everything with a dot in front of it means it's hidden, so in nautilus press ctrl+h to see them).

---

### Post by jonobr on 2009-06-23
Hey Man


Your all over the road here :D

Creating a folder, on the desktop, right click and select create new folder or in the command line, open a terminal and type

```
mkdir myfolder
```
Note that when you open a command line in terminal, you are in your home directory. (~/username)

To move that folder to your desktop

```
mv myfolder Desk*
```

None of this requires root permission if you do it in your own home directory

You can also open "places" and select file->create folder

You can then right click and select copy, and then paste to wherever you want

---

### Post by aeiah on 2009-06-23
this isnt completley applicable, but might be useful to you:

[http://ubuntuforums.org/showthread.php?t=1191842](http://ubuntuforums.org/showthread.php?t=1191842)

---

### Post by DirtDawg on 2009-06-23
> **hasatmax said:**
> I am totally new to ubuntu and wonder why I cant create directories and copy paste either.
I had to install a  tomcat plugin for eclipse but the plugin has to be extracted in Plugins folder of Eclipse in "File System". Is there any terminal commands to get it running, would be grateful if someone could guide me through this. And yeah, it is a wonderful community ofcourse.

Thanks,
hasatmax.

Hi. If you need to move something into the "File System" area of your computer, you will need to use "root" to move them there. The command line version of this would be:
```
sudo cp /path/to/plugin /path/to/plugin/destination
```

The first slash (/) is shorthand for what you refer to as "File System."

Another way to do this using the GUI is to enter this into a terminal (or press ALT+F2):
```
gksu nautilus
```
This will open up the file browser with root permissions, allowing you to move files freely between your home directory (where you have read and write permissions) and the root directories (where you do not).

Conversely, although I do not use Eclipse, I have read that it's possible to install plugins via Help>Software & Updates>Find And Install within Eclipse.

I wish I could point you to a good tutorial about permissions and root, but I'm not sure of any off the top of my head.

EDIT: Yikes, like 4 people responded in the time it took me to write this response!

---

### Post by jonobr on 2009-06-23
Lol Dirtdawg.........

You have to be quick in this game..........!!!!!!

---

### Post by hasatmax on 2009-06-23
Thanks so much guyz, that was really fast and it did work !! you guys are sooo wonderful..


Cheers to this community.
hasatmax.:popcorn:

---

### Post by 3rdalbum on 2009-06-23
Even better solution than gksudo nautilus: Install the "nautilus-gksu" package from Synaptic. Whenever you want to open a file or folder as root, you can then right-click on it and select "Open as Administrator".

Note you need to log out and log back in after installing, in order for the menu item to show.

---

