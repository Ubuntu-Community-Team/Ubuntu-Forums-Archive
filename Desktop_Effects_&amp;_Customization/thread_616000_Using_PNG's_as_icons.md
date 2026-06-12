---
title: "Using PNG's as icons"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by Joshgray on 2007-11-17
I've just started in the linux world with a fresh install of gutsy. I am smitten, but I have a small problem: I created a launcher on my menu (which works fine) and I would like to change the icon from the default to a PNG that I have. Unfortunately, the icon browser will not show PNG's, only the SVG's. Any ideas?

I have found that not even SVG's will show up in the browser. The only ones that do show up are the ones in  /usr/share/icons/hicolor/scalable/apps/gnome-panel-launcher.svg 

Thanks

UPDATED: wow, I am *that* new. I figured it out, but it doesn't seem very intuitive to select a folder in which to browse icons, but not be able to see the contents.

---

### Post by siouzi on 2007-11-30
Wow I had the same problem! The answer why you can't see any icons using the browser is : **BUG**!

So just **type the path to the icons folder** in the box that has the default */usr/share/icons/hicolor/scalable/apps/gnome-panel-launcher.svg*. The displayed icons update dynamically as you type! :popcorn:

---

### Post by aetani on 2007-11-30
Hi everybody
I am new Ubuntu userand I have the same problem.
what should I do.
Regards

---

### Post by MoToR on 2007-12-14
I'm new to ubuntu as well. I started with v7.10 and have no idea how other ubuntu versions look like, so I'll be 7.10 specific.

Open the **File Browser**, click **File System** from **Places** sub-window on the left and go to ***/usr/share/icons/*** (or just go open ***/usr/share/icons/*** any way you like).

What you'll see is a variety of directories, each with subdirectories, from which personally I usually choose ***/gnome/scalable*** and then there's again a variety of subdirs which contain mostly ***.svg*** files.
If you choose fixed size subdir like ***8x8*** or ***32x32*** instead of ***scalable*** you'll see mostly ***.png*** files.

As far as I can see, each ***.svg*** file contains a set of different sizes of the same one icon and not a whole icon library, like ***shell32.dll*** or ***imageres.dll*** in ***System32*** folder of MS Windows. On the other hand each ***.png*** file seems to be a single icon of specific size. It's logical (but I dunno if it's correct) that an ***.svg*** file is a compilation of corresponding ***.png*** files of an icon.

Thus, as far as I can see, both ***.svg*** and ***.png*** can be used as icons to customize whatever you customize.

For example ***/usr/share/icons/gnome/scalable/places*** path leads to 53 (on my computer) ***.svg*** and ***.icon*** files (.icon files seem like service text files, which there's no need to touch).

So browse those folders, find icons you like; at the same time open the **Properties** of the launcher button which icon you'd like to change, click the default icon in the left upper corner of the **Properties** window, click **Browse** and find the subdirectory that contains the icon you chose using the **File Browser**. Enter the subdirectory and although you see it empty, click **Open** (lower right corner of the **Browse** window). Give it time to load and you'll see all the icons contained in the subdirectory you chose to open. Now just pick the one you liked and click **OK**.

Example: I created few shortcuts on the upper panel of the ubuntu desktop (where **Applications**, **Places**, **System** menus are, as well as FireFox, Mail and Help icons by default). One of the shurtcuts was Home Directory. To create it I clicked the upper panel with the Right mouse button, chose **Add To Panel**, then clicked **Custom Application Launcher**, typed "Home" in the **Name** field, "nautilus /home/motor" in the **Command** field ("motor" is my username of course, type yours instead), then I clicked the default icon in the upper left corner of the **Properties** window, clicked **Browse**, changed the path to ***/usr/share/icons/gnome/scalable/places*** using GUI (you can just type it in instead of clicking Browse), clicked **Open**, and finally chose ***folder_home.svg*** icon for the shortcut I created (my preference, choose whatever you like).

Hope this helps. Good luck!

---

