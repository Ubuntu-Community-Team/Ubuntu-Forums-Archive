---
title: "How To: Custom Start Button in GNOME Desktop - Cool!"
date: 2009-10-06
forum: Desktop Environments
---

### Post by shaunsmith_99 on 2009-10-06
I couldn't find these directions on the forums here, so I'll go ahead and post something cool from the Internet. To give proper credit, these instructions were created by Nate Welce, [http://www.natewelch.com/index.php?name=News&file=article&sid=41](http://www.natewelch.com/index.php?name=News&file=article&sid=41) and modified by me to. Basically it's a really neat way to customize your desktop environment by putting in custom Start buttons in the Gnome environment. 
   
--------------------------------

[LIST=1]
[*]Make an image that you want to use as a start menu (download mine at the bottom of this article). It can be anything you want but should be somewhat horizontally or vertically oriented depending on the type of panel you'll be placing it on. Don't worry about the original's size as it will scale down nicely (mine's 350 pixels, 17KB). Lastly, make the background transparent to allow the underlying panel color/background to show through.
[*]Save the image as a transparent PNG file somewhere in your home directory. I personally have a Pictures/GUI subdirectory just in case I ever reinstall my Linux, I have all my GUI tweaks, wallpapers, etc... right there.
[*]If you haven't done so already, add a "Main Menu" to your panel by right-clicking on an empty area on the panel and selecting "Add to Panel". There are two types of menus there - you want to pick the one represented by a single icon of the Ubuntu logo (or whatever your Linux distro uses as a default image). Also remove the Applications/Places/System menu from your panel if you have one of those set.
[*]To set the custom menu graphic, you need to open the Configuration Editor under the "System Tools" menu - or for you hardcore types, "gconf-editor" at the command line. Go to **apps->panel->objects** and you'll see a series of object_x subitems. Click through them until you find the one where the value for "object_type" is "menu-object". Check the "use_custom_icon" option and then set the "custom_icon" value to the path to your custom button graphic, i.e. "/home/username/Pictures/ubuntumenu.png". The graphic should update immediately.
[*]For an added touch, add a "Separator" to your GNOME panel to partition it off from the rest of the panel, as seen in the screenshot above
[/LIST]
-------------------------------------------------------------------------------------------

 Worked like a charm. I found the Penguin online, loaded it into Gimp and with the wand tool, removed all the white background while looking at it from a trasnparant second layer. I saved it as a .png, followed these directions, and now I have a cool Start button. 
 Anybody else use this (or a similar) method and have good results?

 Thanks Nate Welch!

---

### Post by wah fun on 2011-01-21
Thanks for the info. And I really like the dock appearance. Can you tell me what you are using and how to achieve your effect?

thx

---

