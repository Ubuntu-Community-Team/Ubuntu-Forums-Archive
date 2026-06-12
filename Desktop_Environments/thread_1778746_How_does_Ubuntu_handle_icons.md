---
title: "How does Ubuntu handle icons"
date: 2011-06-09
forum: Desktop Environments
---

### Post by Philip Gray on 2011-06-09
Hi

I have been posting a number of queries on themes etc. in a process to get my Ubuntu desktop to really look awesome. I have installed a bucket load of themes but have not really found what I am looking for. I like space wallpapers.

My problem is: In Windows you can click on an object (folder etc) and select 'Change Icon' and  change it. My question is: how do you do this in Linux? Some themes do not change folders etc, like they should, (they advise that you are missing an engine, windows manager etc. My bugbear us the authors of these these themes do not tell you what you need) so how do you get the icon you want? The glass themes is a good example. The only way that I can currently see is through icon themes. If they do not work, what then? 

Is this functionality that is missing? If so I think it should be developed. I have added desktop shortcuts to my desktop via gconf-editor, the corresponding shortcuts do not allow any mods. Why?

Regards
Philip

---

### Post by Tamlynmac on 2011-06-09
I've found the easiest way to change an icon in the menu or on the the desktop is to right click on the icon and select properties, then left click on the icon in the upper left corner of the properties window. At the top of the file manager 

For apps in the menu simply right click on the menu and select "edit menus". Find the app in the listing of individual menus and right click on the app in the right side window, then select properties and left click on the icon in the top left corner when the popup properties window opens.

On the desktop simply right click on the icon and select properties then when the properties window opens left click on the icon in the top left corner.

* I liked to suggest you not confuse Ubuntu/Linux with Windows. Ubuntu is not a Windows clone and the procedures may be different. If you need help configuring select "system/help and support".

Hope this helps.

---

### Post by Philip Gray on 2011-06-13
Hi Tamlynmac

Tks for yr help. I do know that Linux is not a Windows clone and that the procedures are different. Finding things in Linux can be problematic. I lot of the times this is due to a lack of knowledge on its' file structure which has taken me awhile to get used to again. A number of years ago I had to do some work in Unix to get stats from my company's IVR. It was a huge learning curve. This did help me to a certain extent in Linux. 

Finding where Linux stores all of its' icons took me quite awhile. In Windows there are a few things that are a lot easier and simpler, changing and finding icons is one of them. The other one is seeing at a glance which are yr executable files (bat, com, exe), which I have found in Linux to be a bit problematic.

Regards
Philip

---

### Post by Tamlynmac on 2011-06-13
In Nautilus don't forget to turn on show hidden files (View menu).

Most of the executables are located here:
"nautilus/file system/usr/bin" or "nautilus/file system/usr/sbin"

Icons are a little tougher, depending on which icon theme you may be using. Many of which may be located here:
"nautilus/file system/share/icons

I suggest you get used to the Nautilus file browser. The file system is the directory you should not be able to write to or change any files without using sudo in the terminal, logging in as root user (which is not a good idea) or during an app install. You directory is primarily for your use, but also has some folders for operational apps. Some apps load directly into your directory and the executable is generally located in a bin folder located within the app folder. By turning on the show hidden files you should be able to view all the folders & files in your directory.

You could download this free pocket [guide]("http://www.ubuntupocketguide.com/download_main.html"). It does help with both setup & how to deal with files.

Good Luck

* If you don't require any more assistance, please mark this thread as solved.

---

### Post by Philip Gray on 2011-06-20
Hi Tamlynmac

How do I mark this thread as solved?

Regards
Philip

---

### Post by wildmanne39 on 2011-06-20
> **Philip Gray said:**
> Hi Tamlynmac

How do I mark this thread as solved?

Regards
PhilipHi, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

