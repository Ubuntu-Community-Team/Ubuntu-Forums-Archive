---
title: "File searching in nautilus doesn't work. Do I miss something?"
date: 2007-10-25
forum: Desktop Environments
---

### Post by puqing on 2007-10-25
I often use the 'find' command to search my files. Today, I tried to use the search function in nautilus to do the job, but it didn't work. It always says "0 items" and shows a blank window.

I just upgraded the system to 7.10. But I am not sure whether this worked in the old version on my computer, since I don't use it often.

---

### Post by softtower on 2008-04-08
Same here: "Search" button does not search and nobody seems to care: I googled, I checed IRC, I searched here... Seems like Gnome's nautilus is simply broken and most just do everything in command line.

---

### Post by harrybazeegar on 2008-04-08
the search button in nautilus searches for files in the directory ( and all the subdirectories and their subdirectories and... ) for files that you want.

It does not search the entire system at time.

---

### Post by munkyeetr on 2008-04-08
You can use** Places **-> **Search for Files...** to perform a search. In the** Look in Folder:** field select where you want to look (default is your home directory). Use* File System* to search the entire computer, one of the other preset options, or* Other...* to choose another starting point.

If you find something you're looking for, right-click on it and choose Open and it will open in the proper program.


Alternately, you can add the ability to Search to the right-click menu in Nautilus as follows:

1) Install Nautilus Actions:
```

sudo apt-get install nautilus-actions

```

2) **System** -> **Preferences** ->** Nautilus Actions Configuration**
3) **Add** a new action
4) Fill in like so (*or customize as you want, this is how I have mine*):
[QUOTE]
**Menu Item & Action Tab**

Label: **Search...**
Tooltip: **Search this folder**
Icon: **gtk-find**
Path: **/usr/bin/gnome-search-tool**
Parameters: **--hidden --path=%M**

**Conditions Tab**
Filenames: *****
Mimetypes: ***/***
Appears if selections contains: **Only folders**

5) Done.

Now you can *right-click* on a directory in Nautilus and search it and any sub-directories. *Unfortunately it only works on the right-hand pane of Nautilus.*

* You may need to restart Nautilus for the changes to take effect.

---

### Post by vanadium on 2008-04-08
Currently, nautilus uses Beagle for the build in search. I don't think it is restricted to the current directory and its subdirectories. However, new files that are not yet indexed are not found. This is why the tool does not find files that are in fact there. I agree with you that the way this currently works is not suitable. For a directory based search, the "old system" is more suited. I also can only recommend to use Places - Search for files, which can be less convenient.

---

### Post by TokyoYank on 2008-07-14
Places > Search for files >> Advanced "Search hidden files"

The above does ***not*** search directories/sub... starting with a period.  

I'm trying to locate and migrate user config files from a user account on a Fedora machine, and I can't find anything.  .. Why is this such a hard thing to do?

..time to man "find" again...

---

